---
title: Cancelar tarefas assíncronas após um período (C#)
description: Use o método CancellationTokenSource. CancelAfter em C# para agendar o cancelamento de quaisquer tarefas associadas não concluídas dentro de um período neste exemplo.
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: f32af1d893c60ac17648f60fa3aa90adaa0383e8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925282"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="36eef-103">Cancelar tarefas assíncronas após um período (C#)</span><span class="sxs-lookup"><span data-stu-id="36eef-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="36eef-104">Você pode cancelar uma operação assíncrona após um período de tempo usando o método <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> se você não deseja aguardar a conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="36eef-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="36eef-105">Esse método agenda o cancelamento de quaisquer tarefas associadas que não são concluídas dentro do período designado pela expressão `CancelAfter`.</span><span class="sxs-lookup"><span data-stu-id="36eef-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="36eef-106">Este exemplo adiciona o código desenvolvido em [Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) para baixar uma lista de sites e para exibir o tamanho dos conteúdos de cada um.</span><span class="sxs-lookup"><span data-stu-id="36eef-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="36eef-107">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="36eef-107">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="36eef-108">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="36eef-108">Download the example</span></span>

<span data-ttu-id="36eef-109">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="36eef-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="36eef-110">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36eef-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="36eef-111">Na barra de menus, escolha **arquivo**  >  **abrir**  >  **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="36eef-111">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="36eef-112">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="36eef-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="36eef-113">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelAfterTime** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="36eef-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="36eef-114">Pressione a tecla **F5** para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="36eef-114">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="36eef-115">(Ou pressione **Ctrl** + **F5** para executar o projeto sem depurá-lo).</span><span class="sxs-lookup"><span data-stu-id="36eef-115">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="36eef-116">Execute o programa várias vezes para verificar que a saída pode mostrar a saída para todos os sites, nenhum site ou alguns sites.</span><span class="sxs-lookup"><span data-stu-id="36eef-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="36eef-117">Se você não quiser baixar o projeto, você poderá examinar o arquivo MainWindow.xaml.cs no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="36eef-117">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="36eef-118">Criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="36eef-118">Build the example</span></span>

<span data-ttu-id="36eef-119">O exemplo neste tópico adiciona ao projeto que é desenvolvido em [Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) para cancelar uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="36eef-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="36eef-120">O exemplo usa a mesma interface do usuário, embora o botão **Cancelar** não seja explicitamente usado.</span><span class="sxs-lookup"><span data-stu-id="36eef-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="36eef-121">Para compilar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelAListOfTasks** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="36eef-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="36eef-122">Adicione as alterações deste tópico ao projeto.</span><span class="sxs-lookup"><span data-stu-id="36eef-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="36eef-123">Para especificar um tempo máximo antes que as tarefas sejam marcadas como canceladas, adicione uma chamada para `CancelAfter` a `startButton_Click`, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="36eef-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="36eef-124">A adição é marcada com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="36eef-124">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
    }
    catch (OperationCanceledException)
    {
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }

    cts = null;
}
```

 <span data-ttu-id="36eef-125">Execute o programa várias vezes para verificar que a saída pode mostrar a saída para todos os sites, nenhum site ou alguns sites.</span><span class="sxs-lookup"><span data-stu-id="36eef-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="36eef-126">A saída a seguir é um exemplo.</span><span class="sxs-lookup"><span data-stu-id="36eef-126">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="36eef-127">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="36eef-127">Complete example</span></span>

<span data-ttu-id="36eef-128">O código a seguir é o texto completo do arquivo MainWindow.xaml.cs para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="36eef-128">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="36eef-129">Os asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="36eef-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="36eef-130">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="36eef-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="36eef-131">Você pode baixar o projeto de [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="36eef-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace CancelAfterTime
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="36eef-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="36eef-132">See also</span></span>

- [<span data-ttu-id="36eef-133">Programação assíncrona com Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="36eef-133">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="36eef-134">Passo a passo: acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="36eef-134">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="36eef-135">Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)</span><span class="sxs-lookup"><span data-stu-id="36eef-135">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="36eef-136">Ajuste fino de seu aplicativo assíncrono (C#)</span><span class="sxs-lookup"><span data-stu-id="36eef-136">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="36eef-137">Exemplo assíncrono: ajuste fino de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="36eef-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
