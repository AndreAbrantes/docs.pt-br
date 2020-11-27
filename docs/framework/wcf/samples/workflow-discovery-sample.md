---
title: Exemplo de descoberta de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 44d1fed74782051a926ced95c49f3e3cb14f2b9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263768"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="9f6c4-102">Exemplo de descoberta de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9f6c4-102">Workflow Discovery Sample</span></span>

<span data-ttu-id="9f6c4-103">Este exemplo demonstra como tornar um serviço de fluxo de trabalho detectável e como criar uma atividade de código personalizada que pesquisa um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9f6c4-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="9f6c4-104">Demonstrates</span></span>  

 <span data-ttu-id="9f6c4-105">Localização da descoberta de atividades e uso de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9f6c4-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9f6c4-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="9f6c4-106">Discussion</span></span>  

 <span data-ttu-id="9f6c4-107">Na primeira parte do exemplo, um serviço de fluxo de trabalho torna-se detectável usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="9f6c4-108">A configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos).</span><span class="sxs-lookup"><span data-stu-id="9f6c4-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="9f6c4-109">No cliente, o exemplo usa uma atividade de código personalizada, que usa a descoberta para procurar um serviço que corresponda a um contrato específico.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="9f6c4-110">A atividade de código gera um URI, que é usado posteriormente por uma atividade de envio.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9f6c4-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9f6c4-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9f6c4-112">Este exemplo usa pontos de extremidade HTTP, que devem ter ACLs de URL adequadas para execução (consulte [Configurando http e HTTPS](../feature-details/configuring-http-and-https.md) para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="9f6c4-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="9f6c4-113">A execução do comando a seguir em um prompt de comandos com privilégios elevados deve adicionar as ACLs apropriadas.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="9f6c4-114">Se o seu shell não entender o formato da variável, substitua o seu domínio e o nome de usuário pelos argumentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> <span data-ttu-id="9f6c4-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f6c4-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9f6c4-117">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f6c4-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9f6c4-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
