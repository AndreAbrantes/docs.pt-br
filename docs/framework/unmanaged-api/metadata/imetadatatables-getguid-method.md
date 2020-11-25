---
title: Método IMetaDataTables::GetGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: f776ac59ff9bd665dc3bfde74e8a8bb0f8acc89e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702453"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="fd32f-102">Método IMetaDataTables::GetGuid</span><span class="sxs-lookup"><span data-stu-id="fd32f-102">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="fd32f-103">Obtém um GUID da linha no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="fd32f-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd32f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd32f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd32f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd32f-105">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="fd32f-106">no O índice da linha da qual obter o GUID.</span><span class="sxs-lookup"><span data-stu-id="fd32f-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="fd32f-107">fora Um ponteiro para um ponteiro para o GUID.</span><span class="sxs-lookup"><span data-stu-id="fd32f-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd32f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd32f-108">Remarks</span></span>  

  <span data-ttu-id="fd32f-109">Não recomendamos o uso desse método, pois ele não retorna resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="fd32f-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="fd32f-110">Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica".</span><span class="sxs-lookup"><span data-stu-id="fd32f-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="fd32f-111">A documentação está disponível online; consulte [padrões ECMA C# e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e o [padrão ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="fd32f-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd32f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd32f-112">Requirements</span></span>  

 <span data-ttu-id="fd32f-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd32f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd32f-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fd32f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd32f-115">**Biblioteca:** Usado como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd32f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd32f-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd32f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd32f-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd32f-117">See also</span></span>

- [<span data-ttu-id="fd32f-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="fd32f-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fd32f-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="fd32f-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
