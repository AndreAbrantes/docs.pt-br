---
title: Método ICLRRuntimeHost::ExecuteInDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: df0b2d96963ad03e04bd8770d8a8078c6c20b8ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728856"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>Método ICLRRuntimeHost::ExecuteInDefaultAppDomain

Chama o método especificado do tipo especificado no assembly gerenciado especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pwzAssemblyPath`  
 no O caminho para o <xref:System.Reflection.Assembly> que define o <xref:System.Type> cujo método deve ser invocado.  
  
 `pwzTypeName`  
 no O nome do <xref:System.Type> que define o método a ser invocado.  
  
 `pwzMethodName`  
 no O nome do método a ser invocado.  
  
 `pwzArgument`  
 no O parâmetro de cadeia de caracteres a ser passado para o método.  
  
 `pReturnValue`  
 fora O valor inteiro retornado pelo método invocado.  
  
## <a name="return-value"></a>Valor Retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornar E_FAIL, a CRL não poderá mais ser usada no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  

 O método invocado deve ter a seguinte assinatura:  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 onde `pwzMethodName` representa o nome do método invocado e `pwzArgument` representa o valor da cadeia de caracteres passado como um parâmetro para esse método. Se o valor HRESULT for definido como S_OK, `pReturnValue` será definido como o valor inteiro retornado pelo método invocado. Caso contrário, `pReturnValue` não será definido.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRRuntimeHost](iclrruntimehost-interface.md)
