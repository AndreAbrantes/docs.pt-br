---
title: Método IValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: c5c89e0eda6e93e34775c00d5ec8fb4ff0940707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701010"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="9db86-102">Método IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="9db86-102">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="9db86-103">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="9db86-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9db86-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db86-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9db86-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="9db86-106">no O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="9db86-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="9db86-107">no Uma `VEContext` instância que contém informações de contexto sobre o erro de validação.</span><span class="sxs-lookup"><span data-stu-id="9db86-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="9db86-108">[entrada, saída] Uma cadeia de caracteres que contém a mensagem de erro retornada.</span><span class="sxs-lookup"><span data-stu-id="9db86-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="9db86-109">no O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="9db86-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="9db86-110">no Uma matriz segura que contém parâmetros adicionais que descrevem o erro.</span><span class="sxs-lookup"><span data-stu-id="9db86-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db86-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9db86-111">Requirements</span></span>  

 <span data-ttu-id="9db86-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9db86-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db86-113">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="9db86-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="9db86-114">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9db86-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9db86-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9db86-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
