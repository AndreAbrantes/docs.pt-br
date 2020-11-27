---
title: Exemplo de DataContractSerializer
description: Este exemplo demonstra o DataContractSerializer no WCF, que executa os serviços de serialização e desserialização gerais para as classes de contrato de dados.
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: d38dddcaff7316f4933207c4aa0897ad47306352
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253606"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="ef738-103">Exemplo de DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="ef738-103">DataContractSerializer Sample</span></span>

<span data-ttu-id="ef738-104">O exemplo DataContractSerializer demonstra o <xref:System.Runtime.Serialization.DataContractSerializer> , que executa os serviços de serialização e desserialização gerais para as classes de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ef738-104">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="ef738-105">O exemplo cria um `Record` objeto, serializa-o para um fluxo de memória e desserializa o fluxo de memória de volta para outro `Record` objeto para demonstrar o uso do <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ef738-105">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="ef738-106">Em seguida, o exemplo serializa o `Record` objeto usando um gravador binário para demonstrar como o gravador afeta a serialização.</span><span class="sxs-lookup"><span data-stu-id="ef738-106">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef738-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ef738-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ef738-108">O contrato de dados do `Record` é mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef738-108">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="ef738-109">O código de exemplo cria um `Record` objeto chamado `record1` e, em seguida, exibe o objeto.</span><span class="sxs-lookup"><span data-stu-id="ef738-109">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="ef738-110">Em seguida, o exemplo usa o <xref:System.Runtime.Serialization.DataContractSerializer> para serializar `record1` em um fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="ef738-110">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="ef738-111">Em seguida, o exemplo usa o <xref:System.Runtime.Serialization.DataContractSerializer> para desserializar o fluxo de memória de volta para um novo `Record` objeto e exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="ef738-111">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="ef738-112">Por padrão, o `DataContractSerializer` codifica objetos em um fluxo usando uma representação textual de XML.</span><span class="sxs-lookup"><span data-stu-id="ef738-112">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="ef738-113">No entanto, você pode influenciar a codificação do XML passando um gravador diferente.</span><span class="sxs-lookup"><span data-stu-id="ef738-113">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="ef738-114">O exemplo cria um gravador binário chamando <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="ef738-114">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="ef738-115">Em seguida, ele passa o gravador e o objeto de registro para o serializador quando ele chama <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="ef738-115">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="ef738-116">Por fim, a amostra libera o gravador e os relatórios sobre o comprimento dos fluxos.</span><span class="sxs-lookup"><span data-stu-id="ef738-116">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="ef738-117">Quando você executa o exemplo, o registro original e o registro desserializado são exibidos, seguidos pela comparação entre o comprimento da codificação de texto e a codificação binária.</span><span class="sxs-lookup"><span data-stu-id="ef738-117">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="ef738-118">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ef738-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef738-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ef738-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ef738-120">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef738-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ef738-121">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef738-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ef738-122">Para executar o exemplo, inicie o cliente no prompt de comando digitando client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="ef738-122">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef738-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ef738-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef738-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ef738-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ef738-125">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ef738-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef738-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ef738-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
