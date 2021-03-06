---
title: Método ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 2acf8fb507ab617e066a31c9c2657b1ef0d18e47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693275"
---
# <a name="icorpublishprocessenumappdomains-method"></a>Método ICorPublishProcess::EnumAppDomains

Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `ppEnum`  
 fora Um ponteiro para o endereço de uma instância de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) que permite a iteração por meio da coleção de domínios de aplicativo nesse processo.  
  
## <a name="remarks"></a>Comentários  

 A lista de domínios de aplicativo é baseada em um instantâneo dos domínios de aplicativo que existem quando o `EnumAppDomains` método é chamado. Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada. As listas existentes não serão afetadas pelas chamadas subsequentes desse método.  
  
 Se o processo tiver sido encerrado, o `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorPublishProcess](icorpublishprocess-interface.md)
