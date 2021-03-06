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
ms.openlocfilehash: 3e946d8a27ec6b568b2f3c3633695c9f6795c938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712047"
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
 no O tamanho, em caracteres, do `szHostName` buffer. Se esse parâmetro for 0 (zero), `szHostName` deverá ser NULL.  
  
 `pcchHostName`  
 fora O número de caracteres, incluindo um terminador nulo, no nome do host ou endereço IP. Este parâmetro pode ser nulo.  
  
 `szHostName`  
 fora Buffer que contém o nome do host ou o endereço IP.  
  
## <a name="return-value"></a>Valor Retornado  

 S_OK  
 O nome do host ou o endereço IP foi retornado com êxito.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Não é possível retornar o nome do host ou o endereço IP.  
  
## <a name="remarks"></a>Comentários  

 Esse método é implementado pelo gravador do depurador. Ele deve seguir o paradigma de chamada múltipla: na primeira chamada, o chamador passa NULL para `cchHostName` e e `szHostName` `pcchHostName` retorna o tamanho do buffer necessário. Na segunda chamada, o tamanho retornado anteriormente é passado `cchHostName` e um buffer de tamanho apropriado é passado `szHostName` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
- [Interface ICorDebug](icordebug-interface.md)
