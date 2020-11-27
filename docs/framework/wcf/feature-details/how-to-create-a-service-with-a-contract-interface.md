---
title: 'Como: criar um serviço com interface de contrato'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 2234e6fe8d0ee2e0029a061ba96ef84f840f0c9b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286338"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="f4c9a-102">Como: criar um serviço com interface de contrato</span><span class="sxs-lookup"><span data-stu-id="f4c9a-102">How to: Create a Service with a Contract Interface</span></span>

<span data-ttu-id="f4c9a-103">A maneira preferida de criar um contrato de Windows Communication Foundation (WCF) é usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="f4c9a-104">Este contrato especifica a coleção e a estrutura de mensagens necessárias para acessar as operações que o serviço oferece.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="f4c9a-105">Essa interface define os tipos de entrada e saída aplicando a <xref:System.ServiceModel.ServiceContractAttribute> classe à interface e a <xref:System.ServiceModel.OperationContractAttribute> classe aos métodos que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="f4c9a-106">Para obter mais informações sobre contratos de serviço, consulte [Designing Service Contracts](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f4c9a-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="f4c9a-107">Criando um contrato do WCF com uma interface</span><span class="sxs-lookup"><span data-stu-id="f4c9a-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="f4c9a-108">Crie uma nova interface usando Visual Basic, C# ou qualquer outra linguagem de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="f4c9a-109">Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="f4c9a-110">Defina os métodos na interface.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="f4c9a-111">Aplique a <xref:System.ServiceModel.OperationContractAttribute> classe a cada método que deve ser exposto como parte do contrato do WCF público.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c9a-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4c9a-112">Example</span></span>  

 <span data-ttu-id="f4c9a-113">O exemplo de código a seguir mostra uma interface que define um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="f4c9a-114">Por padrão, os métodos que têm a <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="f4c9a-115">Para obter mais informações sobre esse padrão de mensagem, consulte [como: criar um contrato de Request-Reply](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f4c9a-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="f4c9a-116">Você também pode criar e usar outros padrões de mensagem definindo as propriedades do atributo.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="f4c9a-117">Para obter mais exemplos, consulte [como: criar um contrato de One-Way](how-to-create-a-one-way-contract.md) e [como criar um contrato duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f4c9a-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c9a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4c9a-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
