---
title: Método ISymUnmanagedBinder2::GetReaderForFile2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: e0fc6cf2a08de4a00cb8b7f98d3922df98f427c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706964"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="ca585-102">Método ISymUnmanagedBinder2::GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="ca585-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>

<span data-ttu-id="ca585-103">Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="ca585-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="ca585-104">Esse método fornece uma pesquisa mais abrangente para o arquivo de banco de dados do programa (PDB) do que o método [ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ca585-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca585-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca585-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca585-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca585-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="ca585-107">no Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="ca585-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ca585-108">no Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ca585-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ca585-109">no Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ca585-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="ca585-110">no Um valor da enumeração [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) que especifica a política a ser usada ao fazer uma pesquisa por um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="ca585-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ca585-111">fora Um ponteiro que é definido para a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="ca585-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca585-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="ca585-112">Return Value</span></span>  

 <span data-ttu-id="ca585-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ca585-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca585-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca585-114">Requirements</span></span>  

 <span data-ttu-id="ca585-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ca585-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca585-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca585-116">Remarks</span></span>  

 <span data-ttu-id="ca585-117">Esta versão do método pode pesquisar o arquivo PDB em áreas diferentes da direita ao lado do módulo.</span><span class="sxs-lookup"><span data-stu-id="ca585-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="ca585-118">A política de pesquisa pode ser controlada pela combinação de [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ca585-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="ca585-119">Por exemplo, `AllowReferencePathAccess | AllowSymbolServerAccess` procura o PDB ao lado do arquivo executável e em um servidor de símbolos, mas não consulta o registro nem usa o caminho no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="ca585-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="ca585-120">Se o `searchPath` parâmetro for fornecido, esses diretórios sempre serão pesquisados.</span><span class="sxs-lookup"><span data-stu-id="ca585-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca585-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca585-121">See also</span></span>

- [<span data-ttu-id="ca585-122">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="ca585-122">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="ca585-123">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="ca585-123">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
