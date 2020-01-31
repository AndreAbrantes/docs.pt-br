---
title: Método ICLRDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: b5f6a830cbe601443f03cd91a356c7e49450e7f3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793725"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>Método ICLRDataTarget::GetThreadContext
Obtém o contexto de execução atual para o thread determinado no processo de destino. Esse método é chamado pelo Common Language Runtime Data Access Services.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 no O identificador do sistema operacional de um thread no processo de destino.  
  
 `contextFlags`  
 no Sinalizadores que especificam quais partes do contexto retornar. A implementação retornará pelo menos essas partes do contexto.  
  
 `contextSize`  
 no O tamanho do contexto.  
  
 `context`  
 fora Ponteiro para um buffer no qual o contexto será colocado.  
  
 Os dados no buffer de `context` devem estar no formato da estrutura de `CONTEXT` do Win32. O contexto especifica dados de registro específicos do processador, portanto, a definição da estrutura de `CONTEXT` do Win32 depende da arquitetura do processador. Consulte o arquivo de cabeçalho WinNT. h para obter a definição da estrutura de `CONTEXT` do Win32.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
