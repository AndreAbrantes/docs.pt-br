---
title: Comparação entre propriedades e indexadores – Guia de Programação em C#
description: Compare como os indexadores em C# são como propriedades. Exceto para algumas diferenças, as regras definidas para acessadores de propriedade se aplicam aos acessadores do indexador.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192523"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Comparação entre propriedades e indexadores (Guia de Programação em C#)

Os indexadores são como propriedades. Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.  
  
|Propriedade|Indexador|  
|--------------|-------------|  
|Permite que os métodos sejam chamados como se fossem membros de dados públicos.|Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.|  
|Acessado por meio de um nome simples.|Acessado por meio de um índice.|  
|Pode ser estático ou um membro de instância.|Deve ser um membro da instância.|  
|Um acessador [get](../../language-reference/keywords/get.md) de uma propriedade não tem parâmetros.|Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.|  
|Um acessador [set](../../language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.|Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../language-reference/keywords/value.md).|  
|Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../classes-and-structs/auto-implemented-properties.md).|Dá suporte a membros aptos para expressão a fim de obter somente indexadores.|  
  
## <a name="see-also"></a>Veja também

- [Guia de programação C#](../index.md)
- [Indexadores](./index.md)
- [Propriedades](../classes-and-structs/properties.md)
