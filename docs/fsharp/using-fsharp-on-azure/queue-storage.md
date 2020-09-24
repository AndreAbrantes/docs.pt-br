---
title: Introdução ao armazenamento de Filas do Azure usando F#
description: As filas do Azure fornecem uma mensagem assíncrona e confiável entre os componentes do aplicativo. A mensagem na nuvem permite que os componentes do aplicativo se dimensionem de modo independente.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 5d6074751f226f0587c4c73bfa9ff56d9aca2bc1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100081"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="e58dd-104">Introdução ao armazenamento de filas do Azure usando F\#</span><span class="sxs-lookup"><span data-stu-id="e58dd-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="e58dd-105">O armazenamento de filas do Azure fornece mensagens na nuvem entre os componentes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e58dd-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="e58dd-106">Na criação de aplicativos para escala, os componentes do aplicativo geralmente são desassociados, para que possam ser redimensionados independentemente.</span><span class="sxs-lookup"><span data-stu-id="e58dd-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="e58dd-107">O armazenamento de filas fornece mensagens assíncronas para a comunicação entre os componentes do aplicativo, estando eles em execução na nuvem, na área de trabalho, em um servidor local ou em um dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="e58dd-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="e58dd-108">O armazenamento de Fila também dá suporte ao gerenciamento de tarefas assíncronas e à criação de fluxos de trabalho do processo.</span><span class="sxs-lookup"><span data-stu-id="e58dd-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="e58dd-109">Sobre este tutorial</span><span class="sxs-lookup"><span data-stu-id="e58dd-109">About this tutorial</span></span>

<span data-ttu-id="e58dd-110">Este tutorial mostra como escrever código F # para algumas tarefas comuns usando o armazenamento de filas do Azure.</span><span class="sxs-lookup"><span data-stu-id="e58dd-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="e58dd-111">As tarefas cobertas incluem criar e excluir filas e adicionar, ler e excluir mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="e58dd-112">Para obter uma visão geral conceitual do armazenamento de filas, consulte [o guia .net para armazenamento de filas](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="e58dd-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e58dd-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e58dd-113">Prerequisites</span></span>

