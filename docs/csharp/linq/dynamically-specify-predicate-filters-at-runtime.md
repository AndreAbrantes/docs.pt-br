---
title: "Especificar filtros predicados dinamicamente em tempo de execução"
description: "Como especificar filtros predicados dinamicamente em tempo de execução."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8b9ad2603a9c57855f9a8ebd7ff3f5261aa44157
ms.lasthandoff: 03/13/2017

---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Especificar filtros predicados dinamicamente em tempo de execução

Em alguns casos você não sabe até o tempo de execução quantos predicados você precisa aplicar aos elementos de origem na cláusula `where`. Uma maneira de especificar dinamicamente vários filtros de predicados é usar o método <xref:System.Linq.Enumerable.Contains%2A>, como mostrado no exemplo a seguir. O exemplo é construído de duas maneiras. Primeiro, o projeto é executado filtrando valores que são fornecidos no programa. Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.  
  
## <a name="to-filter-by-using-the-contains-method"></a>Para filtrar usando o método Contains  
  
1.  Abra um novo aplicativo de console e nomeie-o como `PredicateFilters`.  
  
2.  Copie a classe `StudentClass` de [Consultar uma coleção de objetos](query-a-collection-of-objects.md) e cole-a no namespace `PredicateFilters` sob a classe `Program`. `StudentClass` fornece uma lista de objetos `Student`.  
  
3.  Comente o método `Main` em `StudentClass`.  
  
4.  Substitua a classe `Program` pelo código a seguir.  
  
     [!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Adicione a seguinte linha ao método `Main` na classe `DynamicPredicates`, sob a declaração de `ids`.  
  
     ```csharp
     QueryById(ids);
     ```

6.  Execute o projeto.  
  
7.  A saída a seguir é exibida em uma janela do console:  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserida em tempo de execução em vez da matriz `ids`. Altere `QueryByID(ids)` para `QueryByID(args)` no método `Main`.  
  
9. Execute o projeto com os argumentos de linha de comando `122 117 120 115`. Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro do método `Main`...  
  
10. A saída a seguir é exibida em uma janela do console:  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
## <a name="to-filter-by-using-a-switch-statement"></a>Para filtrar usando uma instrução switch  
  
1.  Você pode usar uma instrução `switch` para selecionar entre consultas alternativas predeterminadas. No exemplo a seguir, `studentQuery` usa uma cláusula `where` diferente dependendo de qual nível de ensino ou ano, é especificado em tempo de execução.  
  
2.  Copie o método a seguir e cole-o na classe `DynamicPredicates`.  
  
     [!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  No método `Main`, substitua a chamada para `QueryByID` pela chamada a seguir, que envia o primeiro elemento da matriz `args` como seu argumento: `QueryByYear(args[0])`.  
  
4.  Execute o projeto com um argumento de linha de comando de um valor inteiro entre 1 e 4.  
  
 
## <a name="see-also"></a>Consulte também  
 [Expressões de Consulta LINQ](index.md)   
 [Cláusula where](../language-reference/keywords/where-clause.md)
