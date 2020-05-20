---
title: Método ISymUnmanagedDocument::GetSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615599"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>Método ISymUnmanagedDocument::GetSourceRange
Retorna o intervalo especificado da fonte inserida para o buffer fornecido. O buffer deve ser grande o suficiente para manter a origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startLine`  
 no A linha inicial no documento atual.  
  
 `startColumn`  
 no A coluna inicial no documento atual.  
  
 `endLine`  
 no A linha final do documento atual.  
  
 `endColumn`  
 no A coluna final no documento atual.  
  
 `cSourceBytes`  
 no O tamanho da origem, em bytes.  
  
 `pcSourceBytes`  
 fora Um ponteiro para uma variável que recebe o tamanho da origem.  
  
 `source`  
 fora O tamanho e o comprimento do intervalo especificado do documento de origem, em bytes.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso.  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedDocument](isymunmanageddocument-interface.md)
