---
title: 'Passo a passo: acessando a Web usando async e await (C#)'
description: Este tutorial converte um aplicativo síncrono em uma solução assíncrona em C# que usa os recursos Async e Await.
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: d643793bfcdeaaeff56dd252c510d197a45442f9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925105"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="58af1-103">Passo a passo: acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="58af1-103">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="58af1-104">É possível escrever programas assíncronos de forma mais fácil e intuitiva usando funcionalidades async/await.</span><span class="sxs-lookup"><span data-stu-id="58af1-104">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="58af1-105">Você pode escrever código assíncrono que se parece com código síncrono e deixar que o compilador trate das complicadas continuações e funções de retorno de chamada que um código assíncrono normalmente envolve.</span><span class="sxs-lookup"><span data-stu-id="58af1-105">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="58af1-106">Para obter mais informações sobre o recurso Assíncrono, consulte [Programação assíncrona com async e await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-106">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="58af1-107">Este passo a passo começa com um aplicativo WPF (Windows Presentation Foundation) síncrono que soma o número de bytes em uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="58af1-107">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="58af1-108">Em seguida, converte o aplicativo em uma solução assíncrona usando os novos recursos.</span><span class="sxs-lookup"><span data-stu-id="58af1-108">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="58af1-109">Se não quiser compilar os aplicativos, você poderá baixar o [Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="58af1-109">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="58af1-110">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="58af1-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="58af1-111">Criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="58af1-111">Create a WPF application</span></span>

1. <span data-ttu-id="58af1-112">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58af1-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="58af1-113">Na barra de menus, escolha **arquivo**  >  **novo**  >  **projeto**.</span><span class="sxs-lookup"><span data-stu-id="58af1-113">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="58af1-114">A caixa de diálogo **Novo Projeto** será aberta.</span><span class="sxs-lookup"><span data-stu-id="58af1-114">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="58af1-115">No painel **Modelos Instalados**, escolha Visual C# e, em seguida, escolha **Aplicativo WPF** na lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="58af1-115">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="58af1-116">Na caixa de texto **Nome**, insira `AsyncExampleWPF` e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="58af1-116">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="58af1-117">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="58af1-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="58af1-118">Projetar um MainWindow WPF simples</span><span class="sxs-lookup"><span data-stu-id="58af1-118">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="58af1-119">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="58af1-119">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="58af1-120">Se a janela **caixa de ferramentas** não estiver visível, abra o menu **Exibir** e escolha caixa de **ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="58af1-120">If the **Toolbox** window isn't visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="58af1-121">Adicione um controle **Botão** e um controle **Caixa de Texto** à janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="58af1-121">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="58af1-122">Realce o controle **Caixa de Texto** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58af1-122">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="58af1-123">Defina a propriedade **Nome** como `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="58af1-123">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="58af1-124">Defina a propriedade **Altura** como 250.</span><span class="sxs-lookup"><span data-stu-id="58af1-124">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="58af1-125">Defina a propriedade **Largura** como 500.</span><span class="sxs-lookup"><span data-stu-id="58af1-125">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="58af1-126">Na guia **Texto**, especifique uma fonte com espaçamento uniforme, como Lucida Console ou Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="58af1-126">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="58af1-127">Realce o controle **Botão** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="58af1-127">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="58af1-128">Defina a propriedade **Nome** como `startButton`.</span><span class="sxs-lookup"><span data-stu-id="58af1-128">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="58af1-129">Altere o valor da propriedade **Conteúdo** de **Botão** para **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-129">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="58af1-130">Posicione a caixa de texto e o botão de modo que ambos sejam exibidos na janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="58af1-130">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="58af1-131">Para obter mais informações sobre o Designer XAML do WPF, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="58af1-131">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="58af1-132">Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="58af1-132">Add a reference</span></span>

1. <span data-ttu-id="58af1-133">No **Gerenciador de Soluções**, realce o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="58af1-133">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="58af1-134">Na barra de menus, escolha **projeto**  >  **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="58af1-134">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="58af1-135">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="58af1-135">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="58af1-136">Na parte superior da caixa de diálogo, verifique se seu projeto é voltado para o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="58af1-136">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="58af1-137">Na categoria **assemblies** , escolha **estrutura** se ela ainda não estiver escolhida.</span><span class="sxs-lookup"><span data-stu-id="58af1-137">In the **Assemblies** category, choose **Framework** if it isn't already chosen.</span></span>

5. <span data-ttu-id="58af1-138">Na lista de nomes, marque a caixa de seleção **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="58af1-138">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="58af1-139">Escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="58af1-139">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="58af1-140">Adicionar as diretivas using necessárias</span><span class="sxs-lookup"><span data-stu-id="58af1-140">Add necessary using directives</span></span>

1. <span data-ttu-id="58af1-141">No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="58af1-141">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="58af1-142">Adicione as seguintes `using` diretivas na parte superior do arquivo de código se elas ainda não estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="58af1-142">Add the following `using` directives at the top of the code file if they're not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="58af1-143">Criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="58af1-143">Create a synchronous app</span></span>

1. <span data-ttu-id="58af1-144">Na janela de design, MainWindow.xaml, clique duas vezes no botão **Iniciar** para criar o manipulador de eventos `startButton_Click` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="58af1-144">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="58af1-145">Em MainWindow.xaml.cs, copie o seguinte código para o corpo de `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="58af1-145">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="58af1-146">O código chama o método que aciona o aplicativo, `SumPageSizes` e exibe uma mensagem quando o controle retorna para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="58af1-146">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="58af1-147">O código para a solução síncrona contém os quatro métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="58af1-147">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="58af1-148">`SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e chama `GetURLContents` e `DisplayResults` para processar cada URL.</span><span class="sxs-lookup"><span data-stu-id="58af1-148">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="58af1-149">`SetUpURLList`, que cria e retorna uma lista de endereços web.</span><span class="sxs-lookup"><span data-stu-id="58af1-149">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="58af1-150">`GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="58af1-150">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="58af1-151">`DisplayResults`, que exibe o número de bytes na matriz de bytes de cada URL.</span><span class="sxs-lookup"><span data-stu-id="58af1-151">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="58af1-152">Copie os quatro métodos a seguir e cole-os no manipulador de eventos `startButton_Click` em MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="58af1-152">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290136.aspx",
            "https://msdn.microsoft.com/library/ee256749.aspx",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="58af1-153">Testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="58af1-153">Test the synchronous solution</span></span>

<span data-ttu-id="58af1-154">Escolha a tecla **F5** para executar o programa e, em seguida, o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-154">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="58af1-155">Uma saída semelhante à lista a seguir deve aparecer:</span><span class="sxs-lookup"><span data-stu-id="58af1-155">Output that resembles the following list should appear:</span></span>

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

<span data-ttu-id="58af1-156">Observe que são necessários alguns segundos para exibir as contagens.</span><span class="sxs-lookup"><span data-stu-id="58af1-156">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="58af1-157">Durante esse tempo, o thread da interface do usuário é bloqueado enquanto espera que os recursos solicitados sejam baixados.</span><span class="sxs-lookup"><span data-stu-id="58af1-157">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="58af1-158">Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição após escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-158">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="58af1-159">Esses esforços falham até que as contagens de bytes comecem a aparecer.</span><span class="sxs-lookup"><span data-stu-id="58af1-159">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="58af1-160">Se um site não estiver respondendo, você não terá nenhuma indicação de qual site falhou.</span><span class="sxs-lookup"><span data-stu-id="58af1-160">If a website isn't responding, you have no indication of which site failed.</span></span> <span data-ttu-id="58af1-161">É difícil até mesmo parar de esperar e fechar o programa.</span><span class="sxs-lookup"><span data-stu-id="58af1-161">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="58af1-162">Converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="58af1-162">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="58af1-163">Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents`, porque é pelas chamadas para o método <xref:System.Net.HttpWebRequest.GetResponse%2A> de <xref:System.Net.HttpWebRequest> e para o método <xref:System.IO.Stream.CopyTo%2A> de <xref:System.IO.Stream> que o aplicativo acessa a Web.</span><span class="sxs-lookup"><span data-stu-id="58af1-163">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="58af1-164">.NET Framework facilita a conversão fornecendo versões assíncronas de ambos os métodos.</span><span class="sxs-lookup"><span data-stu-id="58af1-164">.NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="58af1-165">Para obter mais informações sobre os métodos usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="58af1-165">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58af1-166">Conforme você seguir as etapas neste passo a passo, vários erros de compilador serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="58af1-166">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="58af1-167">Você pode ignorá-los e continuar com o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="58af1-167">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="58af1-168">Altere o método chamado na terceira linha de `GetURLContents` de `GetResponse` para o método <xref:System.Net.WebRequest.GetResponseAsync%2A> assíncrono, baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="58af1-168">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="58af1-169">`GetResponseAsync` retorna um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="58af1-169">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="58af1-170">Nesse caso, a *variável de retorno da tarefa*, `TResult` , tem o tipo <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="58af1-170">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="58af1-171">A tarefa é uma promessa de produzir um objeto `WebResponse` verdadeiro após os dados solicitados terem sido baixados e a tarefa ter sido executada até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="58af1-171">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="58af1-172">Para recuperar o valor `WebResponse` da tarefa, aplique um operador [await](../../../language-reference/operators/await.md) à chamada para `GetResponseAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-172">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="58af1-173">O operador `await` suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="58af1-173">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="58af1-174">Enquanto isso, o controle retorna para o chamador do método atual.</span><span class="sxs-lookup"><span data-stu-id="58af1-174">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="58af1-175">Neste exemplo, o método atual é `GetURLContents` e o chamador é `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="58af1-175">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="58af1-176">Quando a tarefa é concluída, o objeto `WebResponse` prometido é produzido como o valor da tarefa aguardada e é atribuído à variável `response`.</span><span class="sxs-lookup"><span data-stu-id="58af1-176">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="58af1-177">A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.</span><span class="sxs-lookup"><span data-stu-id="58af1-177">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="58af1-178">A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="58af1-178">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="58af1-179">Em seguida, um operador await é aplicado à tarefa para recuperar o valor `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="58af1-179">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="58af1-180">Se o método Async tiver trabalho para fazer isso não depende da conclusão da tarefa, o método poderá continuar com esse trabalho entre essas duas instruções, após a chamada para o método Async e antes da aplicação do `await` operador.</span><span class="sxs-lookup"><span data-stu-id="58af1-180">If your async method has work to do that doesn't depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="58af1-181">Para obter exemplos, consulte [como fazer várias solicitações da Web em paralelo usando Async e Await (c#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) e [como estender a explicação em modo assíncrono usando Task. WhenAll (c#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-181">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="58af1-182">Como você adicionou o operador `await` na etapa anterior, um erro do compilador ocorre.</span><span class="sxs-lookup"><span data-stu-id="58af1-182">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="58af1-183">O operador pode ser usado apenas em métodos que são marcados com o modificador [async](../../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-183">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="58af1-184">Ignore o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` por uma chamada para `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-184">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="58af1-185">Altere o nome do método chamado para <xref:System.IO.Stream.CopyToAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="58af1-185">Change the name of the method that's called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="58af1-186">O `CopyTo` `CopyToAsync` método ou copia bytes para seu argumento, `content` e não retorna um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="58af1-186">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn't return a meaningful value.</span></span> <span data-ttu-id="58af1-187">Na versão síncrona, a chamada para `CopyTo` é uma instrução simples que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="58af1-187">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="58af1-188">A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="58af1-188">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="58af1-189">A tarefa funciona como "Task(void)" e permite que o método seja aguardado.</span><span class="sxs-lookup"><span data-stu-id="58af1-189">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="58af1-190">Aplique `Await` ou `await` à chamada para `CopyToAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-190">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="58af1-191">A instrução anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-191">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="58af1-192">Tudo o que resta fazer em `GetURLContents` é ajustar a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="58af1-192">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="58af1-193">Você pode usar o operador `await` apenas em métodos que são marcados com o modificador [async](../../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-193">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="58af1-194">Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-194">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="58af1-195">O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `void` em C#.</span><span class="sxs-lookup"><span data-stu-id="58af1-195">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="58af1-196">Normalmente, um tipo de retorno de `void` é usado somente em um manipulador de eventos assíncrono, em que `void` é necessário.</span><span class="sxs-lookup"><span data-stu-id="58af1-196">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="58af1-197">Em outros casos, você usará `Task(T)` se o método Completed tiver uma instrução [Return](../../../language-reference/keywords/return.md) que retorna um valor do tipo T, e você usará `Task` se o método Completed não retornar um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="58af1-197">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn't return a meaningful value.</span></span> <span data-ttu-id="58af1-198">Você pode considerar que o tipo de retorno `Task` significa "Task(void)".</span><span class="sxs-lookup"><span data-stu-id="58af1-198">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="58af1-199">Para obter mais informações, consulte [Tipos de retorno assíncronos (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-199">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="58af1-200">O método `GetURLContents` tem uma instrução de retorno e a instrução retorna uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="58af1-200">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="58af1-201">Portanto, o tipo de retorno da versão assíncrona é Task(T), em que T é uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="58af1-201">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="58af1-202">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="58af1-202">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="58af1-203">Altere o tipo de retorno para `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="58af1-203">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="58af1-204">Por convenção, métodos assíncronos têm nomes que terminam em "Async", então renomeie o método `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-204">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="58af1-205">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="58af1-205">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="58af1-206">Com essas poucas alterações, a conversão de `GetURLContents` em um método assíncrono é concluída.</span><span class="sxs-lookup"><span data-stu-id="58af1-206">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="58af1-207">Converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="58af1-207">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="58af1-208">Repita as etapas do procedimento anterior para `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="58af1-208">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="58af1-209">Primeiro, altere a chamada para `GetURLContents` para uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58af1-209">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="58af1-210">Altere o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync` , se você ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="58af1-210">Change the name of the method that's called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="58af1-211">Aplique `await` à tarefa que `GetURLContentsAsync` retorna para obter o valor da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="58af1-211">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="58af1-212">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="58af1-212">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="58af1-213">A atribuição anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-213">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="58af1-214">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="58af1-214">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="58af1-215">Marque o método com o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="58af1-215">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="58af1-216">Acrescente "Async" ao nome do método.</span><span class="sxs-lookup"><span data-stu-id="58af1-216">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="58af1-217">Não há nenhuma variável de retorno de tarefa, T, desta vez porque `SumPageSizesAsync` o não retorna um valor para T. (o método não tem `return` instrução.) No entanto, o método deve retornar um `Task` para ser awaitable.</span><span class="sxs-lookup"><span data-stu-id="58af1-217">There is no task return variable, T, this time because `SumPageSizesAsync` doesn't return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="58af1-218">Portanto, altere o tipo de retorno do método de `void` para `Task`.</span><span class="sxs-lookup"><span data-stu-id="58af1-218">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="58af1-219">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="58af1-219">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="58af1-220">A conversão de `SumPageSizes` em `SumPageSizesAsync` está concluída.</span><span class="sxs-lookup"><span data-stu-id="58af1-220">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="58af1-221">Converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="58af1-221">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="58af1-222">No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync` , se você ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="58af1-222">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven't already done so.</span></span>

2. <span data-ttu-id="58af1-223">Como `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.</span><span class="sxs-lookup"><span data-stu-id="58af1-223">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="58af1-224">A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-224">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="58af1-225">A chamada retorna um `Task` e não um `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="58af1-225">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="58af1-226">Assim como nos procedimentos anteriores, você pode converter a chamada usando uma instrução ou duas instruções.</span><span class="sxs-lookup"><span data-stu-id="58af1-226">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="58af1-227">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="58af1-227">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="58af1-228">Para evitar inserir novamente a operação por acidente, adicione a seguinte instrução à parte superior de `startButton_Click` para desabilitar o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-228">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="58af1-229">É possível reabilitar o botão no final do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="58af1-229">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="58af1-230">Para obter mais informações sobre a reentrada, consulte [Tratando a reentrada em aplicativos assíncronos (C#)](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-230">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="58af1-231">Por fim, adicione o modificador `async` à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-231">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="58af1-232">Normalmente, os nomes dos manipuladores de eventos não são alterados.</span><span class="sxs-lookup"><span data-stu-id="58af1-232">Typically, the names of event handlers aren't changed.</span></span> <span data-ttu-id="58af1-233">O tipo de retorno não é alterado para `Task` porque os manipuladores de eventos devem retornar `void` .</span><span class="sxs-lookup"><span data-stu-id="58af1-233">The return type isn't changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="58af1-234">A conversão do projeto de um processamento síncrono em um assíncrono está concluída.</span><span class="sxs-lookup"><span data-stu-id="58af1-234">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="58af1-235">Testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="58af1-235">Test the asynchronous solution</span></span>

1. <span data-ttu-id="58af1-236">Escolha a tecla **F5** para executar o programa e, em seguida, o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-236">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="58af1-237">Uma saída semelhante à saída da solução síncrona deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="58af1-237">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="58af1-238">No entanto, observe as diferenças a seguir.</span><span class="sxs-lookup"><span data-stu-id="58af1-238">However, notice the following differences.</span></span>

    - <span data-ttu-id="58af1-239">Os resultados não ocorrem ao mesmo tempo, após a conclusão do processamento.</span><span class="sxs-lookup"><span data-stu-id="58af1-239">The results don't all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="58af1-240">Por exemplo, os dois programas contêm uma linha em `startButton_Click` que desmarca a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="58af1-240">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="58af1-241">A intenção é desmarcar a caixa de texto entre as execuções se você escolher o botão **Iniciar** pela segunda vez, após um conjunto de resultados ter aparecido.</span><span class="sxs-lookup"><span data-stu-id="58af1-241">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="58af1-242">Na versão síncrona, a caixa de texto é desmarcada logo antes das contagens aparecerem pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário fica livre para executar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="58af1-242">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="58af1-243">Na versão assíncrona, a caixa de texto é limpa imediatamente após você escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-243">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="58af1-244">O mais importante é que o thread da interface do usuário não é bloqueado durante os downloads.</span><span class="sxs-lookup"><span data-stu-id="58af1-244">Most importantly, the UI thread isn't blocked during the downloads.</span></span> <span data-ttu-id="58af1-245">Você pode mover ou redimensionar a janela enquanto os recursos da Web estão sendo baixados, contados e exibido.</span><span class="sxs-lookup"><span data-stu-id="58af1-245">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="58af1-246">Se um dos sites estiver lento ou não estiver respondendo, você poderá cancelar a operação escolhendo o botão **Fechar** (o x no campo vermelho no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="58af1-246">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-method"></a><span data-ttu-id="58af1-247">Substituir o método GetURLContentsAsync por um método .NET</span><span class="sxs-lookup"><span data-stu-id="58af1-247">Replace method GetURLContentsAsync with a .NET method</span></span>

1. <span data-ttu-id="58af1-248">.NET Framework 4,5 e versões posteriores fornecem muitos métodos assíncronos que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="58af1-248">.NET Framework 4.5 and later versions provide many async methods that you can use.</span></span> <span data-ttu-id="58af1-249">Um deles, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> de <xref:System.Net.Http.HttpClient>, faz exatamente o que é necessário para este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="58af1-249">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="58af1-250">Você pode usá-lo em vez do método `GetURLContentsAsync` que criou em um procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="58af1-250">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="58af1-251">A primeira etapa é criar um objeto `HttpClient` no método `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-251">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="58af1-252">Adicione a declaração a seguir ao início do método.</span><span class="sxs-lookup"><span data-stu-id="58af1-252">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="58af1-253">Em `SumPageSizesAsync,`, substitua a chamada para seu método `GetURLContentsAsync` por uma chamada para o método `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="58af1-253">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="58af1-254">Remova ou comente o método `GetURLContentsAsync` que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="58af1-254">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="58af1-255">Escolha a tecla **F5** para executar o programa e, em seguida, o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="58af1-255">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="58af1-256">O comportamento desta versão do projeto deve corresponder ao comportamento que o procedimento "Testar a solução assíncrona" descreve, mas com ainda menos esforço para você.</span><span class="sxs-lookup"><span data-stu-id="58af1-256">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="58af1-257">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="58af1-257">Example code</span></span>

<span data-ttu-id="58af1-258">O código a seguir contém o exemplo completo da conversão de uma solução síncrona em uma solução assíncrona usando o método `GetURLContentsAsync` assíncrono que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="58af1-258">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="58af1-259">Observe que ele se assemelha muito à solução síncrona original.</span><span class="sxs-lookup"><span data-stu-id="58af1-259">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

<span data-ttu-id="58af1-260">O código a seguir contém o exemplo completo da solução que usa o método `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="58af1-260">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="58af1-261">Veja também</span><span class="sxs-lookup"><span data-stu-id="58af1-261">See also</span></span>

- <span data-ttu-id="58af1-262">[Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="58af1-262">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="58af1-263">async</span><span class="sxs-lookup"><span data-stu-id="58af1-263">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="58af1-264">await</span><span class="sxs-lookup"><span data-stu-id="58af1-264">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="58af1-265">Programação assíncrona com Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="58af1-265">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="58af1-266">Tipos de retorno assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="58af1-266">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="58af1-267">TAP (programação assíncrona baseada em tarefas)</span><span class="sxs-lookup"><span data-stu-id="58af1-267">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="58af1-268">Como estender a instrução assíncrona usando Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="58af1-268">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="58af1-269">Como fazer várias solicitações da Web em paralelo usando Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="58af1-269">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
