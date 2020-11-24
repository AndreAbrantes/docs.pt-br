---
title: Enumeração CorCheckDuplicatesFor
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 4acdfd6df410f229a002fa191ef24766748a1262
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672351"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="3a84b-102">Enumeração CorCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="3a84b-102">CorCheckDuplicatesFor Enumeration</span></span>

<span data-ttu-id="3a84b-103">Especifica os tokens de metadados que serão verificados em busca de duplicatas.</span><span class="sxs-lookup"><span data-stu-id="3a84b-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a84b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a84b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="3a84b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3a84b-105">Members</span></span>  
  
|<span data-ttu-id="3a84b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3a84b-106">Member</span></span>|<span data-ttu-id="3a84b-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="3a84b-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="3a84b-108">Verifique se há duplicatas em todos os tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="3a84b-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="3a84b-109">Não usado.</span><span class="sxs-lookup"><span data-stu-id="3a84b-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="3a84b-110">Não verifique os tokens de metadados em busca de duplicatas.</span><span class="sxs-lookup"><span data-stu-id="3a84b-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="3a84b-111">Verifique se há duplicatas de `mdTypeDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="3a84b-112">Verifique se há duplicatas de `mdInterfaceImpl` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="3a84b-113">Verifique se há duplicatas de `mdMethodDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="3a84b-114">Verifique se há duplicatas de `mdTypeRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="3a84b-115">Verifique se há duplicatas de `mdMemberRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="3a84b-116">Verifique se há duplicatas de `mdCustomAttribute` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="3a84b-117">Verifique se há duplicatas de `mdParamDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="3a84b-118">Verifique se há duplicatas de `mdPermission` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="3a84b-119">Verifique se há duplicatas de `mdProperty` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="3a84b-120">Verifique se há duplicatas de `mdEvent` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="3a84b-121">Verifique se há duplicatas de `mdFieldDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="3a84b-122">Verifique se há duplicatas de `mdSignature` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="3a84b-123">Verifique se há duplicatas de `mdModuleRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="3a84b-124">Verifique se há duplicatas de `mdTypeSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="3a84b-125">Verifique se há duplicatas de `mdImplMap` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="3a84b-126">Verifique se há duplicatas de `mdAssemblyRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="3a84b-127">Verifique se há duplicatas de `mdFile` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="3a84b-128">Verifique se há duplicatas de `mdExportedType` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="3a84b-129">Verifique se há duplicatas de `mdManifestResource` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="3a84b-130">Verifique se há duplicatas de `mdGenericParam` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="3a84b-131">Verifique se há duplicatas de `mdMethodSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="3a84b-132">Verifique se há duplicatas de `mdGenericParamConstraint` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="3a84b-133">Verifique se há duplicatas de `mdAssembly` tokens.</span><span class="sxs-lookup"><span data-stu-id="3a84b-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="3a84b-134">Verifique se há duplicatas `mdMemberRef` de `mdTypeRef` tokens,,, `mdSignature` `mdTypeSpec` e `mdMethodSpec` .</span><span class="sxs-lookup"><span data-stu-id="3a84b-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a84b-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a84b-135">Requirements</span></span>  

 <span data-ttu-id="3a84b-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a84b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a84b-137">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3a84b-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3a84b-138">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a84b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a84b-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a84b-139">See also</span></span>

- [<span data-ttu-id="3a84b-140">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3a84b-140">Metadata Enumerations</span></span>](metadata-enumerations.md)
