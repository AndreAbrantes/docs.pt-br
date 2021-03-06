---
title: Interface IHostPolicyManager
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 3c85bcbe8aee453b19217ebd1f48feea113e3bb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731210"
---
# <a name="ihostpolicymanager-interface"></a>Interface IHostPolicyManager

Fornece métodos que notificam o host das ações que o Common Language Runtime (CLR) executa em caso de anulações, tempos limite ou falhas.  
  
## <a name="methods"></a>Métodos  
  
|Método|DESCRIÇÃO|  
|------------|-----------------|  
|[Método OnDefaultAction](ihostpolicymanager-ondefaultaction-method.md)|Notifica o host de que o CLR está prestes a tomar a ação padrão especificada por uma chamada para [ICLRPolicyManager:: Setpadrãoaction](iclrpolicymanager-setdefaultaction-method.md) em resposta a um descarregamento ou anulação de thread <xref:System.AppDomain> .|  
|[Método OnFailure](ihostpolicymanager-onfailure-method.md)|Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) em resposta a uma alocação de recurso ou falha de recuperação.|  
|[Método OnTimeout](ihostpolicymanager-ontimeout-method.md)|Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Enumeração EClrFailure](eclrfailure-enumeration.md)
- [Enumeração EClrOperation](eclroperation-enumeration.md)
- [Enumeração EPolicyAction](epolicyaction-enumeration.md)
- [Interface ICLRPolicyManager](iclrpolicymanager-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
