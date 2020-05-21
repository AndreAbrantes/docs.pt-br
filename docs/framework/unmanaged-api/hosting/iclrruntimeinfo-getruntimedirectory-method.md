---
title: Método ICLRRuntimeInfo::GetRuntimeDirectory
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: d744abf5c502e9b9510cf9fd6479149b6c2177cc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762208"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="6ed40-102">Método ICLRRuntimeInfo::GetRuntimeDirectory</span><span class="sxs-lookup"><span data-stu-id="6ed40-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="6ed40-103">Obtém o diretório de instalação do Common Language Runtime (CLR) associado a essa interface.</span><span class="sxs-lookup"><span data-stu-id="6ed40-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="6ed40-104">Esse método substitui a função [GetCORSystemDirectory](getcorsystemdirectory-function.md) fornecida no .NET Framework versões 2,0, 3,0 e 3,5.</span><span class="sxs-lookup"><span data-stu-id="6ed40-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed40-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ed40-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed40-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ed40-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="6ed40-107">fora Retorna o diretório de instalação do CLR.</span><span class="sxs-lookup"><span data-stu-id="6ed40-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="6ed40-108">O caminho de instalação é totalmente qualificado; por exemplo, "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="6ed40-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="6ed40-109">[entrada, saída] Especifica o tamanho de `pwzBuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="6ed40-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="6ed40-110">Se `pwzBuffer` for NULL, `pchBuffer` retornará o tamanho necessário de `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="6ed40-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ed40-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6ed40-111">Return Value</span></span>  
 <span data-ttu-id="6ed40-112">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="6ed40-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6ed40-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ed40-113">HRESULT</span></span>|<span data-ttu-id="6ed40-114">Description</span><span class="sxs-lookup"><span data-stu-id="6ed40-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ed40-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ed40-115">S_OK</span></span>|<span data-ttu-id="6ed40-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="6ed40-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="6ed40-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6ed40-117">E_POINTER</span></span>|<span data-ttu-id="6ed40-118">`pwzBuffer` ou `pchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="6ed40-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ed40-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ed40-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed40-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ed40-120">Requirements</span></span>  
 <span data-ttu-id="6ed40-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed40-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed40-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6ed40-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6ed40-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ed40-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ed40-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed40-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed40-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="6ed40-125">See also</span></span>

- [<span data-ttu-id="6ed40-126">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="6ed40-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6ed40-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="6ed40-127">Hosting</span></span>](index.md)
