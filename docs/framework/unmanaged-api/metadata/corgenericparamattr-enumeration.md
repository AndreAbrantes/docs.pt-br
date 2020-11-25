---
title: Enumeração CorGenericParamAttr
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704900"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="b7140-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="b7140-102">CorGenericParamAttr Enumeration</span></span>

<span data-ttu-id="b7140-103">Contém valores que descrevem os <xref:System.Type> parâmetros para tipos genéricos, conforme usado em chamadas para [IMetaDataEmit2::D efinegenericparam](imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7140-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7140-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7140-104">Syntax</span></span>  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b7140-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7140-105">Members</span></span>  
  
|<span data-ttu-id="b7140-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b7140-106">Member</span></span>|<span data-ttu-id="b7140-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="b7140-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="b7140-108">A variação de parâmetro aplica-se somente a parâmetros genéricos para interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="b7140-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="b7140-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="b7140-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="b7140-110">Indica covariância.</span><span class="sxs-lookup"><span data-stu-id="b7140-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="b7140-111">Indica contravariância.</span><span class="sxs-lookup"><span data-stu-id="b7140-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="b7140-112">Restrições especiais podem ser aplicadas a qualquer <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7140-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="b7140-113">Indica que nenhuma restrição se aplica ao <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7140-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="b7140-114">Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="b7140-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="b7140-115">Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor que não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="b7140-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="b7140-116">Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não aceite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b7140-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7140-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7140-117">Requirements</span></span>  

 <span data-ttu-id="b7140-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7140-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7140-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b7140-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b7140-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7140-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7140-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7140-121">See also</span></span>

- [<span data-ttu-id="b7140-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="b7140-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
