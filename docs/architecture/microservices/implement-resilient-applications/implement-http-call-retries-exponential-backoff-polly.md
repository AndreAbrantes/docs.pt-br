---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Saiba como tratar falhas de HTTP com a Polly e o HttpClientFactory.
ms.date: 01/30/2020
ms.openlocfilehash: 60943360c9674f93b246b37b2667b48dab659e0e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502663"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementar repetições de chamadas HTTP com retirada exponencial com o HttpClientFactory e políticas da Polly

A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.

A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias. Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback. Polly targets .NET Framework 4. x e .NET Standard 1,0, 1,1 e 2,0 (que dá suporte ao .NET Core).

No entanto, escrever seu próprio código personalizado para usar a biblioteca do Polly com HttpClient pode ser significativamente complexo. Na versão original do eShopOnContainers, havia um [bloco de construção ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) com base na Polly. Mas, com o lançamento do [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), a implementação da comunicação http resiliente com o Polly tornou-se muito mais simples, de modo que o bloco de construção foi preterido do eShopOnContainers.

As etapas a seguir mostram como você pode usar repetições de HTTP com a Polly integrada ao HttpClientFactory, que foi explicado na seção anterior.

**Referenciar os pacotes ASP.NET Core 3,1**

o `HttpClientFactory` está disponível desde o .NET Core 2,1, mas recomendamos que você use os pacotes mais recentes do ASP.NET Core 3,1 do NuGet em seu projeto. Normalmente, você também precisa fazer referência ao pacote de extensão `Microsoft.Extensions.Http.Polly`.

**Configurar um cliente com a política de repetição da Polly, na inicialização**

Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

O método **AddPolicyHandler()** é aquele que adiciona políticas aos objetos `HttpClient` que você usará. Nesse caso, ele está adicionando a política da Polly para repetições de HTTP com retirada exponencial.

Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado no arquivo `Startup.cs`, como mostra o código a seguir:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Com a Polly, você pode definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando houver uma exceção de HTTP, como registrar o erro em log. Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Adicionar uma estratégia de tremulação à política de repetição

Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção. Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas. Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial. Isso espalha os picos quando surgem problemas. O princípio é ilustrado pelo exemplo a seguir:

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

O Polly fornece algoritmos de tremulação prontos para produção por meio do site do projeto.

## <a name="additional-resources"></a>Recursos adicionais

- **Padrão de repetição**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly e HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**  
  <https://github.com/App-vNext/Polly>

- **Polly: repetir com tremulação**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker. Tremulação: tornando as coisas melhores com aleatoriedade**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-circuit-breaker-pattern.md)
