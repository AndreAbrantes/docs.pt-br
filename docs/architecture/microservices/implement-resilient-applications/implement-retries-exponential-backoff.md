---
title: Implementar repetição com retirada exponencial
description: Saiba como implementar repetições com retirada exponencial.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674533"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementar repetição com retirada exponencial

[*Repetições com retirada exponencial*](/azure/architecture/patterns/retry) é uma técnica que repete uma operação, com um tempo de espera aumentando exponencialmente, até que uma contagem máxima de repetições seja atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)). Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo. Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga. Durante esse tempo, algumas solicitações podem falhar. Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.

Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.

>[!div class="step-by-step"]
>[Próximo](partial-failure-strategies.md)
>[anterior](implement-resilient-entity-framework-core-sql-connections.md)
