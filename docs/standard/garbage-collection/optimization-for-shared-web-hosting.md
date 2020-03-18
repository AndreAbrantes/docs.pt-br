---
title: Otimização da hospedagem Web compartilhada
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140278"
---
# <a name="optimization-for-shared-web-hosting"></a>Otimização da hospedagem Web compartilhada
Se você for o administrador de um servidor que é compartilhado ao hospedar vários sites pequenos, poderá otimizar o desempenho e aumentar a capacidade do site adicionando a seguinte configuração `gcTrimCommitOnLowMemory` ao nó `runtime` no arquivo Aspnet.config no diretório .NET:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Essa configuração é recomendada somente para cenários de hospedagem na Web compartilhada.  
  
 Como o coletor de lixo retém a memória para alocações futuras, seu espaço confirmado pode ser superior a o que é estritamente necessário. Você pode reduzir esse espaço para acomodar quando houver uma carga pesada na memória do sistema. Reduzir esse espaço confirmado melhora o desempenho e expande a capacidade de hospedar mais sites.  
  
 Quando a configuração `gcTrimCommitOnLowMemory` estiver habilitada, o coletor de lixo avaliará a carga de memória do sistema e entrará em um modo de corte, quando a carga atinge 90%. Ele mantém o modo de corte até que a carga fique abaixo de 85%.  
  
 Quando as condições permitirem, o coletor de lixo poderá decidir que a configuração `gcTrimCommitOnLowMemory` não ajudará o aplicativo atual e poderá ignorá-lo.  
  
## <a name="example"></a>Exemplo  
 O fragmento XML a seguir mostra como habilitar a configuração `gcTrimCommitOnLowMemory`. As reticências indicam outras configurações que estariam no nó `runtime`.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
