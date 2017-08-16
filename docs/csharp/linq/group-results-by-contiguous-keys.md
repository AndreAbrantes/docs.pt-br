---
title: "Agrupar resultados por chaves contíguas"
description: "Como agrupar resultados por chaves contíguas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f49b0e0dac7df20fc6e5015b9707208ee65a48d6
ms.lasthandoff: 03/13/2017

---
# <a name="group-results-by-contiguous-keys"></a>Agrupar resultados por chaves contíguas

O exemplo a seguir mostra como agrupar elementos em partes que representam subsequências de chaves contíguas. Por exemplo, suponha que você receba a seguinte sequência de pares chave-valor:  
  
|Chave|Valor|  
|---------|-----------|  
|Um|We|  
|Um|think|  
|Um|that|  
|B|Linq|  
|C|is|  
|Um|really|  
|B|cool|  
|B|!|  
  
 Os seguintes grupos serão criados nesta ordem:  
  
1.  We, think, that  
  
2.  Linq  
  
3.  is  
  
4.  really  
  
5.  cool, !  
  
 A solução é implementada como um método de extensão que é thread-safe e que retorna os resultados de uma maneira de streaming. Em outras palavras, ela produz seus grupos à medida que percorre a sequência de origem. Diferentemente dos operadores `group` ou `orderby`, ela pode começar a retornar grupos para o chamador antes que todas as sequências sejam lidas.  
  
 O acesso thread-safe é alcançado ao fazer uma cópia de cada grupo ou parte enquanto a sequência de origem é iterada, conforme explicado nos comentários do código-fonte. Se a sequência de origem tiver uma sequência grande de itens contíguos, o Common Language Runtime poderá lançar uma <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o método de extensão e o código cliente que o utiliza.  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Para usar o método de extensão em seu projeto, copie a classe estática `MyExtensions` para um arquivo de código-fonte novo ou existente e se for necessário, adicione uma diretiva `using` para o namespace em que ele está localizado.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)   
 
