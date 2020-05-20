---
title: Método ISymUnmanagedWriter::GetDebugInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614780"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>Método ISymUnmanagedWriter::GetDebugInfo
Retorna as informações necessárias para um compilador gravar a entrada do diretório de depuração no cabeçalho do arquivo PE (executável portátil). O gravador de símbolos preenche todos os campos, exceto para `TimeDateStamp` e `PointerToRawData` . (O compilador é responsável por definir esses dois campos adequadamente.)  
  
 Um compilador deve chamar esse método, emitir o blob de dados para o arquivo PE, definir o `PointerToRawData` campo no IMAGE_DEBUG_DIRECTORY para apontar para os dados emitidos e gravar o IMAGE_DEBUG_DIRECTORY no arquivo PE. O compilador também deve definir o `TimeDateStamp` campo para igual ao `TimeDateStamp` do arquivo PE que está sendo gerado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIDD`  
 [entrada, saída] Um ponteiro para um IMAGE_DEBUG_DIRECTORY que o gravador de símbolo preencherá.  
  
 `cData`  
 no Um `DWORD` que contém o tamanho dos dados de depuração.  
  
 `pcData`  
 fora Um ponteiro para um `DWORD` que recebe o tamanho do buffer necessário para conter os dados de depuração.  
  
 `data`  
 fora Um ponteiro para um buffer que é grande o suficiente para manter os dados de depuração para o armazenamento de símbolo.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
