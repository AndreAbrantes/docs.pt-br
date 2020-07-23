---
title: Usando o Async para acessar arquivos (C#)
description: Saiba como usar o recurso assíncrono para acessar arquivos em C#. Você pode chamar métodos assíncronos sem usar retornos de chamada ou dividir seu código entre os métodos.
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: eb67bd408fe37b99e6c5ffdc2550e8f95110d7eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925118"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="9690e-104">Usando o Async para acessar arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="9690e-104">Using Async for File Access (C#)</span></span>
<span data-ttu-id="9690e-105">Você pode usar o recurso async para acessar arquivos.</span><span class="sxs-lookup"><span data-stu-id="9690e-105">You can use the async feature to access files.</span></span> <span data-ttu-id="9690e-106">Usando o recurso async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="9690e-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="9690e-107">Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicionar algumas palavras-chave ao código.</span><span class="sxs-lookup"><span data-stu-id="9690e-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="9690e-108">Você pode considerar seguintes motivos para adicionar a assincronia às chamadas de acesso ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="9690e-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="9690e-109">A assincronia torna os aplicativos de interface do usuário mais responsivos porque o thread de interface do usuário que inicia a operação pode executar outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="9690e-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="9690e-110">Se o thread de interface do usuário precisar executar o código que leva muito tempo (por exemplo, mais de 50 milissegundos), a interface do usuário poderá congelar até que a E/S seja concluída e o thread da interface do usuário possa processar entradas do mouse e do teclado e outros eventos.</span><span class="sxs-lookup"><span data-stu-id="9690e-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="9690e-111">A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor reduzindo a necessidade de threads.</span><span class="sxs-lookup"><span data-stu-id="9690e-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="9690e-112">Se o aplicativo usar um thread dedicado por resposta e mil solicitações forem tratadas simultaneamente, serão necessários mil threads.</span><span class="sxs-lookup"><span data-stu-id="9690e-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="9690e-113">As operações assíncronas normalmente não precisam usar um thread durante a espera.</span><span class="sxs-lookup"><span data-stu-id="9690e-113">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="9690e-114">Elas podem usar o thread de conclusão de E/S existente rapidamente no final.</span><span class="sxs-lookup"><span data-stu-id="9690e-114">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="9690e-115">A latência de uma operação de acesso de arquivo pode ser muito baixa nas condições atuais, mas a latência pode aumentar consideravelmente no futuro.</span><span class="sxs-lookup"><span data-stu-id="9690e-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="9690e-116">Por exemplo, um arquivo pode ser movido para um servidor que está do outro lado do mundo.</span><span class="sxs-lookup"><span data-stu-id="9690e-116">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="9690e-117">A sobrecarga adicional de usar o recurso async é pequena.</span><span class="sxs-lookup"><span data-stu-id="9690e-117">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="9690e-118">As tarefas assíncronas podem facilmente ser executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="9690e-118">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="9690e-119">Executando os exemplos</span><span class="sxs-lookup"><span data-stu-id="9690e-119">Running the Examples</span></span>  
 <span data-ttu-id="9690e-120">Para executar os exemplos neste tópico, você pode criar um **Aplicativo WPF** ou um **Aplicativo do Windows Forms** e, em seguida, adicionar um **Botão**.</span><span class="sxs-lookup"><span data-stu-id="9690e-120">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="9690e-121">No evento `Click` do botão, adicione uma chamada para o primeiro método em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="9690e-121">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="9690e-122">Nos exemplos a seguir, inclua as seguintes `using` diretivas.</span><span class="sxs-lookup"><span data-stu-id="9690e-122">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="9690e-123">Uso da classe FileStream</span><span class="sxs-lookup"><span data-stu-id="9690e-123">Use of the FileStream Class</span></span>  
 <span data-ttu-id="9690e-124">Os exemplos neste tópico usam a classe <xref:System.IO.FileStream>, que tem uma opção que faz com que a E/S assíncrona ocorra no nível do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9690e-124">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="9690e-125">Usando essa opção, você pode evitar o bloqueio de um thread de ThreadPool em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="9690e-125">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="9690e-126">Para habilitar essa opção, você deve especificar o argumento `useAsync=true` ou `options=FileOptions.Asynchronous` na chamada do construtor.</span><span class="sxs-lookup"><span data-stu-id="9690e-126">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="9690e-127">Você não pode usar essa opção com <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> se você os abrir diretamente especificando um caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="9690e-127">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="9690e-128">No entanto, você poderá usar essa opção se fornecer um <xref:System.IO.Stream> que a classe <xref:System.IO.FileStream> abriu.</span><span class="sxs-lookup"><span data-stu-id="9690e-128">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="9690e-129">Observe que as chamadas assíncronas serão mais rápidas em aplicativos de interface do usuário mesmo se um thread de ThreadPool estiver bloqueado, porque o thread de interface do usuário não é bloqueado durante a espera.</span><span class="sxs-lookup"><span data-stu-id="9690e-129">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="9690e-130">Gravando texto</span><span class="sxs-lookup"><span data-stu-id="9690e-130">Writing Text</span></span>  
 <span data-ttu-id="9690e-131">O exemplo a seguir grava um texto em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9690e-131">The following example writes text to a file.</span></span> <span data-ttu-id="9690e-132">A cada instrução await, o método sai imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9690e-132">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="9690e-133">Quando o arquivo de E/S for concluído, o método continuará na instrução após a instrução await.</span><span class="sxs-lookup"><span data-stu-id="9690e-133">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="9690e-134">Observe que o modificador async é a definição de métodos que usam a instrução await.</span><span class="sxs-lookup"><span data-stu-id="9690e-134">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="9690e-135">O exemplo original tem a instrução `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, que é uma contração das duas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="9690e-135">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="9690e-136">A primeira instrução retorna uma tarefa e faz com que o processamento do arquivo seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="9690e-136">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="9690e-137">A segunda instrução com o await faz com que o método saia imediatamente e retorne uma tarefa diferente.</span><span class="sxs-lookup"><span data-stu-id="9690e-137">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="9690e-138">Quando o processamento do arquivo é concluído posteriormente, a execução retorna para a instrução após a await.</span><span class="sxs-lookup"><span data-stu-id="9690e-138">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="9690e-139">Para obter mais informações, consulte [Fluxo de controle em programas assíncronos (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="9690e-139">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="9690e-140">Lendo texto</span><span class="sxs-lookup"><span data-stu-id="9690e-140">Reading Text</span></span>  
 <span data-ttu-id="9690e-141">O exemplo a seguir lê o texto de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9690e-141">The following example reads text from a file.</span></span> <span data-ttu-id="9690e-142">O texto é armazenado em buffer e, nesse caso, colocado em um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="9690e-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="9690e-143">Diferentemente do exemplo anterior, a avaliação de await produz um valor.</span><span class="sxs-lookup"><span data-stu-id="9690e-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="9690e-144">O método <xref:System.IO.Stream.ReadAsync%2A> retorna um <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, portanto, a avaliação do await produz um valor `Int32` (`numRead`) após a conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="9690e-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="9690e-145">Para obter mais informações, consulte [Tipos de retorno assíncronos (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="9690e-145">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="9690e-146">E/S assíncrona paralela</span><span class="sxs-lookup"><span data-stu-id="9690e-146">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="9690e-147">O exemplo a seguir demonstra o processamento paralelo escrevendo dez arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="9690e-147">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="9690e-148">Para cada arquivo, o método <xref:System.IO.Stream.WriteAsync%2A> retorna uma tarefa que é então adicionada a uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9690e-148">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="9690e-149">A instrução `await Task.WhenAll(tasks);` sai do método e retoma no método quando o processamento do arquivo é concluído para todas as tarefas.</span><span class="sxs-lookup"><span data-stu-id="9690e-149">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="9690e-150">O exemplo fecha todas as instâncias de <xref:System.IO.FileStream> em um bloco `finally` após as tarefas serem concluídas.</span><span class="sxs-lookup"><span data-stu-id="9690e-150">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="9690e-151">Se cada `FileStream` foi criado em uma instrução `using`, o `FileStream` pode ter sido descartado antes de a tarefa ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="9690e-151">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="9690e-152">Observe que qualquer aumento de desempenho é quase que totalmente do processamento paralelo e não o processamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="9690e-152">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="9690e-153">As vantagens da assincronia são que ela não bloqueia vários threads e que ela não bloqueia o thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9690e-153">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9690e-154">Ao usar os métodos <xref:System.IO.Stream.WriteAsync%2A> e <xref:System.IO.Stream.ReadAsync%2A>, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usado para cancelar o fluxo intermediário da operação.</span><span class="sxs-lookup"><span data-stu-id="9690e-154">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="9690e-155">Para obter mais informações, consulte [Ajuste fino de seu aplicativo assíncrono (C#)](./fine-tuning-your-async-application.md) e [Cancelamento em threads gerenciados](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="9690e-155">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9690e-156">Veja também</span><span class="sxs-lookup"><span data-stu-id="9690e-156">See also</span></span>

- [<span data-ttu-id="9690e-157">Programação assíncrona com Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="9690e-157">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="9690e-158">Tipos de retorno assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="9690e-158">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="9690e-159">Fluxo de controle em programas assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="9690e-159">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
