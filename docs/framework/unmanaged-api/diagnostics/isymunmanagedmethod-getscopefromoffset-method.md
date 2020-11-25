---
title: Método ISymUnmanagedMethod::GetScopeFromOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: cf2784ce0ac6e614e75a341660808b9fe03ada0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699437"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="cea85-102">Método ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="cea85-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="cea85-103">Obtém o escopo léxico mais delimitador dentro desse método que envolve o deslocamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="cea85-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="cea85-104">Isso pode ser usado para iniciar pesquisas de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="cea85-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cea85-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cea85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cea85-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cea85-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="cea85-107">no Um `ULONG` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="cea85-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cea85-108">fora Um ponteiro que é definido para a interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="cea85-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cea85-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="cea85-109">Return Value</span></span>  

 <span data-ttu-id="cea85-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="cea85-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cea85-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cea85-111">Requirements</span></span>  

 <span data-ttu-id="cea85-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cea85-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea85-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cea85-113">See also</span></span>

- [<span data-ttu-id="cea85-114">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="cea85-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
