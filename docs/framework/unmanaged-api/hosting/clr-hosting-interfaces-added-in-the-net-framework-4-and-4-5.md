---
title: Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 6ee3b8cdf348a5eade3903e2d26b4f9b93886305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706808"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="a487c-102">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="a487c-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="a487c-103">Esta seção descreve as interfaces que os hosts não gerenciados podem usar para integrar o Common Language Runtime (CLR) no .NET Framework 4, .NET Framework 4,5 e versões posteriores em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a487c-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="a487c-104">Essas interfaces fornecem métodos para um host configurar e carregar o tempo de execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="a487c-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="a487c-105">A partir do .NET Framework 4, todas as interfaces de hospedagem têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="a487c-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="a487c-106">Eles usam o gerenciamento de tempo de vida ( `AddRef` e `Release` ), encapsulamento (contexto implícito) e `QueryInterface` de com.</span><span class="sxs-lookup"><span data-stu-id="a487c-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="a487c-107">Eles não usam tipos COM, como, `BSTR` `SAFEARRAY` ou `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="a487c-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="a487c-108">Não há modelos de apartamento, agregação ou ativação de registro que usam a [função CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span><span class="sxs-lookup"><span data-stu-id="a487c-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a487c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a487c-109">In This Section</span></span>  

 [<span data-ttu-id="a487c-110">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="a487c-110">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="a487c-111">Fornece métodos que inspecionam o uso de memória e CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a487c-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="a487c-112">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="a487c-112">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="a487c-113">Permite que o host especifique o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar as propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a487c-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="a487c-114">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="a487c-114">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="a487c-115">Fornece o método [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) , que permite que um host defina o tamanho do segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo com valores maiores que `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="a487c-115">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="a487c-116">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="a487c-116">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="a487c-117">Fornece métodos que retornam uma versão específica do CLR, listam todos os CLRs instalados, listam todos os tempos de execução em processo, retornam a interface de ativação e detectam a versão do CLR usada para compilar um assembly.</span><span class="sxs-lookup"><span data-stu-id="a487c-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="a487c-118">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="a487c-118">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="a487c-119">Fornece o método [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) que fornece uma interface CLR baseada em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a487c-119">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="a487c-120">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a487c-120">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="a487c-121">Fornece métodos que retornam informações sobre um tempo de execução específico, incluindo versão, diretório e status de carregamento.</span><span class="sxs-lookup"><span data-stu-id="a487c-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="a487c-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a487c-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="a487c-123">Fornece funções estáticas globais básicas para assinar assemblies com nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="a487c-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="a487c-124">Todos os métodos [ICLRStrongName](iclrstrongname-interface.md) retornam o padrão com HResults.</span><span class="sxs-lookup"><span data-stu-id="a487c-124">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="a487c-125">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="a487c-125">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="a487c-126">Fornece a capacidade de criar nomes fortes usando o grupo SHA-2 de algoritmos de hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="a487c-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="a487c-127">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="a487c-127">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="a487c-128">Fornece toda a funcionalidade da [interface ICLRTask](iclrtask-interface.md); Além disso, o fornece métodos que permitem que as anulações de thread sejam atrasadas no thread atual.</span><span class="sxs-lookup"><span data-stu-id="a487c-128">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a487c-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a487c-129">Related Sections</span></span>  

 [<span data-ttu-id="a487c-130">Interfaces e coclasse de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="a487c-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a487c-131">Descreve as interfaces de hospedagem fornecidas com as versões 1,0 e 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a487c-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a487c-132">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="a487c-132">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="a487c-133">Descreve as interfaces de hospedagem fornecidas com as .NET Framework versões 2,0, 3,0 e 3,5.</span><span class="sxs-lookup"><span data-stu-id="a487c-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="a487c-134">Hosting</span><span class="sxs-lookup"><span data-stu-id="a487c-134">Hosting</span></span>](index.md)  
 <span data-ttu-id="a487c-135">Apresenta a hospedagem no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a487c-135">Introduces hosting in the .NET Framework.</span></span>
