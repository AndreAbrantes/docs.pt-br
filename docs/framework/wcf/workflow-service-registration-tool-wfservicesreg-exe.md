---
title: Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 763b617a99c98383b5b873e4fb8646884f9b5253
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261872"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="81b7f-102">Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="81b7f-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>

<span data-ttu-id="81b7f-103">A ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe) é uma ferramenta autônoma que pode ser usada para adicionar, remover ou reparar os elementos de configuração para os serviços do Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="81b7f-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81b7f-104">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="81b7f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="81b7f-105">Remarks</span></span>  

 <span data-ttu-id="81b7f-106">A ferramenta pode ser encontrada no local de instalação do .NET Framework 3,5, especificamente,%windir%\Microsoft.NET\Framework\v3.5 ou em%windir%\Microsoft.NET\Framework64\v3.5 em computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="81b7f-106">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="81b7f-107">As tabelas a seguir descrevem as opções que podem ser usadas com a ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="81b7f-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="81b7f-108">Opção</span><span class="sxs-lookup"><span data-stu-id="81b7f-108">Option</span></span>|<span data-ttu-id="81b7f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="81b7f-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="81b7f-110">Configura os serviços de fluxo de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="81b7f-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="81b7f-111">Usado em cenários de instalação e reparo.</span><span class="sxs-lookup"><span data-stu-id="81b7f-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="81b7f-112">Remove a configuração dos serviços de fluxo de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="81b7f-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="81b7f-113">Imprimir informações detalhadas (para a configuração ou remoção).</span><span class="sxs-lookup"><span data-stu-id="81b7f-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="81b7f-114">Habilita o formato de log MSI.</span><span class="sxs-lookup"><span data-stu-id="81b7f-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="81b7f-115">Minimiza a janela quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="81b7f-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="81b7f-116">Registro</span><span class="sxs-lookup"><span data-stu-id="81b7f-116">Registration</span></span>  

 <span data-ttu-id="81b7f-117">A ferramenta inspeciona o arquivo de Web.config e registra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="81b7f-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="81b7f-118">.NET Framework assemblies de referência 3,5.</span><span class="sxs-lookup"><span data-stu-id="81b7f-118">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="81b7f-119">Um provedor de compilação para arquivos. xoml.</span><span class="sxs-lookup"><span data-stu-id="81b7f-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="81b7f-120">Manipuladores HTTP para arquivos. xoml e. Rules.</span><span class="sxs-lookup"><span data-stu-id="81b7f-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="81b7f-121">A ferramenta inspeciona o arquivo de Machine.config e registra as seguintes extensões:</span><span class="sxs-lookup"><span data-stu-id="81b7f-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="81b7f-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="81b7f-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="81b7f-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="81b7f-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="81b7f-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="81b7f-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="81b7f-125">A ferramenta também registra os seguintes importadores de metadados do cliente:</span><span class="sxs-lookup"><span data-stu-id="81b7f-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="81b7f-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="81b7f-126">policyImporters</span></span>  
  
