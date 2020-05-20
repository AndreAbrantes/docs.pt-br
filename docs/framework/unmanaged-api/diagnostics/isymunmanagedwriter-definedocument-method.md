---
title: Método ISymUnmanagedWriter::DefineDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615222"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="65c89-102">Método ISymUnmanagedWriter::DefineDocument</span><span class="sxs-lookup"><span data-stu-id="65c89-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="65c89-103">Define um documento de origem.</span><span class="sxs-lookup"><span data-stu-id="65c89-103">Defines a source document.</span></span> <span data-ttu-id="65c89-104">Os GUIDs são fornecidos para idiomas, fornecedores e tipos de documentos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="65c89-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c89-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65c89-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c89-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65c89-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="65c89-107">no Um ponteiro para um `WCHAR` que define o Uniform Resource Locator (URL) que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="65c89-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="65c89-108">no Um ponteiro para um GUID que define o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="65c89-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="65c89-109">no Um ponteiro para um GUID que define a identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="65c89-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="65c89-110">no Um ponteiro para um GUID que define o tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="65c89-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="65c89-111">fora Um ponteiro para a interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="65c89-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65c89-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="65c89-112">Return Value</span></span>  
 <span data-ttu-id="65c89-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="65c89-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c89-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65c89-114">Requirements</span></span>  
 <span data-ttu-id="65c89-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="65c89-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c89-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="65c89-116">See also</span></span>

- [<span data-ttu-id="65c89-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="65c89-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
