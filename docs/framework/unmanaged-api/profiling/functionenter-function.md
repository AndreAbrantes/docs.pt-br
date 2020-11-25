---
title: Função FunctionEnter
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 9bc88d7dd5b00213da634dc9f511cfe0d39b42f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729831"
---
# <a name="functionenter-function"></a><span data-ttu-id="5538c-102">Função FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="5538c-102">FunctionEnter Function</span></span>

<span data-ttu-id="5538c-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="5538c-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5538c-104">A `FunctionEnter` função é preterida no .NET Framework versão 2,0, e seu uso incorrerá em uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="5538c-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="5538c-105">Em vez disso, use a função [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5538c-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5538c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5538c-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5538c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5538c-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="5538c-108">\[in] o identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="5538c-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="5538c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5538c-109">Remarks</span></span>  

 <span data-ttu-id="5538c-110">A `FunctionEnter` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="5538c-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="5538c-111">A implementação deve usar o `__declspec` `naked` atributo de classe de armazenamento ().</span><span class="sxs-lookup"><span data-stu-id="5538c-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="5538c-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="5538c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="5538c-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="5538c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="5538c-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="5538c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5538c-115">A implementação de `FunctionEnter` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5538c-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="5538c-116">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5538c-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5538c-117">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionEnter` retorno.</span><span class="sxs-lookup"><span data-stu-id="5538c-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="5538c-118">Além disso, a `FunctionEnter` função não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5538c-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5538c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5538c-119">Requirements</span></span>  

 <span data-ttu-id="5538c-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5538c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5538c-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="5538c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5538c-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5538c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5538c-123">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="5538c-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5538c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="5538c-124">See also</span></span>

- [<span data-ttu-id="5538c-125">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="5538c-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="5538c-126">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="5538c-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="5538c-127">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="5538c-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="5538c-128">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="5538c-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="5538c-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="5538c-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
