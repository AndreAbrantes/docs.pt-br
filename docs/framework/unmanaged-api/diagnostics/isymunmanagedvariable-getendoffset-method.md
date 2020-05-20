---
title: Método ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 91117eae23d38f3bc608f3203ebe53f92516c9c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610490"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="0224a-102">Método ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="0224a-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="0224a-103">Obtém o deslocamento final dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="0224a-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="0224a-104">Se essa for uma variável local dentro de um escopo, o deslocamento final se enquadrará dentro dos deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="0224a-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0224a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0224a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0224a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0224a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0224a-107">fora Um ponteiro para um `ULONG32` que recebe o deslocamento final.</span><span class="sxs-lookup"><span data-stu-id="0224a-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0224a-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0224a-108">Return Value</span></span>  
 <span data-ttu-id="0224a-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0224a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0224a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0224a-110">Requirements</span></span>  
 <span data-ttu-id="0224a-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0224a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0224a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="0224a-112">See also</span></span>

- [<span data-ttu-id="0224a-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="0224a-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="0224a-114">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="0224a-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
