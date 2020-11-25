---
title: Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: eba9caece91e369cd46aed652b559ace49c77725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704897"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>Método ICLRAppDomainResourceMonitor::GetCurrentSurvived

Obtém o número de bytes que sobreviveram o último total, bloqueando a coleta de lixo e que são referenciados pelo domínio do aplicativo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `dwAppDomainId`  
 no A ID do domínio do aplicativo solicitado.  
  
 `pAppDomainBytesSurvived`  
 fora Um ponteiro para o número de bytes que sobreviveram após a última coleta de lixo que é mantida por esse domínio de aplicativo. Após uma coleção completa, esse número é preciso e completo. Após uma coleção efêmera, esse número é potencialmente incompleto. Esse parâmetro pode ser `null`.  
  
 `pRuntimeBytesSurvived`  
 fora Um ponteiro para o número total de bytes que sobreviveram da última coleta de lixo. Após uma coleção completa, esse número representa o número de bytes que são mantidos em heaps gerenciados. Após uma coleção efêmera, esse número representa o número de bytes que são mantidos ao vivo em gerações efêmeras. Esse parâmetro pode ser `null`.  
  
## <a name="return-value"></a>Valor Retornado  

 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|COR_E_APPDOMAINUNLOADED|O domínio do aplicativo foi descarregado ou não existe.|  
  
## <a name="remarks"></a>Comentários  

 As estatísticas são atualizadas somente após um total, bloqueando a coleta de lixo; ou seja, uma coleção que inclui todas as gerações e que interrompe o aplicativo enquanto a coleta ocorre. Por exemplo, a <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método executa uma coleção de bloqueio completa. A coleta de lixo simultânea ocorre em segundo plano e não bloqueia o aplicativo.  
  
 O `GetCurrentSurvived` método é o equivalente não gerenciado da propriedade gerenciada <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRAppDomainResourceMonitor](iclrappdomainresourcemonitor-interface.md)
- [Monitoramento de recursos de domínio do aplicativo](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
- [Hosting](index.md)
