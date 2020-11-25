---
title: Função GetRequestedRuntimeInfo
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: b120b854e1787824808dd64d95b0fa78ba6c9fa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705482"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="58372-102">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="58372-102">GetRequestedRuntimeInfo Function</span></span>

<span data-ttu-id="58372-103">Obtém informações de versão e diretório sobre o Common Language Runtime (CLR) solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58372-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="58372-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="58372-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58372-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58372-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58372-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58372-106">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="58372-107">no O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58372-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="58372-108">no Uma cadeia de caracteres que especifica o número de versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="58372-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="58372-109">no O nome do arquivo de configuração associado ao `pExe` .</span><span class="sxs-lookup"><span data-stu-id="58372-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="58372-110">no Um ou mais dos [STARTUP_FLAGS](startup-flags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="58372-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="58372-111">no Um ou mais dos [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="58372-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="58372-112">fora Um buffer que contém o caminho do diretório para o tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="58372-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="58372-113">no O comprimento do buffer de diretório.</span><span class="sxs-lookup"><span data-stu-id="58372-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="58372-114">fora Um ponteiro para o comprimento da cadeia de caracteres do caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="58372-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="58372-115">fora Um buffer que contém o número de versão do tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="58372-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="58372-116">no O comprimento do buffer de cadeia de caracteres da versão.</span><span class="sxs-lookup"><span data-stu-id="58372-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="58372-117">fora Um ponteiro para o comprimento da cadeia de caracteres da versão.</span><span class="sxs-lookup"><span data-stu-id="58372-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58372-118">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="58372-118">Return Value</span></span>  

 <span data-ttu-id="58372-119">Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="58372-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="58372-120">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="58372-120">Return code</span></span>|<span data-ttu-id="58372-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="58372-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="58372-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="58372-122">S_OK</span></span>|<span data-ttu-id="58372-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="58372-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="58372-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="58372-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="58372-125">O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="58372-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="58372-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="58372-126">- or -</span></span><br /><br /> <span data-ttu-id="58372-127">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="58372-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58372-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="58372-128">Remarks</span></span>  

 <span data-ttu-id="58372-129">O `GetRequestedRuntimeInfo` método retorna informações de tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="58372-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="58372-130">Na versão .NET Framework 2,0, você pode obter informações sobre a versão instalada mais recente usando o `GetRequestedRuntimeInfo` método da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="58372-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="58372-131">Especifique os `pExe` `pwszVersion` parâmetros, e `pConfigurationFile` como NULL.</span><span class="sxs-lookup"><span data-stu-id="58372-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="58372-132">Especifique o sinalizador de RUNTIME_INFO_UPGRADE_VERSION nas `RUNTIME_INFO_FLAGS` enumerações para o `runtimeInfoFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="58372-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="58372-133">O `GetRequestedRuntimeInfo` método não retorna a versão mais recente do CLR nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="58372-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="58372-134">Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma versão CLR específica.</span><span class="sxs-lookup"><span data-stu-id="58372-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="58372-135">Observe que o .NET Framework usará o arquivo de configuração mesmo se você especificar NULL para o `pConfigurationFile` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="58372-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="58372-136">O método [CorBindToRuntimeEx](corbindtoruntimeex-function.md) foi chamado especificando uma versão anterior do CLR.</span><span class="sxs-lookup"><span data-stu-id="58372-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="58372-137">Um aplicativo que foi compilado para uma versão anterior do CLR está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="58372-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="58372-138">Para o `runtimeInfoFlags` parâmetro, você pode especificar apenas uma das constantes de arquitetura da `RUNTIME_INFO_FLAGS` enumeração de cada vez:</span><span class="sxs-lookup"><span data-stu-id="58372-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="58372-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="58372-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="58372-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="58372-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="58372-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="58372-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58372-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58372-142">Requirements</span></span>  

 <span data-ttu-id="58372-143">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58372-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58372-144">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="58372-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58372-145">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58372-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58372-146">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58372-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58372-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="58372-147">See also</span></span>

- [<span data-ttu-id="58372-148">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="58372-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="58372-149">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="58372-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="58372-150">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="58372-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
