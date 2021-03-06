---
title: Coclass CorpubPublish
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722343"
---
# <a name="corpubpublish-coclass"></a>Coclass CorpubPublish

Fornece interfaces para publicar informações sobre processos e domínios de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[Interface ICorPublish](icorpublish-interface.md)|Fornece métodos para publicar informações sobre processos e os domínios de aplicativo nesses processos.|  
|[Interface ICorPublishAppDomain](icorpublishappdomain-interface.md)|Representa e fornece informações sobre o, um domínio de aplicativo em um processo.|  
|[Interface ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)|Fornece métodos que atravessam uma coleção de domínios de aplicativo que existem atualmente dentro de um processo.|  
|[Interface ICorPublishProcess](icorpublishprocess-interface.md)|Representa um processo que está sendo executado em um computador.|  
|[Interface ICorPublishProcessEnum](icorpublishprocessenum-interface.md)|Fornece métodos que atravessam uma coleção de processos que estão em execução em um computador.|  
  
## <a name="remarks"></a>Comentários  

 Um cenário de publicação típico envolve um desenvolvedor que deseja depurar o código gerenciado que está sendo executado em um computador dentro de um domínio de aplicativo. O ambiente de hospedagem pode estar executando mais de um domínio de aplicativo dentro de um processo. O desenvolvedor gostaria de usar uma interface gráfica do usuário ou algum outro meio de listar todos os processos em execução no computador e escolher um processo específico. A listagem deve incluir todos os domínios de aplicativo em processos que estejam executando código gerenciado. O desenvolvedor pode então identificar o domínio do aplicativo específico e anexar um depurador a esse domínio.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depuração](index.md)
