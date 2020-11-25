---
title: Método ICLRProbingAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 9a6145ff2874890f052f18a7e537e20ff259933c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728934"
---
# <a name="iclrprobingassemblyenumget-method"></a>Método ICLRProbingAssemblyEnum::Get

Obtém a identidade do assembly no índice especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `dwIndex`  
 no O índice de base zero da identidade do assembly a ser retornado.  
  
 `pwzBuffer`  
 fora Um buffer que contém os dados de identidade do assembly.  
  
 `pcchBufferSize`  
 [entrada, saída] O tamanho do `pwzBuffer` buffer.  
  
## <a name="return-value"></a>Valor Retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Get` retornado com êxito.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` é pequeno demais.|  
|ERROR_NO_MORE_ITEMS|A enumeração não contém mais itens.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo. As chamadas subsequentes para quaisquer métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  

 A identidade no índice 0 é a identidade específica para a arquitetura do processador. A identidade no índice 1 é o assembly de arquitetura neutra para MSIL (Microsoft Intermediate Language). A identidade no índice 2 não contém informações de arquitetura.  
  
 `Get` normalmente é chamado duas vezes. A primeira chamada fornece um valor nulo para `pwzBuffer` e define `pcchBufferSize` o tamanho apropriado para `pwzBuffer` . A segunda chamada fornece um tamanho adequado `pwzBuffer` e contém os dados de identidade do assembly canônico após a conclusão.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md)
- [Interface ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md)