- <span data-ttu-id="81b7f-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="81b7f-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="81b7f-128">A ferramenta também registra mapas de ferramentas e manipuladores. xoml e. Rules na metabase do IIS.</span><span class="sxs-lookup"><span data-stu-id="81b7f-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="81b7f-129">Em computadores com Windows Server 2003 e Windows XP (IIS 5,1 e IIS 6,0), um conjunto de mapas de registro. xoml e. Rules é registrado.</span><span class="sxs-lookup"><span data-stu-id="81b7f-129">On Windows Server 2003 and Windows XP machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="81b7f-130">Em computadores de 64 bits, a ferramenta registra os mapas de bits do modo WOW se a `Enable32BitAppOnWin64` opção estiver habilitada ou mapas de bits 64 nativos se a `Enable32BitAppOnWin64` opção estiver desabilitada.</span><span class="sxs-lookup"><span data-stu-id="81b7f-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="81b7f-131">No Windows Vista e no Windows Server 2008 (IIS 7,0 e superior) computadores, dois conjuntos de manipuladores. xoml e. Rules são registrados: um para o modo integrado e outro para o modo clássico.</span><span class="sxs-lookup"><span data-stu-id="81b7f-131">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="81b7f-132">Em computadores de 64 bits, três conjuntos de manipuladores são registrados (independentemente do estado da `Enable32BitAppOnWin64` opção): um para o modo integrado, um para o modo clássico de wow e outro para o modo clássico de 64 bits nativo.</span><span class="sxs-lookup"><span data-stu-id="81b7f-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81b7f-133">Ao contrário de ServiceModelreg.exe, WFServicesReg.exe não permite adicionar, remover ou reparar mapas de chaves ou manipuladores para um site específico.</span><span class="sxs-lookup"><span data-stu-id="81b7f-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="81b7f-134">Para obter uma solução alternativa para esse problema, consulte a seção "reparando o ScriptMaps".</span><span class="sxs-lookup"><span data-stu-id="81b7f-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="81b7f-135">Cenários de uso</span><span class="sxs-lookup"><span data-stu-id="81b7f-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="81b7f-136">Instalando o IIS após a instalação do .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="81b7f-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  

 <span data-ttu-id="81b7f-137">Em um computador com Windows Server 2003, o .NET Framework 3,5 é instalado antes da instalação do IIS.</span><span class="sxs-lookup"><span data-stu-id="81b7f-137">On a Windows Server 2003 machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="81b7f-138">Devido à indisponibilidade da metabase do IIS, a instalação do .NET Framework 3,5 é realizada com sucesso sem instalar os mapas de regras. xoml e. Rules.</span><span class="sxs-lookup"><span data-stu-id="81b7f-138">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="81b7f-139">Depois que o IIS for instalado, você poderá usar a ferramenta de WFServicesReg.exe com a `/c` opção para instalar esses mapas de informações específicos.</span><span class="sxs-lookup"><span data-stu-id="81b7f-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="81b7f-140">Reparando os mapas de chaves</span><span class="sxs-lookup"><span data-stu-id="81b7f-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="81b7f-141">Mapa de site excluído no nó sites</span><span class="sxs-lookup"><span data-stu-id="81b7f-141">Scriptmap deleted under Web Sites node</span></span>  

 <span data-ttu-id="81b7f-142">Em um computador com Windows Server 2003,. xoml ou. Rules é excluído acidentalmente do nó sites.</span><span class="sxs-lookup"><span data-stu-id="81b7f-142">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="81b7f-143">Isso pode ser reparado executando a ferramenta de WFServicesReg.exe com a `/c` opção.</span><span class="sxs-lookup"><span data-stu-id="81b7f-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="81b7f-144">Mapa de site excluído em um local específico</span><span class="sxs-lookup"><span data-stu-id="81b7f-144">Scriptmap deleted under a particular Web site</span></span>  

 <span data-ttu-id="81b7f-145">Em um computador com Windows Server 2003,. xoml ou. Rules é acidentalmente excluído de um site específico (por exemplo, o site padrão) em vez do nó sites.</span><span class="sxs-lookup"><span data-stu-id="81b7f-145">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="81b7f-146">Para reparar manipuladores excluídos para um site específico, você deve executar "WFServicesReg.exe/r" para remover manipuladores de todos os sites da Web e, em seguida, executar "WFServicesReg.exe/c" para criar os manipuladores apropriados para todos os sites da Web.</span><span class="sxs-lookup"><span data-stu-id="81b7f-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="81b7f-147">Configurando manipuladores depois de alternar o modo IIS</span><span class="sxs-lookup"><span data-stu-id="81b7f-147">Configuring handlers after switching IIS mode</span></span>  

 <span data-ttu-id="81b7f-148">Quando o IIS está no modo de configuração compartilhada e .NET Framework 3,5 é instalado, a metabase do IIS é configurada em um local compartilhado.</span><span class="sxs-lookup"><span data-stu-id="81b7f-148">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="81b7f-149">Se você alternar o IIS para o modo de configuração não compartilhado, a metabase local não conterá os manipuladores necessários.</span><span class="sxs-lookup"><span data-stu-id="81b7f-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="81b7f-150">Para configurar a metabase local corretamente, você pode importar a metabase compartilhada para local ou executar "WFServicesReg.exe/c", que configura a metabase local.</span><span class="sxs-lookup"><span data-stu-id="81b7f-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
