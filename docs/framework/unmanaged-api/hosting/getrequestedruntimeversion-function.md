---
title: Função GetRequestedRuntimeVersion
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711631"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="9a197-102">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="9a197-102">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="9a197-103">Obtém o número de versão do Common Language Runtime (CLR) solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="9a197-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="9a197-104">Se essa versão não estiver instalada, o obterá a versão mais recente instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="9a197-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="9a197-105">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9a197-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a197-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a197-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a197-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a197-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="9a197-108">no O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a197-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="9a197-109">fora Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9a197-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9a197-110">no O comprimento do buffer de versão.</span><span class="sxs-lookup"><span data-stu-id="9a197-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="9a197-111">fora Um ponteiro para o comprimento da cadeia de caracteres do número de versão.</span><span class="sxs-lookup"><span data-stu-id="9a197-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a197-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9a197-112">Return Value</span></span>  

 <span data-ttu-id="9a197-113">Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="9a197-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9a197-114">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="9a197-114">Return code</span></span>|<span data-ttu-id="9a197-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a197-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9a197-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a197-116">S_OK</span></span>|<span data-ttu-id="9a197-117">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a197-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="9a197-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9a197-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9a197-119">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="9a197-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="9a197-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9a197-120">E_POINTER</span></span>|<span data-ttu-id="9a197-121">`pdwLength` é nulo.</span><span class="sxs-lookup"><span data-stu-id="9a197-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a197-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a197-122">Requirements</span></span>  

 <span data-ttu-id="9a197-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a197-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a197-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a197-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a197-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a197-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a197-126">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a197-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a197-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a197-127">See also</span></span>

- [<span data-ttu-id="9a197-128">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="9a197-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="9a197-129">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="9a197-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="9a197-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="9a197-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
