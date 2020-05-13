---
title: Como partir dados serializados
description: Você pode dividir os dados para evitar problemas com grandes conjuntos. Implemente a interface IXmlSerializable para controlar a serialização e a desserialização.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 860fdcae0d1937f53ee964d9d4631ec812b3d379
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379136"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="9f0ec-104">Como partir dados serializados</span><span class="sxs-lookup"><span data-stu-id="9f0ec-104">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="9f0ec-105">Dois problemas que ocorrem ao enviar grandes conjuntos de dados em mensagens de serviço Web são:</span><span class="sxs-lookup"><span data-stu-id="9f0ec-105">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="9f0ec-106">Um grande conjunto de trabalho (memória) devido ao armazenamento em buffer pelo mecanismo de serialização.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-106">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="9f0ec-107">Consumo de largura de banda desordenado devido à inflação de 33 por cento após a codificação Base64.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-107">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="9f0ec-108">Para resolver esses problemas, implemente a interface <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-108">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="9f0ec-109">Especificamente, implemente os métodos <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> e <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para partir os dados.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-109">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="9f0ec-110">Para implementar o agrupamento do lado do servidor</span><span class="sxs-lookup"><span data-stu-id="9f0ec-110">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="9f0ec-111">Na música do servidor, o método da Web deve desativar o buffer do ASP.NET e retornar um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-111">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="9f0ec-112">O tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> partir os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-112">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="9f0ec-113">Para implementar o processamento do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="9f0ec-113">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="9f0ec-114">Altere o método da Web no proxy do cliente para retornar o tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-114">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="9f0ec-115">Você pode usar uma <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> para fazer isso automaticamente, mas isso não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-115">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="9f0ec-116">Implemente o método <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para ler o fluxo de dados em partes e gravar os bytes no disco.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-116">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="9f0ec-117">Essa implementação também gera eventos de progresso que podem ser usados por um controle de gráfico, como uma barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-117">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f0ec-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f0ec-118">Example</span></span>  
<span data-ttu-id="9f0ec-119">O exemplo de código a seguir mostra o método da Web no cliente que desativa o buffering do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-119">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="9f0ec-120">Ele também mostra a implementação do lado do cliente da interface <xref:System.Xml.Serialization.IXmlSerializable> que parte os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-120">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f0ec-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9f0ec-121">Compiling the code</span></span>  
  
- <span data-ttu-id="9f0ec-122">O código usa os seguintes namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> e <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="9f0ec-122">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0ec-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f0ec-123">See also</span></span>

- [<span data-ttu-id="9f0ec-124">Serialização personalizada</span><span class="sxs-lookup"><span data-stu-id="9f0ec-124">Custom Serialization</span></span>](custom-serialization.md)
