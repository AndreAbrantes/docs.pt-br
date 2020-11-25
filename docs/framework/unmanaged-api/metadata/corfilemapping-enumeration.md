---
title: Enumeração CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726109"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="024e8-102">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="024e8-102">CorFileMapping Enumeration</span></span>

<span data-ttu-id="024e8-103">Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o método [IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="024e8-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="024e8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="024e8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="024e8-105">Members</span></span>  
  
|<span data-ttu-id="024e8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="024e8-106">Member</span></span>|<span data-ttu-id="024e8-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="024e8-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="024e8-108">O arquivo é mapeado como um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="024e8-108">The file is mapped as a data file.</span></span> <span data-ttu-id="024e8-109">Ou seja, o `SEC_IMAGE` sinalizador não foi passado para a função Microsoft Win32 `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="024e8-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="024e8-110">O arquivo é mapeado para execução, usando a `LoadLibrary` função ou a `CreateFileMapping` função com o `SEC_IMAGE` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="024e8-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="024e8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="024e8-111">Requirements</span></span>  

 <span data-ttu-id="024e8-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="024e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024e8-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="024e8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="024e8-114">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024e8-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="024e8-115">See also</span></span>

- [<span data-ttu-id="024e8-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="024e8-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="024e8-117">Método GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="024e8-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
