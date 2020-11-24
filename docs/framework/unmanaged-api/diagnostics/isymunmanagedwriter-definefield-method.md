---
title: Método ISymUnmanagedWriter::DefineField
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 5683c10938873821cbe998dbf13937a6a7d24d7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675081"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>Método ISymUnmanagedWriter::DefineField

Define uma única variável que não está dentro de um método. Esse método é usado para determinados campos em classes, campos de bits e assim por diante.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `parent`  
 no O tipo de metadados ou o token do método.  
  
 `name`  
 no O nome do campo.  
  
 `attributes`  
 no Os atributos do campo.  
  
 `cSig`  
 no Um `ULONG32` que é o tamanho, em caracteres, do buffer necessário para conter a assinatura de campo.  
  
 `signature`  
 no A matriz de assinaturas de campo.  
  
 `addrKind`  
 no O tipo de endereço.  
  
 `addr1`  
 no O primeiro endereço para a especificação de campo.  
  
 `addr2`  
 no O segundo endereço para a especificação de campo.  
  
 `addr3`  
 no O terceiro endereço para a especificação de campo.  
  
## <a name="return-value"></a>Valor Retornado  

 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  

 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
