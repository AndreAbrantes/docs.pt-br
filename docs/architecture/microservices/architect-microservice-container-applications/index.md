---
title: Como arquitetar aplicativos baseados em contêineres e em microsserviços
description: Arquitetar aplicativos baseados em contêineres e em microsserviços não é simples e deve ser levado a sério. Aprenda os conceitos principais neste capítulo.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295514"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Como arquitetar aplicativos baseados em contêineres e em microsserviços

*Os microserviços oferecem grandes benefícios, mas também levantam enormes novos desafios. Padrões de arquitetura de microserviços são pilares fundamentais ao criar um aplicativo baseado em microserviços.*

Antes neste guia, você aprendeu os conceitos básicos sobre contêineres e sobre o Docker. Esse é o mínimo de informações necessárias para a introdução aos contêineres. Embora os contêineres habilitem os microsserviços e sejam muito adequados para isso, eles não são obrigatórios para uma arquitetura de microsserviço e muitos conceitos de arquitetura nesta seção de arquitetura também podem ser aplicados sem contêineres. No entanto, este guia concentra-se na interseção de ambos devido a importância dos contêineres que já foi apresentada.

Os aplicativos corporativos podem ser complexos e geralmente são compostos de vários serviços e não em um único serviço. Para esses casos, você precisa entender as abordagens de arquitetura adicionais, como os microsserviços e certos padrões de DDD (design controlado por domínio) além de conceitos de orquestração de contêiner. Observe que este capítulo não descreve apenas microsserviços em contêineres, mas também qualquer aplicativo em contêiner.

## <a name="container-design-principles"></a>Princípios de design de contêiner

No modelo de contêiner, uma instância de imagem de contêiner representa um único processo. Definindo uma imagem de contêiner como um limite de processo, você pode criar primitivas que podem ser usadas para dimensionar o processo ou criar um lote.

Ao criar uma imagem de contêiner, você verá uma definição [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) no Dockerfile. Ela define o processo cujo tempo de vida controla o tempo de vida do contêiner. Quando o processo for concluído, o ciclo de vida do contêiner será encerrado. Os contêineres podem representar processos de longa execução como servidores Web, mas também podem representar processos de curta duração, como trabalhos em lotes, que anteriormente talvez eram implementados como Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Se o processo falhar, o contêiner é encerrado e o orquestrador assume. Se o orquestrador foi configurado para manter cinco instâncias em execução e uma falhar, ele criará outra instância de contêiner para substituir o processo com falha. Em um trabalho em lotes, o processo é iniciado com parâmetros. Quando o processo é concluído, o trabalho é concluído. Mais tarde, este guia faz drill-down em orquestradores.

Você pode encontrar um cenário em que deseje vários processos em execução em um único contêiner. Para esse cenário, como pode haver apenas um ponto de entrada por contêiner, você poderá executar um script dentro do contêiner para iniciar quantos programas forem necessários. Por exemplo, você pode usar o [Supervisor](http://supervisord.org/) ou uma ferramenta semelhante para cuidar da inicialização de vários processos dentro de um único contêiner. No entanto, mesmo que seja possível encontrar arquiteturas com vários processos por contêiner, essa abordagem não é muito comum.

>[!div class="step-by-step"]
>[Próximo](../net-core-net-framework-containers/official-net-docker-images.md)
>[anterior](containerize-monolithic-applications.md)