<span data-ttu-id="e58dd-114">Para usar este guia, você deve primeiro [criar uma conta de armazenamento do Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="e58dd-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="e58dd-115">Você também precisará da sua chave de acesso de armazenamento para essa conta.</span><span class="sxs-lookup"><span data-stu-id="e58dd-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="e58dd-116">Criar um script F # e iniciar o F# Interativo</span><span class="sxs-lookup"><span data-stu-id="e58dd-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="e58dd-117">Os exemplos neste artigo podem ser usados em um aplicativo F # ou em um script F #.</span><span class="sxs-lookup"><span data-stu-id="e58dd-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="e58dd-118">Para criar um script F #, crie um arquivo com a `.fsx` extensão, por exemplo `queues.fsx` , em seu ambiente de desenvolvimento em F #.</span><span class="sxs-lookup"><span data-stu-id="e58dd-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="e58dd-119">Em seguida, use um [Gerenciador de pacotes](package-management.md) , como [paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) , para instalar o `WindowsAzure.Storage` pacote e a referência `WindowsAzure.Storage.dll` em seu script usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="e58dd-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="e58dd-120">Adicionar declarações do namespace</span><span class="sxs-lookup"><span data-stu-id="e58dd-120">Add namespace declarations</span></span>

<span data-ttu-id="e58dd-121">Adicione as seguintes instruções `open` à parte superior do arquivo `queues.fsx`:</span><span class="sxs-lookup"><span data-stu-id="e58dd-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="e58dd-122">Obter a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="e58dd-122">Get your connection string</span></span>

<span data-ttu-id="e58dd-123">Você precisará de uma cadeia de conexão de armazenamento do Azure para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="e58dd-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="e58dd-124">Para obter mais informações sobre cadeias de conexão, consulte [Configurar cadeias de conexão de armazenamento](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="e58dd-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="e58dd-125">Para o tutorial, você inserirá sua cadeia de conexão em seu script, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e58dd-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="e58dd-126">No entanto, isso **não é recomendado** para projetos reais.</span><span class="sxs-lookup"><span data-stu-id="e58dd-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="e58dd-127">Sua chave de conta de armazenamento é semelhante para a senha raiz da sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e58dd-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="e58dd-128">Sempre tenha cuidado para proteger a chave de sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e58dd-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="e58dd-129">Evite distribuí-la a outros usuários, embuti-la no código ou salvá-lo em um arquivo de texto sem formatação que esteja acessível a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="e58dd-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="e58dd-130">Você pode regenerar sua chave usando o portal do Azure se acreditar que ele pode ter sido comprometido.</span><span class="sxs-lookup"><span data-stu-id="e58dd-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="e58dd-131">Para aplicativos reais, a melhor maneira de manter a cadeia de conexão de armazenamento está em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e58dd-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="e58dd-132">Para buscar a cadeia de conexão de um arquivo de configuração, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="e58dd-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="e58dd-133">O uso do Gerenciador de Configurações do Azure é opcional.</span><span class="sxs-lookup"><span data-stu-id="e58dd-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="e58dd-134">Você também pode usar uma API como o tipo de .NET Framework `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="e58dd-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="e58dd-135">Analisar a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="e58dd-135">Parse the connection string</span></span>

<span data-ttu-id="e58dd-136">Para analisar a cadeia de conexão, use:</span><span class="sxs-lookup"><span data-stu-id="e58dd-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="e58dd-137">Isso retornará um `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="e58dd-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="e58dd-138">Criar o cliente do serviço Fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-138">Create the Queue service client</span></span>

<span data-ttu-id="e58dd-139">A `CloudQueueClient` classe permite que você recupere filas armazenadas no armazenamento de filas.</span><span class="sxs-lookup"><span data-stu-id="e58dd-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="e58dd-140">Veja uma maneira de criar o cliente de serviço:</span><span class="sxs-lookup"><span data-stu-id="e58dd-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="e58dd-141">Agora você está pronto para escrever um código que lê e grava dados no Armazenamento de Filas.</span><span class="sxs-lookup"><span data-stu-id="e58dd-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="e58dd-142">Criar uma fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-142">Create a queue</span></span>

<span data-ttu-id="e58dd-143">Este exemplo mostra como criar uma fila, caso ela ainda não exista:</span><span class="sxs-lookup"><span data-stu-id="e58dd-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="e58dd-144">Inserir uma mensagem em uma fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-144">Insert a message into a queue</span></span>

<span data-ttu-id="e58dd-145">Para inserir uma mensagem em uma fila existente, primeiro crie uma nova `CloudQueueMessage` .</span><span class="sxs-lookup"><span data-stu-id="e58dd-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="e58dd-146">Em seguida, chame o `AddMessage` método.</span><span class="sxs-lookup"><span data-stu-id="e58dd-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="e58dd-147">Um `CloudQueueMessage` pode ser criado por meio de uma cadeia de caracteres (em formato UTF-8) ou de uma `byte` matriz, como esta:</span><span class="sxs-lookup"><span data-stu-id="e58dd-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="e58dd-148">Espiar a próxima mensagem</span><span class="sxs-lookup"><span data-stu-id="e58dd-148">Peek at the next message</span></span>

<span data-ttu-id="e58dd-149">Você pode inspecionar a mensagem na frente de uma fila, sem removê-la da fila, chamando o `PeekMessage` método.</span><span class="sxs-lookup"><span data-stu-id="e58dd-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="e58dd-150">Obter a próxima mensagem para processamento</span><span class="sxs-lookup"><span data-stu-id="e58dd-150">Get the next message for processing</span></span>

<span data-ttu-id="e58dd-151">Você pode recuperar a mensagem na frente de uma fila para processamento chamando o `GetMessage` método.</span><span class="sxs-lookup"><span data-stu-id="e58dd-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="e58dd-152">Posteriormente, você indicará o processamento bem-sucedido da mensagem usando `DeleteMessage` .</span><span class="sxs-lookup"><span data-stu-id="e58dd-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="e58dd-153">Alterar o conteúdo de uma mensagem na fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-153">Change the contents of a queued message</span></span>

<span data-ttu-id="e58dd-154">Você pode alterar o conteúdo de uma mensagem recuperada in-loco na fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="e58dd-155">Se a mensagem representar uma tarefa de trabalho, você poderá usar esse recurso para atualizar o status da tarefa de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e58dd-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="e58dd-156">O código a seguir atualiza a mensagem da fila com novo conteúdo e define o tempo limite de visibilidade para estender mais 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="e58dd-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="e58dd-157">Isso salva o estado do trabalho associado à mensagem e dá ao cliente mais um minuto para continuar trabalhando na mensagem.</span><span class="sxs-lookup"><span data-stu-id="e58dd-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="e58dd-158">Você pode usar essa técnica para acompanhar fluxos de trabalho de várias etapas em mensagens em fila, sem a necessidade de começar desde o início, caso uma etapa de processamento falhar devido a uma falha de hardware ou de software.</span><span class="sxs-lookup"><span data-stu-id="e58dd-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="e58dd-159">Normalmente, você manteria uma contagem de repetições também e, se a mensagem for repetida mais do que um número de vezes, você a excluiria.</span><span class="sxs-lookup"><span data-stu-id="e58dd-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="e58dd-160">Isso protege contra uma mensagem que dispara um erro do aplicativo sempre que for processada.</span><span class="sxs-lookup"><span data-stu-id="e58dd-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="e58dd-161">Remover a próxima mensagem da fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-161">De-queue the next message</span></span>

<span data-ttu-id="e58dd-162">Seu código remove uma mensagem de um fila em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="e58dd-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="e58dd-163">Ao chamar `GetMessage` , você receberá a próxima mensagem em uma fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="e58dd-164">Uma mensagem retornada de `GetMessage` torna-se invisível para todas as outras mensagens de leitura de código da fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="e58dd-165">Por padrão, essa mensagem permanece invisível por 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="e58dd-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="e58dd-166">Para concluir a remoção da mensagem da fila, você também deve chamar `DeleteMessage` .</span><span class="sxs-lookup"><span data-stu-id="e58dd-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="e58dd-167">Este processo de duas etapas de remover uma mensagem garante que quando o código não processa uma mensagem devido à falhas de hardware ou de software, outra instância do seu código pode receber a mesma mensagem e tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="e58dd-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="e58dd-168">Seu código chama `DeleteMessage` logo após a mensagem ser processada.</span><span class="sxs-lookup"><span data-stu-id="e58dd-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="e58dd-169">Usar fluxos de trabalho assíncronos com APIs de armazenamento de fila comuns</span><span class="sxs-lookup"><span data-stu-id="e58dd-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="e58dd-170">Este exemplo mostra como usar um fluxo de trabalho assíncrono com APIs de armazenamento de fila comuns.</span><span class="sxs-lookup"><span data-stu-id="e58dd-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="e58dd-171">Opções adicionais para remover mensagens da fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="e58dd-172">Há duas maneiras de personalizar a recuperação da mensagem de uma fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="e58dd-173">Primeiro, você pode obter um lote de mensagens (até 32).</span><span class="sxs-lookup"><span data-stu-id="e58dd-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="e58dd-174">Segundo, você pode definir um tempo limite de invisibilidade mais longo ou mais curto, permitindo mais ou menos tempo para seu código processar totalmente cada mensagem.</span><span class="sxs-lookup"><span data-stu-id="e58dd-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="e58dd-175">O exemplo de código a seguir usa `GetMessages` para obter 20 mensagens em uma chamada e, em seguida, processa cada mensagem.</span><span class="sxs-lookup"><span data-stu-id="e58dd-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="e58dd-176">Ele também define o tempo limite de invisibilidade de cinco minutos para cada mensagem.</span><span class="sxs-lookup"><span data-stu-id="e58dd-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="e58dd-177">Observe que os 5 minutos começam para todas as mensagens ao mesmo tempo; portanto, após 5 minutos desde a chamada para `GetMessages` , todas as mensagens que não foram excluídas ficarão visíveis novamente.</span><span class="sxs-lookup"><span data-stu-id="e58dd-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="e58dd-178">Obter o tamanho da fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-178">Get the queue length</span></span>

<span data-ttu-id="e58dd-179">Você pode obter uma estimativa do número de mensagens em uma fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="e58dd-180">O `FetchAttributes` método solicita ao serviço fila recuperar os atributos da fila, incluindo a contagem de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e58dd-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="e58dd-181">A `ApproximateMessageCount` propriedade retorna o último valor recuperado pelo `FetchAttributes` método, sem chamar o serviço fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="e58dd-182">Excluir uma fila</span><span class="sxs-lookup"><span data-stu-id="e58dd-182">Delete a queue</span></span>

<span data-ttu-id="e58dd-183">Para excluir uma fila e todas as mensagens contidas nela, chame o `Delete` método no objeto de fila.</span><span class="sxs-lookup"><span data-stu-id="e58dd-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="e58dd-184">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e58dd-184">Next steps</span></span>

<span data-ttu-id="e58dd-185">Agora que você aprendeu os conceitos básicos do armazenamento de Fila, siga estes links para saber mais sobre tarefas de armazenamento mais complexas.</span><span class="sxs-lookup"><span data-stu-id="e58dd-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="e58dd-186">APIs do Armazenamento do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="e58dd-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="e58dd-187">Provedor de tipo de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="e58dd-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="e58dd-188">Blog da equipe de Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="e58dd-188">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="e58dd-189">Configurar cadeias de conexão do Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="e58dd-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="e58dd-190">Referência de API REST dos Serviços de Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="e58dd-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
