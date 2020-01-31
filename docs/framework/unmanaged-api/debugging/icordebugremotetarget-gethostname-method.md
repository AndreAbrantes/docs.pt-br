---
title: Método ICorDebugRemoteTarget::GetHostName
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791941"
---
# <a name="icordebugremotetargetgethostname-method"></a>Método ICorDebugRemoteTarget::GetHostName
Retorna o nome de domínio totalmente qualificado ou o endereço IPv4 do computador de destino de depuração remota. Não há suporte para IPV6 no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchHostName`  
 no O tamanho, em caracteres, do buffer de `szHostName`. Se esse parâmetro for 0 (zero), `szHostName` deverá ser NULL.  
  
 `pcchHostName`  
 fora O número de caracteres, incluindo um terminador nulo, no nome do host ou endereço IP. Este parâmetro pode ser nulo.  
  
 `szHostName`  
 fora Buffer que contém o nome do host ou o endereço IP.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O nome do host ou o endereço IP foi retornado com êxito.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Não é possível retornar o nome do host ou o endereço IP.  
  
## <a name="remarks"></a>Comentários  
 Esse método é implementado pelo gravador do depurador. Ele deve seguir o paradigma de chamada múltipla: na primeira chamada, o chamador passa nulo para `cchHostName` e `szHostName`e `pcchHostName` retorna o tamanho do buffer necessário. Na segunda chamada, o tamanho retornado anteriormente é passado em `cchHostName`e um buffer de tamanho apropriado é passado `szHostName`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
- [Interface ICorDebug](icordebug-interface.md)
