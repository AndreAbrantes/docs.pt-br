---
title: Método ICorDebugProcess::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 66d544bbc0511ea76565376c8f10294f1758026b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792565"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>Método ICorDebugProcess::SetThreadContext
Define o contexto para o thread fornecido nesse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 no A ID do thread para o qual definir o contexto.  
  
 `contextSize`  
 no O tamanho da matriz de `context`.  
  
 `context`  
 no Uma matriz de bytes que descreve o contexto do thread.  
  
 O contexto especifica a arquitetura do processador no qual o thread está sendo executado.  
  
## <a name="remarks"></a>Comentários  
 O depurador deve chamar esse método em vez da função de `SetThreadContext` do Win32, porque o thread pode realmente estar em um estado "seqüestrado", no qual seu contexto foi alterado temporariamente. Esse método deve ser usado somente quando um thread estiver em código nativo. Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) para threads em código gerenciado. Nunca é necessário modificar o contexto de um thread durante um evento de depuração OOB (fora de banda).  
  
 Os dados passados devem ser uma estrutura de contexto para a plataforma atual.  
  
 Esse método pode corromper o tempo de execução se for usado de forma inadequada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
