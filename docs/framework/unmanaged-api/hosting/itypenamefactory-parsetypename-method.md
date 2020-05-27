---
title: Método ITypeNameFactory::ParseTypeName
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 1d00d150f98e44fb5c6484378266b7d9b238f4a9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008580"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="0ebe5-102">Método ITypeNameFactory::ParseTypeName</span><span class="sxs-lookup"><span data-stu-id="0ebe5-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="0ebe5-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="0ebe5-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebe5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ebe5-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0ebe5-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ebe5-105">Requirements</span></span>  
 <span data-ttu-id="0ebe5-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebe5-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebe5-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ebe5-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ebe5-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ebe5-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ebe5-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebe5-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebe5-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ebe5-110">See also</span></span>

- [<span data-ttu-id="0ebe5-111">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="0ebe5-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
