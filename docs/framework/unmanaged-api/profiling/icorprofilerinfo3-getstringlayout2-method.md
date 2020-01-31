---
title: Método ICorProfilerInfo3::GetStringLayout2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862250"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="bfd01-102">Método ICorProfilerInfo3::GetStringLayout2</span><span class="sxs-lookup"><span data-stu-id="bfd01-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="bfd01-103">Obtém informações sobre o layout de um objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfd01-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="bfd01-104">Esse método substitui o método [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bfd01-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd01-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfd01-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfd01-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfd01-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="bfd01-107">fora Um ponteiro para o deslocamento do local, relativo ao ponteiro de `ObjectID`, que armazena o comprimento da própria cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfd01-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="bfd01-108">O comprimento é armazenado como um `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bfd01-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="bfd01-109">fora Um ponteiro para o deslocamento do buffer, relativo ao ponteiro de `ObjectID`, que armazena a cadeia de caracteres de largura inteira.</span><span class="sxs-lookup"><span data-stu-id="bfd01-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfd01-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfd01-110">Remarks</span></span>  
 <span data-ttu-id="bfd01-111">Cadeias de caracteres podem ou não ser terminadas em nulo.</span><span class="sxs-lookup"><span data-stu-id="bfd01-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfd01-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="bfd01-112">Requirements</span></span>  
 <span data-ttu-id="bfd01-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd01-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd01-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bfd01-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfd01-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfd01-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfd01-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd01-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd01-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="bfd01-117">See also</span></span>

- [<span data-ttu-id="bfd01-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="bfd01-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bfd01-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bfd01-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
