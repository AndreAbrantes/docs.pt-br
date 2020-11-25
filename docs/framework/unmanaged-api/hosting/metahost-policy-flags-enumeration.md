---
title: Enumeração METAHOST_POLICY_FLAGS
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: 16fb112cf5b209091001872567c95bb0b3a8ab61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729987"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="9d1eb-102">Enumeração METAHOST_POLICY_FLAGS</span><span class="sxs-lookup"><span data-stu-id="9d1eb-102">METAHOST_POLICY_FLAGS Enumeration</span></span>

<span data-ttu-id="9d1eb-103">Fornece políticas de associação que são comuns à maioria dos hosts de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="9d1eb-104">Essa enumeração é usada pelo método [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d1eb-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d1eb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d1eb-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="9d1eb-106">Membros</span><span class="sxs-lookup"><span data-stu-id="9d1eb-106">Members</span></span>  
  
|<span data-ttu-id="9d1eb-107">Membro</span><span class="sxs-lookup"><span data-stu-id="9d1eb-107">Member</span></span>|<span data-ttu-id="9d1eb-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9d1eb-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="9d1eb-109">Define a política de alta compatibilidade, que não considera Common Language Runtime (CLR) que é carregado no processo atual.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="9d1eb-110">Em vez disso, ele considera apenas o CLRs instalado e as preferências do componente, como derivado do próprio arquivo de assembly, a versão interna declarada ou o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="9d1eb-111">Aplica a política de atualização ao resultado da Associação de versão quando uma correspondência exata não é encontrada, com base no conteúdo de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="9d1eb-112">Isso tem o mesmo efeito que [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9d1eb-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="9d1eb-113">Os resultados da associação são retornados como se a imagem fornecida à chamada fosse iniciada em um novo processo.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="9d1eb-114">Atualmente, `GetRequestedRuntime` o ignora o conjunto de tempos de execução carregável e é associado ao conjunto de tempos de execução instalados.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="9d1eb-115">Esse sinalizador permite que um host determine a qual tempo de execução um EXE se associará quando for iniciado.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="9d1eb-116">Uma caixa de diálogo de erro será exibida se `GetRequestedRuntime` o não conseguir encontrar um tempo de execução compatível com os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="9d1eb-117">A partir do .NET Framework 4,5, essa caixa de diálogo de erro pode assumir a forma de uma caixa de diálogo de recurso do Windows que pergunta se o usuário deseja habilitar o recurso apropriado.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="9d1eb-118">`GetRequestedRuntime` usa a imagem do processo (e qualquer arquivo de configuração correspondente) como entrada adicional para o processo de associação.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="9d1eb-119">Por padrão, `GetRequestedRuntime` o não retorna ao caminho da imagem do processo (normalmente, o exe que foi usado para iniciar o processo) ao determinar o tempo de execução ao qual associar.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="9d1eb-120">`GetRequestedRuntime` deve verificar se o SKU apropriado está instalado quando não há informações disponíveis no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="9d1eb-121">Isso permite que aplicativos que não têm arquivos de configuração falhem normalmente em SKUs menores do que a instalação padrão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="9d1eb-122">Por padrão, `GetRequestedRuntime` o não verifica se o SKU apropriado está instalado, a menos que o atributo SKU seja especificado no elemento arquivo de configuração `<supportedRuntime />` .</span><span class="sxs-lookup"><span data-stu-id="9d1eb-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="9d1eb-123">`GetRequestedRuntime` deve ignorar SEM_FAILCRITICALERRORS (que é definido chamando a função [SetError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) e mostrar a caixa de diálogo de erro.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="9d1eb-124">Por padrão, SEM_FAILCRITICALERRORS suprime a caixa de diálogo de erro.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="9d1eb-125">Ele pode ter sido herdado de outro processo e o erro silencioso pode ser indesejável em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="9d1eb-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d1eb-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d1eb-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d1eb-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d1eb-127">Requirements</span></span>  

 <span data-ttu-id="9d1eb-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d1eb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d1eb-129">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9d1eb-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="9d1eb-130">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d1eb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d1eb-131">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d1eb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1eb-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d1eb-132">See also</span></span>

- [<span data-ttu-id="9d1eb-133">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="9d1eb-133">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="9d1eb-134">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="9d1eb-134">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
