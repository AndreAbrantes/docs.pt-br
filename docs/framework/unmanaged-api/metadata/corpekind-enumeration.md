---
title: Enumeração CorPEKind
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 001be0c5e8897bacf76d2a044fb9400768473052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673521"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="bfcac-102">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="bfcac-102">CorPEKind Enumeration</span></span>

<span data-ttu-id="bfcac-103">Contém valores que descrevem um arquivo executável portátil (PE), como retornado de uma chamada para [IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfcac-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfcac-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="bfcac-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bfcac-105">Members</span></span>  
  
|<span data-ttu-id="bfcac-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bfcac-106">Member</span></span>|<span data-ttu-id="bfcac-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="bfcac-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="bfcac-108">Indica que este não é um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="bfcac-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="bfcac-109">Indica que este arquivo PE contém apenas código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bfcac-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="bfcac-110">Indica que esse arquivo PE faz chamadas Win32.</span><span class="sxs-lookup"><span data-stu-id="bfcac-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="bfcac-111">Indica que este arquivo PE é executado em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bfcac-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="bfcac-112">Indica que este arquivo PE é um código nativo.</span><span class="sxs-lookup"><span data-stu-id="bfcac-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="bfcac-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="bfcac-113">pe32BitPreferred</span></span>|<span data-ttu-id="bfcac-114">Indica que este arquivo PE é de plataforma neutra e prefere ser carregado em um ambiente de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="bfcac-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfcac-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfcac-115">Remarks</span></span>  

 <span data-ttu-id="bfcac-116">Esses valores podem ser usados em combinações de bits.</span><span class="sxs-lookup"><span data-stu-id="bfcac-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcac-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfcac-117">Requirements</span></span>  

 <span data-ttu-id="bfcac-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfcac-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcac-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="bfcac-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bfcac-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcac-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="bfcac-121">See also</span></span>

- [<span data-ttu-id="bfcac-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="bfcac-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
