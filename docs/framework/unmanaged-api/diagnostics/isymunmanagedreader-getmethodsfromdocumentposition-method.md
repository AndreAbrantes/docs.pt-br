---
title: "Método ISymUnmanagedReader::GetMethodsFromDocumentPosition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdf3762c40e5ec4da84a27ed7abcb15981b81379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>Método ISymUnmanagedReader::GetMethodsFromDocumentPosition
Retorna uma matriz de métodos, cada qual contendo o ponto de interrupção na posição fornecida em um documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `document`  
 [in] O documento especificado.  
  
 `line`  
 [in] A linha do documento especificado.  
  
 `column`  
 [in] A coluna do documento especificado.  
  
 `cMethod`  
 [in] O tamanho do `pRetVal` matriz.  
  
 `pcMethod`  
 [out] Um ponteiro para uma variável que recebe o número de elementos retornados no `pRetVal` matriz.  
  
 `pRetVal`  
 [out] Uma matriz de ponteiros, cada qual apontando para um [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objeto que representa um método que contém o ponto de interrupção.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
