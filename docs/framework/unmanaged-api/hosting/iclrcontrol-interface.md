---
title: Interface ICLRControl
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728323"
---
# <a name="iclrcontrol-interface"></a>Interface ICLRControl

Fornece métodos que permitem que um host obtenha referências e configure aspectos do, o Common Language Runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|DESCRIÇÃO|  
|------------|-----------------|  
|[Método GetCLRManager](iclrcontrol-getclrmanager-method.md)|Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o CLR.|  
|[Método SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)|Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md)
- [Interface ICLRDebugManager](iclrdebugmanager-interface.md)
- [Interface ICLRGCManager](iclrgcmanager-interface.md)
- [Interface ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md)
- [Interface ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)
- [Interface ICLROnEventManager](iclroneventmanager-interface.md)
- [Interface ICLRPolicyManager](iclrpolicymanager-interface.md)
- [Interface IHostControl](ihostcontrol-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
