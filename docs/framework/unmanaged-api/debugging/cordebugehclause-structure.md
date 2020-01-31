---
title: Estrutura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: 197c33511a474eb8291e4361ebb3c21fb3720cae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789419"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="8021c-102">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="8021c-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="8021c-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8021c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8021c-104">Representa uma cláusula de manipulação de exceção (EH) para um determinado código de linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="8021c-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8021c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8021c-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="8021c-106">Membros</span><span class="sxs-lookup"><span data-stu-id="8021c-106">Members</span></span>  
  
|<span data-ttu-id="8021c-107">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8021c-107">Member</span></span>|<span data-ttu-id="8021c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8021c-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="8021c-109">Um campo de bits que descreve as informações de exceção na cláusula EH.</span><span class="sxs-lookup"><span data-stu-id="8021c-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="8021c-110">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="8021c-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="8021c-111">O deslocamento, em bytes, do bloco `try` a partir do início do corpo do método.</span><span class="sxs-lookup"><span data-stu-id="8021c-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="8021c-112">O tamanho, em bytes, do bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="8021c-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="8021c-113">A localização do manipulador desse bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="8021c-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="8021c-114">O tamanho, em bytes, do código do manipulador.</span><span class="sxs-lookup"><span data-stu-id="8021c-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="8021c-115">O token de metadados para um manipulador de exceção com base em tipo.</span><span class="sxs-lookup"><span data-stu-id="8021c-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="8021c-116">O deslocamento, em bytes, do início do corpo do método para um manipulador de exceção com base em filtro.</span><span class="sxs-lookup"><span data-stu-id="8021c-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8021c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8021c-117">Remarks</span></span>  
 <span data-ttu-id="8021c-118">Uma matriz de valores de `CoreDebugEHClause` é retornada pelo método [GetEHClauses](icordebugilcode-getehclauses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8021c-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="8021c-119">As informações da cláusula EH são definidas pela especificação CLI.</span><span class="sxs-lookup"><span data-stu-id="8021c-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="8021c-120">Para obter mais informações, consulte [Standard ECMA-355: Common Language Infrastructure (CLI), 6º edição](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="8021c-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="8021c-121">O campo `flags` pode conter os seguintes sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="8021c-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="8021c-122">Observe se eles não estão definidos em CorDebug.idl ou em CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="8021c-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="8021c-123">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="8021c-123">Flag</span></span>|<span data-ttu-id="8021c-124">Value</span><span class="sxs-lookup"><span data-stu-id="8021c-124">Value</span></span>|<span data-ttu-id="8021c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8021c-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="8021c-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="8021c-126">0x00000000</span></span>|<span data-ttu-id="8021c-127">Uma cláusula de exceção digitada.</span><span class="sxs-lookup"><span data-stu-id="8021c-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="8021c-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="8021c-128">0x00000001</span></span>|<span data-ttu-id="8021c-129">Uma cláusula do manipulador e do filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="8021c-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="8021c-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="8021c-130">0x00000002</span></span>|<span data-ttu-id="8021c-131">Uma cláusula `finally`.</span><span class="sxs-lookup"><span data-stu-id="8021c-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="8021c-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="8021c-132">0x00000004</span></span>|<span data-ttu-id="8021c-133">Uma cláusula de falha (uma cláusula `finally` que é chamada somente quando uma exceção é lançada).</span><span class="sxs-lookup"><span data-stu-id="8021c-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8021c-134">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8021c-134">Requirements</span></span>  
 <span data-ttu-id="8021c-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8021c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8021c-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8021c-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8021c-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8021c-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8021c-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8021c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8021c-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="8021c-139">See also</span></span>

- [<span data-ttu-id="8021c-140">Método GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="8021c-140">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="8021c-141">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8021c-141">Debugging Structures</span></span>](debugging-structures.md)
