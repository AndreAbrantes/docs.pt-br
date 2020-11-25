---
title: Método ICorProfilerCallback::ClassLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 3be00d278a92398ad282a071f3e313e5de0e65a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700282"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="9ad7f-102">Método ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="9ad7f-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>

<span data-ttu-id="9ad7f-103">Notifica o criador de perfil que a conclusão do carregamento de uma classe.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ad7f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ad7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ad7f-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="9ad7f-106">\[in] identifica a classe que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="9ad7f-107">\[in] um HRESULT que indica se a classe foi carregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ad7f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ad7f-108">Remarks</span></span>  

 <span data-ttu-id="9ad7f-109">O valor de `classId` não é válido para uma solicitação de informações até que o `ClassLoadFinished` método seja chamado.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="9ad7f-110">Algumas partes do carregamento da classe podem continuar após o `ClassLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="9ad7f-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9ad7f-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9ad7f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad7f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ad7f-113">Requirements</span></span>  

 <span data-ttu-id="9ad7f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad7f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad7f-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ad7f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ad7f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ad7f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ad7f-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad7f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad7f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ad7f-118">See also</span></span>

- [<span data-ttu-id="9ad7f-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9ad7f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ad7f-120">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="9ad7f-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
