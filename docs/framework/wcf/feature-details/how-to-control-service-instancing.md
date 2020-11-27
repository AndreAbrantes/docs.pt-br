---
title: 'Como: controlar instanciação de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: b028e062acd47118314c9fafd18dd698d04ec244
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257256"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="ce310-102">Como: controlar instanciação de serviço</span><span class="sxs-lookup"><span data-stu-id="ce310-102">How to: Control Service Instancing</span></span>

<span data-ttu-id="ce310-103">Definir o modo de instância de um serviço permite que você especifique quando um <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (e seu objeto de serviço associado definido pelo usuário) são criados.</span><span class="sxs-lookup"><span data-stu-id="ce310-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="ce310-104">Consulte a <xref:System.ServiceModel.InstanceContextMode> enumeração para os modos possíveis.</span><span class="sxs-lookup"><span data-stu-id="ce310-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="ce310-105">Para obter mais informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="ce310-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="ce310-106">Para obter exemplos de funcionamento, consulte [comportamentos](../samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="ce310-106">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="ce310-107">Para controlar o tempo de vida da instância de serviço usando código</span><span class="sxs-lookup"><span data-stu-id="ce310-107">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="ce310-108">Aplique o <xref:System.ServiceModel.ServiceBehaviorAttribute> à classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="ce310-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="ce310-109">Defina a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade como um dos seguintes valores: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> ou <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="ce310-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="ce310-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce310-110">Example</span></span>  

 <span data-ttu-id="ce310-111">O exemplo de código a seguir define a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Propriedade do <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo como <xref:System.ServiceModel.InstanceContextMode.PerCall> .</span><span class="sxs-lookup"><span data-stu-id="ce310-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ce310-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="ce310-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="ce310-113">Serviço: exemplos de comportamentos</span><span class="sxs-lookup"><span data-stu-id="ce310-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
