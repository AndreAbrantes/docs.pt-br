---
title: AssemblyAttributesGoHereS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac8f25632521f2e8abe5209608e42632293feb4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="4bdf7-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="4bdf7-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="4bdf7-103">Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bdf7-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="4bdf7-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bdf7-105">Remarks</span></span>  
 <span data-ttu-id="4bdf7-106">Referências a este tipo podem ser incorporadas dentro netmodules cujos fontes contêm atributos de assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="4bdf7-107">Ao criar um manifesto do assembly de um ou mais netmodules que contêm referências a esses tipos, ALink usa informações associadas a essas referências para emitir os atributos personalizados real.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="4bdf7-108">Como tal, esse tipo nunca é instanciado e referências a ele são usadas apenas como parte do processo de compilação e não servem para nenhuma finalidade no assembly final.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="4bdf7-109">Referências a este tipo indicam atributos personalizados que são relacionadas à segurança e não use vários.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="4bdf7-110">Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="4bdf7-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdf7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bdf7-111">Requirements</span></span>  
 <span data-ttu-id="4bdf7-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="4bdf7-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdf7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdf7-113">See Also</span></span>  
 [<span data-ttu-id="4bdf7-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="4bdf7-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="4bdf7-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="4bdf7-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="4bdf7-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="4bdf7-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
