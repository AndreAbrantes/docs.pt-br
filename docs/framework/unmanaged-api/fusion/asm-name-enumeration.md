---
title: Enumeração ASM_NAME
ms.date: 03/30/2017
api_name:
- ASM_NAME
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_NAME
helpviewer_keywords:
- ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type:
- apiref
ms.openlocfilehash: 64a34cdf92df345041cb94e9069bcc4d489e3cf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728622"
---
# <a name="asm_name-enumeration"></a><span data-ttu-id="5e4b6-102">Enumeração ASM_NAME</span><span class="sxs-lookup"><span data-stu-id="5e4b6-102">ASM_NAME Enumeration</span></span>

<span data-ttu-id="5e4b6-103">Indica a versão, a compilação, a cultura, a assinatura e assim por diante, do assembly cujas propriedades serão recuperadas ou definidas pelos métodos [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5e4b6-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e4b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e4b6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e4b6-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e4b6-105">Requirements</span></span>  

 <span data-ttu-id="5e4b6-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4b6-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e4b6-107">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5e4b6-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5e4b6-108">**Biblioteca:** Incluído como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e4b6-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e4b6-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4b6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4b6-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e4b6-110">See also</span></span>

- [<span data-ttu-id="5e4b6-111">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5e4b6-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="5e4b6-112">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="5e4b6-112">Fusion Enumerations</span></span>](fusion-enumerations.md)
