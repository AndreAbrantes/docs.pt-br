---
title: Método ISymUnmanagedVariable::GetAttributes
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 1142dbb83693f6104ba6e22e174ce02fb92997a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726893"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="1f89b-102">Método ISymUnmanagedVariable::GetAttributes</span><span class="sxs-lookup"><span data-stu-id="1f89b-102">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="1f89b-103">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="1f89b-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f89b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f89b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f89b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f89b-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1f89b-106">fora Um ponteiro para um `ULONG32` que recebe os atributos.</span><span class="sxs-lookup"><span data-stu-id="1f89b-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="1f89b-107">O valor retornado será um dos valores definidos na enumeração [CorSymVarFlag](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1f89b-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f89b-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="1f89b-108">Return Value</span></span>  

 <span data-ttu-id="1f89b-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1f89b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f89b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f89b-110">Requirements</span></span>  

 <span data-ttu-id="1f89b-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1f89b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f89b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f89b-112">See also</span></span>

- [<span data-ttu-id="1f89b-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="1f89b-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
