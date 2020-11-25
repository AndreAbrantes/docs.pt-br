---
title: 'Método ICorDebugMergedAssemblyRecord:: GetVersion'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 7352a77fc8f41124d7e6c78a3dfc6ccd6d3a94aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710500"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="f4c67-102">Método ICorDebugMergedAssemblyRecord:: GetVersion</span><span class="sxs-lookup"><span data-stu-id="f4c67-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="f4c67-103">Obtém as informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="f4c67-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4c67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4c67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4c67-105">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="f4c67-106">fora Um ponteiro para o número de versão principal.</span><span class="sxs-lookup"><span data-stu-id="f4c67-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="f4c67-107">fora Um ponteiro para o número de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="f4c67-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="f4c67-108">fora Um ponteiro para o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="f4c67-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="f4c67-109">fora Um ponteiro para o número de revisão.</span><span class="sxs-lookup"><span data-stu-id="f4c67-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4c67-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4c67-110">Remarks</span></span>  

 <span data-ttu-id="f4c67-111">Para obter informações sobre números de versão do assembly, consulte o <xref:System.Version> tópico classe.</span><span class="sxs-lookup"><span data-stu-id="f4c67-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4c67-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f4c67-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c67-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4c67-113">Requirements</span></span>  

 <span data-ttu-id="f4c67-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4c67-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4c67-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4c67-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4c67-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4c67-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4c67-117">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c67-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c67-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4c67-118">See also</span></span>

- [<span data-ttu-id="f4c67-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="f4c67-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="f4c67-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f4c67-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
