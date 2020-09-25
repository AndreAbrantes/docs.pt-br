---
title: Números de ponto flutuante
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 754338ce842fdfccb8c3874e63a75a3aa2fe3eb3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169551"
---
# <a name="floating-point-numbers"></a>Números de ponto flutuante

Este tópico descreve alguns dos problemas que os desenvolvedores costumam encontrar quando trabalham com números de ponto flutuante no ADO.NET. Esses problemas são causados pela maneira como os computadores armazenam números de ponto flutuante e não são específicos de um provedor específico, como <xref:System.Data.SqlClient> ou <xref:System.Data.OracleClient> .  
  
 Números de ponto flutuante geralmente não têm uma representação binária exata. Em vez disso, o computador armazena uma aproximação do número. Em momentos diferentes, números diferentes de dígitos binários podem ser usados para representar o número. Quando um número de ponto flutuante é convertido de uma representação para outra representação, os dígitos menos significativos desse número podem variar um pouco. A conversão normalmente ocorre quando o número é convertido de um tipo para outro tipo. A variação ocorre se a conversão ocorre em um banco de dados, entre tipos que representam valores de banco de dados ou entre tipos. Devido a essas alterações, os números que logicamente seriam iguais podem ter alterações em seus dígitos menos significativos que fazem com que eles tenham valores diferentes. O número de dígitos de precisão no número pode ser maior ou menor do que o esperado. Quando formatado como uma cadeia de caracteres, o número pode não mostrar o valor esperado.  
  
 Para minimizar esses efeitos, você deve usar a correspondência mais próxima entre os tipos numéricos disponíveis para você. Por exemplo, se você estiver trabalhando com SQL Server, o valor numérico exato poderá ser alterado se você converter um valor de Transact-SQL de tipo real para um valor de tipo float. No .NET Framework, converter um <xref:System.Single> para a <xref:System.Double> também pode produzir resultados inesperados. Em ambos os casos, uma boa estratégia é fazer com que todos os valores no aplicativo usem o mesmo tipo numérico. Você também pode usar um tipo decimal de precisão fixa ou converter números de ponto flutuante para um tipo decimal de precisão fixa antes de trabalhar com eles.  
  
 Para solucionar problemas com a comparação de igualdade, considere codificar seu aplicativo para que as variações nos dígitos menos significativos sejam ignoradas. Por exemplo, em vez de comparar para ver se dois números são iguais, subtraia um número do outro número. Se a diferença estiver dentro de uma margem aceitável de arredondamento, seu aplicativo poderá tratar os números como se eles fossem os mesmos.  
  
## <a name="see-also"></a>Confira também

- [Por que os números de ponto flutuante podem perder a precisão](/cpp/build/why-floating-point-numbers-may-lose-precision)
- [Visão geral do ADO.NET](ado-net-overview.md)
