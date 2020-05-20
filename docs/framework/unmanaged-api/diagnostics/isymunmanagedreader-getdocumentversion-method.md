---
title: Método ISymUnmanagedReader::GetDocumentVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615027"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="24fc3-102">Método ISymUnmanagedReader::GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="24fc3-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="24fc3-103">Obtém a versão especificada do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="24fc3-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="24fc3-104">A versão do documento começa em 1 e é incrementada toda vez que o documento é atualizado usando o método [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24fc3-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="24fc3-105">Se o `pbCurrent` parâmetro for `true` , esta é a versão mais recente do documento.</span><span class="sxs-lookup"><span data-stu-id="24fc3-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fc3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24fc3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24fc3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24fc3-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="24fc3-108">no O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="24fc3-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="24fc3-109">fora Um ponteiro para uma variável que recebe a versão do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="24fc3-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="24fc3-110">fora Um ponteiro para uma variável que recebe `true` se esta é a versão mais recente do documento ou `false` se não é a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="24fc3-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24fc3-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="24fc3-111">Return Value</span></span>  
 <span data-ttu-id="24fc3-112">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="24fc3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24fc3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24fc3-113">Requirements</span></span>  
 <span data-ttu-id="24fc3-114">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="24fc3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fc3-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="24fc3-115">See also</span></span>

- [<span data-ttu-id="24fc3-116">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="24fc3-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
