---
title: Tratando a reentrada em aplicativos assíncronos (C#)
description: Saiba como lidar com a reentrância em aplicativos assíncronos em C#, que se refere à reinserção de uma operação assíncrona antes que ela seja concluída com possíveis resultados inesperados.
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: fdd440d167b95268a5ae6de0e57a32f0fad66b7c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925235"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="bb2bc-103">Tratando a reentrada em aplicativos assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="bb2bc-103">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="bb2bc-104">Ao incluir código assíncrono em seu aplicativo, você deve considerar e, possivelmente, evitar a reentrância, que se refere à reinserção de uma operação assíncrona antes de ela ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-104">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="bb2bc-105">Se você não identificar e tratar as possibilidades de reentrância, isso poderá causar resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-105">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="bb2bc-106">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="bb2bc-106">**In this topic**</span></span>

- [<span data-ttu-id="bb2bc-107">Reconhecendo a reentrância</span><span class="sxs-lookup"><span data-stu-id="bb2bc-107">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="bb2bc-108">Manipulando a reentrância</span><span class="sxs-lookup"><span data-stu-id="bb2bc-108">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="bb2bc-109">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="bb2bc-109">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="bb2bc-110">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bb2bc-110">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="bb2bc-111">Executar várias operações e colocar a saída na fila</span><span class="sxs-lookup"><span data-stu-id="bb2bc-111">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="bb2bc-112">Examinar e executar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="bb2bc-112">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="bb2bc-113">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e .NET Framework 4,5 ou mais recente instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-113">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="bb2bc-114">O protocolo TLS versão 1,2 agora é a versão mínima a ser usada no desenvolvimento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-114">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="bb2bc-115">Se seu aplicativo for destinado a uma versão de .NET Framework anterior a 4,7, consulte o artigo a seguir para [práticas recomendadas de TLS (Transport Layer Security) com .NET Framework](../../../../framework/network-programming/tls.md).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-115">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="bb2bc-116">Reconhecendo a reentrância</span><span class="sxs-lookup"><span data-stu-id="bb2bc-116">Recognizing Reentrancy</span></span>

<span data-ttu-id="bb2bc-117">No exemplo deste tópico, os usuários escolhem um botão **Iniciar** para iniciar um aplicativo assíncrono que baixa uma série de sites e calcula o número total de bytes baixados.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-117">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="bb2bc-118">Uma versão síncrona do exemplo responderia da mesma forma, independentemente de quantas vezes um usuário escolhesse o botão porque, após a primeira vez, o thread da interface do usuário ignora esses eventos até que o aplicativo conclua a execução.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-118">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="bb2bc-119">Em um aplicativo assíncrono, no entanto, o thread da interface do usuário continua a responder e você pode reinserir a operação assíncrona antes que ele seja concluído.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-119">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="bb2bc-120">O exemplo a seguir mostra a saída esperada, caso o usuário escolha o botão **Iniciar** apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-120">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="bb2bc-121">É exibida uma lista dos sites baixados com o tamanho, em bytes, de cada site.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-121">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="bb2bc-122">O número total de bytes é exibido no final.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-122">The total number of bytes appears at the end.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="bb2bc-123">No entanto, se o usuário escolhe o botão mais de uma vez, o manipulador de eventos é invocado repetidamente e o processo de download é reinserido a cada vez.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-123">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="bb2bc-124">Como resultado, várias operações assíncronas estarão em execução ao mesmo tempo, a saída intercalará os resultados e o número total de bytes será confuso.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-124">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="bb2bc-125">Você pode examinar o código que produz esta saída fazendo a rolagem até o final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-125">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="bb2bc-126">Você pode fazer experimentos com o código baixando a solução em seu computador local e, em seguida, executar o projeto WebsiteDownload ou usar o código no final deste tópico para criar seu próprio projeto.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-126">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="bb2bc-127">Para obter mais informações e instruções, consulte [Examinar e executar o aplicativo de exemplo](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-127">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="bb2bc-128">Tratando a reentrância</span><span class="sxs-lookup"><span data-stu-id="bb2bc-128">Handling Reentrancy</span></span>

<span data-ttu-id="bb2bc-129">É possível tratar a reentrância de várias maneiras, dependendo do que você deseja que seu aplicativo faça.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-129">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="bb2bc-130">Este tópico apresenta os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb2bc-130">This topic presents the following examples:</span></span>

- [<span data-ttu-id="bb2bc-131">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="bb2bc-131">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="bb2bc-132">Desabilitar o botão **Iniciar** enquanto a operação estiver em execução para que o usuário não possa interrompê-la.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-132">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="bb2bc-133">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bb2bc-133">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="bb2bc-134">Cancelar qualquer operação que ainda estiver em execução quando o usuário escolher o botão **Iniciar** novamente e, em seguida, permitir que a operação solicitada mais recentemente continue.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-134">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="bb2bc-135">Executar várias operações e colocar a saída na fila</span><span class="sxs-lookup"><span data-stu-id="bb2bc-135">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="bb2bc-136">Permitir que todas as operações solicitadas sejam executadas de forma assíncrona, mas coordenar a exibição da saída, de forma que os resultados de cada operação apareçam juntos e em ordem.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-136">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="bb2bc-137">Desabilitar o botão iniciar</span><span class="sxs-lookup"><span data-stu-id="bb2bc-137">Disable the Start Button</span></span>

<span data-ttu-id="bb2bc-138">Você pode bloquear o botão **Iniciar** enquanto uma operação estiver em execução, desabilitando o botão na parte superior do manipulador de eventos `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-138">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="bb2bc-139">Você pode reativar o botão de dentro um bloco `finally` quando a operação for concluída para que os usuários possam executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-139">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="bb2bc-140">Para configurar esse cenário, faça as seguintes alterações no código básico que é fornecido em [Examinar e executar o aplicativo de exemplo](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-140">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="bb2bc-141">Você também pode baixar o aplicativo concluído de [exemplos assíncronos: reentrância em aplicativos da área de trabalho .net](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-141">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="bb2bc-142">O nome do projeto é DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-142">The name of the project is DisableStartButton.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

<span data-ttu-id="bb2bc-143">Como resultado das alterações, o botão não responde enquanto `AccessTheWebAsync` está baixando os sites, portanto, o processo não pode ser reinserido.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-143">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can't be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="bb2bc-144">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bb2bc-144">Cancel and Restart the Operation</span></span>

<span data-ttu-id="bb2bc-145">Em vez de desabilitar o botão **Iniciar**, você pode manter o botão ativo, mas, se o usuário escolher esse botão novamente, cancele a operação que já está em execução e permita que a operação iniciada mais recentemente continue.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-145">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="bb2bc-146">Para obter mais informações sobre o cancelamento, consulte [Ajuste fino de seu aplicativo assíncrono (C#)](./fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-146">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="bb2bc-147">Para configurar esse cenário, faça as seguintes alterações no código básico que é fornecido em [Examinar e executar o aplicativo de exemplo](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-147">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="bb2bc-148">Você também pode baixar o aplicativo concluído de [exemplos assíncronos: reentrância em aplicativos da área de trabalho .net](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-148">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="bb2bc-149">O nome do projeto é CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-149">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="bb2bc-150">Declare uma <xref:System.Threading.CancellationTokenSource> variável, `cts` , que está no escopo de todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-150">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that's in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="bb2bc-151">Em `StartButton_Click`, determine se uma operação já está em andamento.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-151">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="bb2bc-152">Se o valor de `cts` for nulo, nenhuma operação estará ativa.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-152">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="bb2bc-153">Se o valor não for nulo, a operação que já está em execução será cancelada.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-153">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="bb2bc-154">Defina `cts` para um valor diferente que represente o processo atual.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-154">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="bb2bc-155">Ao final de `StartButton_Click`, o processo atual estará concluído, então, defina o valor de `cts` novamente como nulo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-155">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="bb2bc-156">O código a seguir mostra todas as alterações em `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-156">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="bb2bc-157">As adições estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-157">The additions are marked with asterisks.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

<span data-ttu-id="bb2bc-158">Em `AccessTheWebAsync`, faça as seguintes alterações.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-158">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="bb2bc-159">Adicione um parâmetro para aceitar o token de cancelamento de `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-159">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="bb2bc-160">Use o método <xref:System.Net.Http.HttpClient.GetAsync%2A> para baixar os sites porque `GetAsync` aceita um argumento <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-160">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="bb2bc-161">Antes `DisplayResults` de chamar para exibir os resultados de cada site baixado, verifique se `ct` a operação atual não foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-161">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn't been canceled.</span></span>

<span data-ttu-id="bb2bc-162">O código a seguir mostra essas alterações, que estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-162">The following code shows these changes, which are marked with asterisks.</span></span>

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

<span data-ttu-id="bb2bc-163">Se você escolher o botão **Iniciar** várias vezes enquanto este aplicativo estiver em execução, ele deverá produzir resultados semelhantes à saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-163">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="bb2bc-164">Para eliminar as listas parciais, remova a marca de comentário da primeira linha de código em `StartButton_Click`, para limpar a caixa de texto sempre que o usuário reiniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-164">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="bb2bc-165">Executar várias operações e enfileirar a saída</span><span class="sxs-lookup"><span data-stu-id="bb2bc-165">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="bb2bc-166">Este terceiro exemplo é mais complicado pois o aplicativo iniciará outra operação assíncrona a cada vez que o usuário escolher o botão **Iniciar** e todas as operações serão executadas até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-166">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="bb2bc-167">Todas as operações solicitadas baixam sites da lista de maneira assíncrona, mas a saída das operações será apresentada sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-167">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="bb2bc-168">Ou seja, a atividade de download real é intercalada, conforme mostrado na saída em [Reconhecendo a reentrância](#BKMK_RecognizingReentrancy), mas a lista de resultados para cada grupo é apresentada separadamente.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-168">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="bb2bc-169">As operações compartilham uma <xref:System.Threading.Tasks.Task> global, `pendingWork`, que serve como um gatekeeper para o processo de exibição.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-169">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="bb2bc-170">Para configurar esse cenário, faça as seguintes alterações no código básico que é fornecido em [Examinar e executar o aplicativo de exemplo](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-170">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="bb2bc-171">Você também pode baixar o aplicativo concluído de [exemplos assíncronos: reentrância em aplicativos da área de trabalho .net](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-171">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="bb2bc-172">O nome do projeto é QueueResults.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-172">The name of the project is QueueResults.</span></span>

<span data-ttu-id="bb2bc-173">A saída a seguir mostra o resultado, caso o usuário escolha o botão **Iniciar** apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-173">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="bb2bc-174">O rótulo de letra A indica que o resultado é da primeira vez que o botão **Iniciar** foi escolhido.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-174">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="bb2bc-175">Os números mostram a ordem das URLs na lista de destinos de download.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-175">The numbers show the order of the URLs in the list of download targets.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

<span data-ttu-id="bb2bc-176">Se o usuário escolher o botão **Iniciar** três vezes, o aplicativo produzirá uma saída semelhante à das linhas a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-176">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="bb2bc-177">As linhas de informações que começam com um sinal de jogo da velha (#) rastreiam o progresso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-177">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

<span data-ttu-id="bb2bc-178">Os grupos B e C iniciam antes da conclusão do grupo A, mas a saída para cada grupo é exibida separadamente.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-178">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="bb2bc-179">Toda a saída para o grupo A aparece em primeiro, seguida por toda a saída para o grupo B e, em seguida, toda a saída para o grupo C. O aplicativo sempre exibe os grupos em ordem e, para cada grupo, sempre exibe as informações sobre os sites individuais na ordem em que as URLs aparecem na lista de URLs.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-179">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="bb2bc-180">No entanto, não é possível prever a ordem na qual os downloads realmente acontecem.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-180">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="bb2bc-181">Depois que vários grupos tiverem sido iniciados, as tarefas de download que eles geram estarão todos ativas.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-181">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="bb2bc-182">Você não pode presumir que A-1 será baixado antes de B-1 e não pode presumir que A-1 será baixado antes de A-2.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-182">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="bb2bc-183">Definições Globais</span><span class="sxs-lookup"><span data-stu-id="bb2bc-183">Global Definitions</span></span>

<span data-ttu-id="bb2bc-184">O código de exemplo contém as duas declarações globais a seguir, que estão visíveis em todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-184">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="bb2bc-185">A variável `Task`, `pendingWork`, supervisiona o processo de exibição e impede que qualquer grupo interrompa a operação de exibição do outro grupo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-185">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="bb2bc-186">A variável de caractere, `group`, rotula a saída de grupos diferentes para verificar se os resultados aparecem na ordem esperada.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-186">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="bb2bc-187">O manipulador de eventos Click</span><span class="sxs-lookup"><span data-stu-id="bb2bc-187">The Click Event Handler</span></span>

<span data-ttu-id="bb2bc-188">O manipulador de eventos `StartButton_Click`, incrementa a letra de grupo sempre que o usuário escolhe o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-188">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="bb2bc-189">Em seguida, o manipulador chama `AccessTheWebAsync` para executar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-189">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="bb2bc-190">O método AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="bb2bc-190">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="bb2bc-191">Este exemplo divide o `AccessTheWebAsync` em dois métodos.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-191">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="bb2bc-192">O primeiro método, `AccessTheWebAsync`, inicia todas as tarefas de download de um grupo e configura `pendingWork` para controlar o processo de exibição.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-192">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="bb2bc-193">O método usa uma LINQ (consulta integrada à linguagem) e um <xref:System.Linq.Enumerable.ToArray%2A> para iniciar todas as tarefas de download ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-193">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="bb2bc-194">Em seguida, o `AccessTheWebAsync` chama `FinishOneGroupAsync` para aguardar a conclusão de cada download e exibir seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-194">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="bb2bc-195">O `FinishOneGroupAsync` retorna uma tarefa que é atribuída a `pendingWork` em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-195">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="bb2bc-196">Esse valor impede a interrupção por outra operação antes que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-196">That value prevents interruption by another operation before the task is complete.</span></span>

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="bb2bc-197">O método FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="bb2bc-197">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="bb2bc-198">Esse método percorre as tarefas de download em um grupo, aguardando cada uma delas, exibindo o comprimento do site baixado e adicionando o comprimento ao total.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-198">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="bb2bc-199">A primeira instrução em `FinishOneGroupAsync` usa `pendingWork` para verificar se o método de inserção não interfere com uma operação que já está no processo de exibição ou que já está aguardando.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-199">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="bb2bc-200">Se houver uma operação dessas em andamento, a operação de inserção deverá esperar por sua vez.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-200">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a><span data-ttu-id="bb2bc-201">Pontos de Interesse</span><span class="sxs-lookup"><span data-stu-id="bb2bc-201">Points of Interest</span></span>

<span data-ttu-id="bb2bc-202">As linhas de informações que começam com um sinal de jogo da velha (#) na saída esclarecem o funcionamento deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-202">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="bb2bc-203">A saída mostra os padrões a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-203">The output shows the following patterns.</span></span>

- <span data-ttu-id="bb2bc-204">Um grupo pode ser iniciado enquanto um grupo anterior estiver exibindo a saída, mas a exibição da saída do grupo anterior não será interrompida.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-204">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- <span data-ttu-id="bb2bc-205">O tarefa `pendingWork` é nula no início de `FinishOneGroupAsync` somente para o grupo A, que foi iniciado primeiro.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-205">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="bb2bc-206">O grupo A ainda não concluiu uma expressão Await quando ela chega `FinishOneGroupAsync` .</span><span class="sxs-lookup"><span data-stu-id="bb2bc-206">Group A hasn't yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="bb2bc-207">Portanto, o controle não foi retornado ao `AccessTheWebAsync` e a primeira atribuição para `pendingWork` não ocorreu.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-207">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="bb2bc-208">As duas linhas a seguir sempre aparecem juntas na saída.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-208">The following two lines always appear together in the output.</span></span> <span data-ttu-id="bb2bc-209">O código nunca é interrompido entre o início de uma operação de um grupo em `StartButton_Click` e a atribuição de uma tarefa para o grupo para `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-209">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="bb2bc-210">Depois que um grupo insere o `StartButton_Click`, a operação não conclui uma expressão await até que a operação insira `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-210">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="bb2bc-211">Portanto, nenhuma outra operação pode obter controle durante esse segmento de código.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-211">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="bb2bc-212">Revisando e executando o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="bb2bc-212">Reviewing and Running the Example App</span></span>

<span data-ttu-id="bb2bc-213">Para entender melhor o aplicativo de exemplo, você pode baixá-lo, compilá-lo ou examinar o código ao final deste tópico sem implementar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-213">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="bb2bc-214">Para executar o exemplo como um aplicativo da área de trabalho do WPF (Windows Presentation Foundation), você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-214">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="bb2bc-215">Baixar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb2bc-215">Downloading the App</span></span>

1. <span data-ttu-id="bb2bc-216">Baixe o aplicativo compactado em [Exemplos assíncronos: reentrância em aplicativos de área de trabalho do .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-216">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="bb2bc-217">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-217">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="bb2bc-218">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-218">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="bb2bc-219">Navegue até a pasta que contém o código de exemplo descompactado e, em seguida, abra o arquivo de solução (.sln).</span><span class="sxs-lookup"><span data-stu-id="bb2bc-219">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="bb2bc-220">No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja executar e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-220">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="bb2bc-221">Escolha as teclas CTRL+F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-221">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="bb2bc-222">Compilando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb2bc-222">Building the App</span></span>

<span data-ttu-id="bb2bc-223">A seção a seguir fornece o código para compilar o exemplo como um aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-223">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="bb2bc-224">Para compilar um aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="bb2bc-224">To build a WPF app</span></span>

1. <span data-ttu-id="bb2bc-225">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-225">Start Visual Studio.</span></span>

2. <span data-ttu-id="bb2bc-226">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-226">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="bb2bc-227">A caixa de diálogo **Novo Projeto** será aberta.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-227">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="bb2bc-228">No painel **Modelos Instalados**, expanda **Visual C#** e, em seguida, expanda **Windows**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-228">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="bb2bc-229">Na lista de tipos de projeto, escolha **Aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-229">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="bb2bc-230">Nomeie o projeto `WebsiteDownloadWPF` , escolha .NET Framework versão 4,6 ou superior e, em seguida, clique no botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="bb2bc-230">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher, and then click the **OK** button.</span></span>

     <span data-ttu-id="bb2bc-231">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-231">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="bb2bc-232">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-232">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="bb2bc-233">Se a guia não estiver visível, abra o menu de atalho para MainWindow. XAML em **Gerenciador de soluções**e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-233">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="bb2bc-234">Na exibição **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-234">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     <span data-ttu-id="bb2bc-235">Uma janela simples, contendo uma caixa de texto e um botão, aparecerá no modo de exibição de **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-235">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="bb2bc-236">Em **Gerenciador de soluções**, clique com o botão direito do mouse em **referências** e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-236">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="bb2bc-237">Adicione uma referência para <xref:System.Net.Http> , se ela ainda não estiver selecionada.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-237">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="bb2bc-238">No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-238">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="bb2bc-239">Em MainWindow.xaml.cs, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-239">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Navigation;
    using System.Windows.Shapes;

    // Add the following using directives, and add a reference for System.Net.Http.
    using System.Net.Http;
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. <span data-ttu-id="bb2bc-240">Escolha a tecla CTRL+F5 para executar o programa e, em seguida, escolha o botão **Iniciar** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-240">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="bb2bc-241">Faça as alterações de [Desabilitar o botão Iniciar](#BKMK_DisableTheStartButton), [Cancelar e reiniciar a operação](#BKMK_CancelAndRestart) ou [Executar várias operações e colocar a saída em fila](#BKMK_RunMultipleOperations) para tratar a reentrância.</span><span class="sxs-lookup"><span data-stu-id="bb2bc-241">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb2bc-242">Veja também</span><span class="sxs-lookup"><span data-stu-id="bb2bc-242">See also</span></span>

- [<span data-ttu-id="bb2bc-243">Passo a passo: acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="bb2bc-243">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="bb2bc-244">Programação assíncrona com Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="bb2bc-244">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
