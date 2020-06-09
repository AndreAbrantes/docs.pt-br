---
title: Serialização e transferência de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593474"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="12dad-102">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="12dad-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="12dad-103">Em um sistema conectado, os serviços e os clientes dependem da troca de dados para realizar qualquer tarefa.</span><span class="sxs-lookup"><span data-stu-id="12dad-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="12dad-104">Como desenvolvedor de um serviço ou cliente, você também deve entender como a Windows Communication Foundation (WCF) lida com dados e a serialização de dados para criar aplicativos que são eficientes e fáceis de manter.</span><span class="sxs-lookup"><span data-stu-id="12dad-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12dad-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="12dad-105">In This Section</span></span>  
 [<span data-ttu-id="12dad-106">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="12dad-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="12dad-107">Descreve os conceitos básicos de transferência de dados em serviços.</span><span class="sxs-lookup"><span data-stu-id="12dad-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="12dad-108">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="12dad-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="12dad-109">Descreve o que são contratos de dados e como criá-los e usá-los.</span><span class="sxs-lookup"><span data-stu-id="12dad-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="12dad-110">Serializador de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="12dad-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="12dad-111">Descreve como realizar a serialização de dados com a <xref:System.Runtime.Serialization.DataContractSerializer> classe ou qualquer extensão da <xref:System.Runtime.Serialization.XmlObjectSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="12dad-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="12dad-112">Usando a classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="12dad-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="12dad-113">Descreve como e por que usar a <xref:System.Xml.Serialization.XmlSerializer> classe, uma alternativa para a <xref:System.Runtime.Serialization.DataContractSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="12dad-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="12dad-114">Utilizando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="12dad-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="12dad-115">Descreve como os contratos de mensagem permitem um controle fino sobre mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="12dad-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="12dad-116">Usando a classe de mensagens</span><span class="sxs-lookup"><span data-stu-id="12dad-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="12dad-117">Descreve como usar recursos de classe de mensagem.</span><span class="sxs-lookup"><span data-stu-id="12dad-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="12dad-118">Filtragem</span><span class="sxs-lookup"><span data-stu-id="12dad-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="12dad-119">Descreve a filtragem, que habilita o pré-processamento de uma mensagem com base em vários critérios.</span><span class="sxs-lookup"><span data-stu-id="12dad-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="12dad-120">Dados grandes e streaming</span><span class="sxs-lookup"><span data-stu-id="12dad-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="12dad-121">Descreve como enviar um grande bloco de dados, como um arquivo binário.</span><span class="sxs-lookup"><span data-stu-id="12dad-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="12dad-122">Considerações de segurança para dados</span><span class="sxs-lookup"><span data-stu-id="12dad-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="12dad-123">Descreve os itens que estão cientes do ao programar a transferência e a serialização de dados.</span><span class="sxs-lookup"><span data-stu-id="12dad-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="12dad-124">Visão geral da arquitetura de transferência de dados</span><span class="sxs-lookup"><span data-stu-id="12dad-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="12dad-125">Descreve uma exibição do design geral de transferência de dados no WCF.</span><span class="sxs-lookup"><span data-stu-id="12dad-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="12dad-126">Referência</span><span class="sxs-lookup"><span data-stu-id="12dad-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="12dad-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="12dad-127">Related Sections</span></span>  
 [<span data-ttu-id="12dad-128">Estendendo codificadores e serializadores</span><span class="sxs-lookup"><span data-stu-id="12dad-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="12dad-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12dad-129">See also</span></span>

- [<span data-ttu-id="12dad-130">Práticas recomendadas: controle de versão de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="12dad-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="12dad-131">Controle de versão de serviço</span><span class="sxs-lookup"><span data-stu-id="12dad-131">Service Versioning</span></span>](../service-versioning.md)
