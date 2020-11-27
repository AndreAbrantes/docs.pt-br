---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 04bc5db4172d9052b45f63a2f7ed0fb997dc4c6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257191"
---
# <a name="stream"></a><span data-ttu-id="b1967-102">STREAM</span><span class="sxs-lookup"><span data-stu-id="b1967-102">Stream</span></span>

<span data-ttu-id="b1967-103">O exemplo de fluxo demonstra o uso da comunicação do modo de transferência de streaming.</span><span class="sxs-lookup"><span data-stu-id="b1967-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="b1967-104">O serviço expõe várias operações que enviam e recebem fluxos.</span><span class="sxs-lookup"><span data-stu-id="b1967-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="b1967-105">Este exemplo é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="b1967-105">This sample is self-hosted.</span></span> <span data-ttu-id="b1967-106">O cliente e o serviço são programas de console.</span><span class="sxs-lookup"><span data-stu-id="b1967-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1967-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b1967-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b1967-108">O Windows Communication Foundation (WCF) pode se comunicar em dois modos de transferência — em buffer ou streaming.</span><span class="sxs-lookup"><span data-stu-id="b1967-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="b1967-109">No modo de transferência em buffer padrão, uma mensagem deve ser totalmente entregue antes que um receptor possa lê-la.</span><span class="sxs-lookup"><span data-stu-id="b1967-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="b1967-110">No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de ser totalmente entregue.</span><span class="sxs-lookup"><span data-stu-id="b1967-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="b1967-111">O modo de streaming é útil quando as informações que são passadas são demoradas e podem ser processadas em série.</span><span class="sxs-lookup"><span data-stu-id="b1967-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="b1967-112">O modo de streaming também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.</span><span class="sxs-lookup"><span data-stu-id="b1967-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="b1967-113">Contratos de streaming e serviço</span><span class="sxs-lookup"><span data-stu-id="b1967-113">Streaming and Service Contracts</span></span>  

 <span data-ttu-id="b1967-114">O streaming é algo a ser considerado ao criar um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="b1967-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="b1967-115">Se uma operação receber ou retornar grandes quantidades de dados, considere transmitir esses dados para evitar uma alta utilização de memória devido ao buffer de mensagens de entrada ou saída.</span><span class="sxs-lookup"><span data-stu-id="b1967-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="b1967-116">Para transmitir dados, o parâmetro que mantém esses dados deve ser o único parâmetro na mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1967-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="b1967-117">Por exemplo, se a mensagem de entrada for aquela a ser transmitida, a operação deverá ter exatamente um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1967-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="b1967-118">Da mesma forma, se a mensagem de saída for para ser transmitida, a operação deverá ter exatamente um parâmetro de saída ou um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b1967-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="b1967-119">Em ambos os casos, o parâmetro ou o tipo de valor de retorno deve ser `Stream` , `Message` ou `IXmlSerializable` .</span><span class="sxs-lookup"><span data-stu-id="b1967-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="b1967-120">Este é o contrato de serviço usado neste exemplo de streaming.</span><span class="sxs-lookup"><span data-stu-id="b1967-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="b1967-121">A `GetStream` operação recebe alguns dados de entrada como uma cadeia de caracteres, que é armazenada em buffer e retorna um `Stream` , que é transmitido.</span><span class="sxs-lookup"><span data-stu-id="b1967-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="b1967-122">Por outro lado, `UploadStream` o leva em um `Stream` (transmitido) e retorna um `bool` (em buffer).</span><span class="sxs-lookup"><span data-stu-id="b1967-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="b1967-123">`EchoStream` Pega e retorna `Stream` e é um exemplo de uma operação cujas mensagens de entrada e saída são transmitidas.</span><span class="sxs-lookup"><span data-stu-id="b1967-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="b1967-124">Por fim, `GetReversedStream` o não usa entradas e retorna um `Stream` (transmitido).</span><span class="sxs-lookup"><span data-stu-id="b1967-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="b1967-125">Habilitando transferências em fluxo</span><span class="sxs-lookup"><span data-stu-id="b1967-125">Enabling Streamed Transfers</span></span>  

 <span data-ttu-id="b1967-126">Definir os contratos de operação conforme descrito anteriormente fornece streaming no nível de modelo de programação.</span><span class="sxs-lookup"><span data-stu-id="b1967-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="b1967-127">Se você parar lá, o transporte ainda armazenará em buffer todo o conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1967-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="b1967-128">Para habilitar o streaming de transporte, selecione um modo de transferência no elemento de associação do transporte.</span><span class="sxs-lookup"><span data-stu-id="b1967-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="b1967-129">O elemento Binding tem uma `TransferMode` propriedade que pode ser definida como `Buffered` , `Streamed` , `StreamedRequest` ou `StreamedResponse` .</span><span class="sxs-lookup"><span data-stu-id="b1967-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="b1967-130">Definir o modo de transferência para `Streamed` habilita a comunicação de streaming em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="b1967-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="b1967-131">Definir o modo de transferência como `StreamedRequest` ou `StreamedResponse` habilita a comunicação de streaming somente na solicitação ou resposta, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b1967-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="b1967-132">O `basicHttpBinding` expõe a `TransferMode` Propriedade na associação como faz `NetTcpBinding` e `NetNamedPipeBinding` .</span><span class="sxs-lookup"><span data-stu-id="b1967-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="b1967-133">Para outros transportes, você deve criar uma associação personalizada para definir o modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="b1967-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="b1967-134">O código de configuração a seguir do exemplo mostra a configuração da `TransferMode` propriedade como streaming no `basicHttpBinding` e uma associação http personalizada:</span><span class="sxs-lookup"><span data-stu-id="b1967-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="b1967-135">Além de definir `transferMode` como `Streamed` , o código de configuração anterior define o `maxReceivedMessageSize` para 64MB.</span><span class="sxs-lookup"><span data-stu-id="b1967-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="b1967-136">Como um mecanismo de defesa, `maxReceivedMessageSize` o coloca um limite no tamanho máximo permitido de mensagens em recebimento.</span><span class="sxs-lookup"><span data-stu-id="b1967-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="b1967-137">O padrão `maxReceivedMessageSize` é 64 KB, que geralmente é muito baixo para cenários de streaming.</span><span class="sxs-lookup"><span data-stu-id="b1967-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="b1967-138">Processando dados conforme são transmitidos</span><span class="sxs-lookup"><span data-stu-id="b1967-138">Processing Data As It Is Streamed</span></span>  

 <span data-ttu-id="b1967-139">As operações `GetStream` `UploadStream` e `EchoStream` todas lidam com o envio de dados diretamente de um arquivo ou o salvamento de dados recebidos diretamente em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b1967-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="b1967-140">No entanto, em alguns casos, há um requisito para enviar ou receber grandes quantidades de dados e executar algum processamento em partes dos dados à medida que eles são enviados ou recebidos.</span><span class="sxs-lookup"><span data-stu-id="b1967-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="b1967-141">Uma maneira de abordar esses cenários é gravar um fluxo personalizado (uma classe derivada de <xref:System.IO.Stream> ) que processa os dados conforme eles são lidos ou gravados.</span><span class="sxs-lookup"><span data-stu-id="b1967-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="b1967-142">A `GetReversedStream` operação e a `ReverseStream` classe são um exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="b1967-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="b1967-143">`GetReversedStream` Cria e retorna uma nova instância do `ReverseStream` .</span><span class="sxs-lookup"><span data-stu-id="b1967-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="b1967-144">O processamento real ocorre quando o sistema lê a partir desse `ReverseStream` objeto.</span><span class="sxs-lookup"><span data-stu-id="b1967-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="b1967-145">A `ReverseStream.Read` implementação lê um bloco de bytes do arquivo subjacente, reverte-os e retorna os bytes invertidos.</span><span class="sxs-lookup"><span data-stu-id="b1967-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="b1967-146">Isso não reverte todo o conteúdo do arquivo; Ele reverte uma parte de bytes de cada vez.</span><span class="sxs-lookup"><span data-stu-id="b1967-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="b1967-147">Este é um exemplo para mostrar como você pode executar o processamento de fluxo, pois o conteúdo está sendo lido ou gravado de e para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="b1967-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="b1967-148">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1967-148">Running the Sample</span></span>  

 <span data-ttu-id="b1967-149">Para executar o exemplo, primeiro crie o serviço e o cliente seguindo as instruções no final deste documento.</span><span class="sxs-lookup"><span data-stu-id="b1967-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="b1967-150">Em seguida, inicie o serviço e o cliente em duas janelas de console diferentes.</span><span class="sxs-lookup"><span data-stu-id="b1967-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="b1967-151">Quando o cliente for iniciado, ele aguardará que você pressione ENTER quando o serviço estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="b1967-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="b1967-152">Em seguida, o cliente chama os métodos `GetStream()` `UploadStream()` e `GetReversedStream()` primeiro por http e, em seguida, sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="b1967-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="b1967-153">Aqui está um exemplo de saída do serviço seguido por exemplo de saída do cliente:</span><span class="sxs-lookup"><span data-stu-id="b1967-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="b1967-154">Saída do serviço:</span><span class="sxs-lookup"><span data-stu-id="b1967-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="b1967-155">Saída do cliente:</span><span class="sxs-lookup"><span data-stu-id="b1967-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1967-156">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1967-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b1967-157">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1967-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b1967-158">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1967-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b1967-159">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1967-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1967-160">Se você usar Svcutil.exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1967-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1967-161">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b1967-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1967-162">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b1967-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b1967-163">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b1967-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1967-164">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b1967-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
