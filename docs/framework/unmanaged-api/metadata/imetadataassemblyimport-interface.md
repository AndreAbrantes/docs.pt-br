---
title: Interface IMetaDataAssemblyImport
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: c556fe247754b363ece0c5dc60750068276ddcc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714751"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="da9df-102">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="da9df-102">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="da9df-103">Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="da9df-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da9df-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="da9df-104">Methods</span></span>  
  
|<span data-ttu-id="da9df-105">Método</span><span class="sxs-lookup"><span data-stu-id="da9df-105">Method</span></span>|<span data-ttu-id="da9df-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="da9df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da9df-107">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="da9df-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="da9df-108">Libera o identificador para o enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="da9df-109">Método EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="da9df-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="da9df-110">Obtém um ponteiro de interface para um enumerador que contém os `mdAssemblyRef` tokens dos assemblies referenciados pelo assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="da9df-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="da9df-111">Método EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="da9df-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="da9df-112">Obtém um ponteiro de interface para um enumerador que contém os `mdExportedType` tokens dos tipos com referenciados pelo assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="da9df-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="da9df-113">Método EnumFiles</span><span class="sxs-lookup"><span data-stu-id="da9df-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="da9df-114">Obtém um ponteiro de interface para um enumerador que contém os `mdFile` tokens dos arquivos referenciados pelo assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="da9df-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="da9df-115">Método EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="da9df-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="da9df-116">Obtém um ponteiro de interface para um enumerador que contém os `mdManifestResource` tokens dos recursos referenciados pelo assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="da9df-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="da9df-117">Método FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="da9df-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="da9df-118">Obtém uma matriz de `mdAssemblyRef` tokens para os assemblies com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="da9df-119">Método FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="da9df-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="da9df-120">Obtém um `mdExportedType` token para o tipo com com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="da9df-121">Método FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="da9df-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="da9df-122">Obtém um `mdManifestResource` token para o recurso com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="da9df-123">Método GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="da9df-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="da9df-124">Obtém o token para o assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="da9df-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="da9df-125">Método GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="da9df-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="da9df-126">Obtém as configurações de Propriedade do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="da9df-127">Método GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="da9df-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="da9df-128">Obtém as configurações de Propriedade do `mdAssemblyRef` token especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="da9df-129">Método GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="da9df-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="da9df-130">Obtém as configurações de Propriedade do tipo COM especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="da9df-131">Método GetFileProps</span><span class="sxs-lookup"><span data-stu-id="da9df-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="da9df-132">Obtém as configurações de Propriedade do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="da9df-133">Método GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="da9df-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="da9df-134">Obtém as configurações de Propriedade do recurso de manifesto especificado.</span><span class="sxs-lookup"><span data-stu-id="da9df-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da9df-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da9df-135">Requirements</span></span>  

 <span data-ttu-id="da9df-136">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da9df-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da9df-137">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="da9df-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da9df-138">**Biblioteca:** Usado como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da9df-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da9df-139">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da9df-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9df-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="da9df-140">See also</span></span>

- [<span data-ttu-id="da9df-141">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="da9df-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="da9df-142">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="da9df-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
