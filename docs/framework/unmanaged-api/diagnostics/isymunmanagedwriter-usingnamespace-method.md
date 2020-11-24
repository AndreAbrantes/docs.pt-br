---
title: Método ISymUnmanagedWriter::UsingNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: 6404252f2c1eb14f0cd723451beb82b4c65960fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683479"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="32fa4-102">Método ISymUnmanagedWriter::UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="32fa4-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="32fa4-103">Especifica que o nome de namespace totalmente qualificado fornecido está sendo usado dentro do escopo léxico aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="32fa4-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="32fa4-104">O namespace será usado em todos os escopos que herdam do escopo aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="32fa4-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="32fa4-105">Fechar o escopo atual também irá parar o uso do namespace.</span><span class="sxs-lookup"><span data-stu-id="32fa4-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32fa4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32fa4-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32fa4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32fa4-107">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="32fa4-108">no Um ponteiro para o nome totalmente qualificado do namespace.</span><span class="sxs-lookup"><span data-stu-id="32fa4-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32fa4-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="32fa4-109">Return Value</span></span>  

 <span data-ttu-id="32fa4-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="32fa4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32fa4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32fa4-111">Requirements</span></span>  

 <span data-ttu-id="32fa4-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="32fa4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fa4-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="32fa4-113">See also</span></span>

- [<span data-ttu-id="32fa4-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="32fa4-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
