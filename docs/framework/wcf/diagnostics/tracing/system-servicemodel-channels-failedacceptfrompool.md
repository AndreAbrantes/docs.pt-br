---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 8615cca7d4ed8ea1f40baa9502e7136d4349eb9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256307"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a>System.ServiceModel.Channels.FailedAcceptFromPool

Falha ao tentar reutilizar uma conexão em pool. Outra tentativa é feita dentro do período de tempo limite especificado.  
  
## <a name="description"></a>Descrição  

 Esse rastreamento informativo indica que ocorreu um erro ao tentar reutilizar uma conexão em pool. Isso pode acontecer porque a conexão em pool não era compatível, pronta ou ainda está ativa. As tentativas adicionais de reutilização de outra conexão em pool são feitas dentro de um determinado tempo limite e uma nova conexão é criada caso não sejam encontradas conexões utilizáveis.  
  
## <a name="see-also"></a>Veja também

- [Rastreamento](index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnóstico](../index.md)
