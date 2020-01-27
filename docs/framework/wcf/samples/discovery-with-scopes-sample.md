---
title: Exemplos de descoberta com escopos
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 8ba5618f472fc8a6e1751776060f99103a67a073
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728757"
---
# <a name="discovery-with-scopes-sample"></a>Exemplos de descoberta com escopos

Este exemplo mostra como usar escopos para categorizar pontos de extremidade detectáveis, bem como usar <xref:System.ServiceModel.Discovery.DiscoveryClient> para executar uma pesquisa assíncrona de pontos de extremidade. No serviço, este exemplo mostra como personalizar a descoberta para cada ponto de extremidade adicionando um comportamento de descoberta de ponto de extremidade e usando-o para adicionar um escopo ao ponto de extremidade, bem como controlar a descoberta do ponto de extremidade. No cliente, o exemplo vai além de como os clientes podem criar um <xref:System.ServiceModel.Discovery.DiscoveryClient> e ajustar parâmetros de pesquisa para incluir escopos adicionando escopos ao <xref:System.ServiceModel.Discovery.FindCriteria>. Este exemplo também mostra como os clientes podem restringir as respostas adicionando um critério de encerramento.

## <a name="service-features"></a>Recursos de serviço

Este projeto mostra dois pontos de extremidade de serviço que estão sendo adicionados a um <xref:System.ServiceModel.ServiceHost>. Cada ponto de extremidade tem um <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> associado a ele. Esse comportamento é usado para adicionar escopos de URI para ambos os pontos de extremidade. Os escopos são usados para distinguir cada um desses pontos de extremidade para que os clientes possam ajustar a pesquisa. Para o segundo ponto de extremidade, a descoberta pode ser desabilitada definindo a propriedade <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> como `false`. Isso garante que os metadados de descoberta associados a esse ponto de extremidade não sejam enviados como parte de todas as mensagens de descoberta.

## <a name="client-features"></a>Recursos do cliente

O método `FindCalculatorServiceAddress()` mostra como usar um <xref:System.ServiceModel.Discovery.DiscoveryClient> e passar um <xref:System.ServiceModel.Discovery.FindCriteria> com duas restrições. Um escopo é adicionado aos critérios e a propriedade <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> é definida como 1. O escopo limita os resultados apenas aos serviços que publicam o mesmo escopo. Definir <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> como 1 limita as respostas às quais o <xref:System.ServiceModel.Discovery.DiscoveryClient> aguarda, no máximo, 1 ponto de extremidade. A chamada <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> é uma operação síncrona que bloqueia o thread até que um tempo limite seja atingido ou um ponto de extremidade seja encontrado.

### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, as ACLs de URL adequadas devem ser adicionadas. Para obter mais informações, consulte [Configurando http e HTTPS](../feature-details/configuring-http-and-https.md). A execução do comando a seguir em um privilégio elevado deve adicionar as ACLs apropriadas. Talvez você queira substituir seu domínio e nome de usuário pelos seguintes argumentos se o comando não funcionar como está: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. {1&gt;Compile a solução.&lt;1}

3. Execute o executável do serviço no diretório de compilação.

4. Execute o executável do cliente. Observe que o cliente é capaz de localizar o serviço.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
