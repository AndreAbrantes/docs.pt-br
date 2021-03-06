---
title: Estrutura SYMLINEDELTA
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690935"
---
# <a name="symlinedelta-structure"></a>Estrutura SYMLINEDELTA

Fornece informações para o manipulador de símbolos sobre métodos que foram movidos como resultado de edições.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|DESCRIÇÃO|  
|------------|-----------------|  
|`mdMethod`|O token de metadados do método.|  
|`delta`|O número de linhas que o método foi movido.|  
  
## <a name="requirements"></a>Requisitos  

 **Cabeçalho:** CorSym. idl  
  
## <a name="see-also"></a>Confira também

- [Estruturas de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-structures.md)
