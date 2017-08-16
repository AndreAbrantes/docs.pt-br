---
title: "Sintaxe de consulta e sintaxe de método em LINQ (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 687741ed357fd13424c4e2f9eeda3d2b531fd129
ms.lasthandoff: 03/13/2017

---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Sintaxe de consulta e sintaxe de método em LINQ (C#)
A maioria das consultas na documentação introdutória da [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] (Consulta Integrada à Linguagem) é escrita usando a sintaxe de consulta declarativa da LINQ. No entanto, a sintaxe de consulta deve ser convertida em chamadas de método para o CLR (Common Language Runtime) do .NET quando o código for compilado. Essas chamadas de método invocam os operadores de consulta padrão, que têm nomes como `Where`, `Select`, `GroupBy`, `Join`, `Max` e `Average`. Você pode chamá-los diretamente usando a sintaxe de método em vez da sintaxe de consulta.  
  
 A sintaxe de consulta e a sintaxe de método são semanticamente idênticas, mas muitas pessoas acham a sintaxe de consulta mais simples e fácil de ler. Algumas consultas devem ser expressadas como chamadas de método. Por exemplo, você deve usar uma chamada de método para expressar uma consulta que recupera o número de elementos que correspondem a uma condição especificada. Você também deve usar uma chamada de método para uma consulta que recupera o elemento que tem o valor máximo em uma sequência de origem. A documentação de referência para os operadores de consulta padrão no namespace <xref:System.Linq> geralmente usa a sintaxe de método. Portanto, mesmo quando começar a escrever consultas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], é útil estar familiarizado com como usar a sintaxe de método nas consultas e nas próprias expressões de consulta.  
  
## <a name="standard-query-operator-extension-methods"></a>Métodos de Extensão do Operador de Consulta Padrão  
 O exemplo a seguir mostra uma *expressão de consulta* simples e a consulta semanticamente equivalente escrita como uma *consulta baseada em método*.  
  
 [!code-cs[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 A saída dos dois exemplos é idêntica. Você pode ver que o tipo da variável de consulta é o mesmo em ambas as formas: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Para entender a consulta baseada em método, vamos examiná-la melhor. No lado direito da expressão, observe que a cláusula `where` agora é expressa como um método de instância no objeto `numbers`, que, como você deve se lembrar, tem um tipo de `IEnumerable<int>`. Se você estiver familiarizado com a interface <xref:System.Collections.Generic.IEnumerable%601> genérica, sabe que ele não tem um método `Where`. No entanto, se você invocar a lista de conclusão do IntelliSense no IDE do Visual Studio, verá não apenas um método `Where`, mas muitos outros métodos como `Select`, `SelectMany`, `Join` e `Orderby`. Esses são todos os operadores de consulta padrão.  
  
 ![Operadores de consulta padrão no IntelliSense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Embora pareça como se <xref:System.Collections.Generic.IEnumerable%601> tivesse sido redefinido para incluir esses métodos adicionais, na verdade esse não é o caso. Os operadores de consulta padrão são implementados como um novo tipo de método chamado *métodos de extensão*. Métodos de extensão "estendem" um tipo existente, eles podem ser chamados como se fossem métodos de instância no tipo. Os operadores de consulta padrão estendem <xref:System.Collections.Generic.IEnumerable%601> e é por essa razão que você pode escrever `numbers.Where(...)`.  
  
 Para começar a usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], tudo o que você realmente precisa saber sobre os métodos de extensão é como colocá-los no escopo em seu aplicativo usando as diretivas `using` corretas. Do ponto de vista do aplicativo, um método de extensão e um método de instância normal são iguais.  
  
 Para obter mais informações sobre os métodos de extensão, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Para obter mais informações sobre os operadores de consulta padrão, consulte [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Alguns provedores de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], como [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], implementam seus próprios operadores de consulta padrão e os métodos de extensão adicionais para outros tipos além de <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Expressões lambda  
 No exemplo anterior, observe que a expressão condicional (`num % 2 == 0`) é passada como um argumento embutido para o método `Where`: `Where(num => num % 2 == 0).` Essa expressão embutida é chamada de uma expressão lambda. É uma maneira conveniente de escrever um código que de outra forma precisaria ser escrito de forma mais complicada como um método anônimo, um delegado genérico ou uma árvore de expressão. No C# `=>` é o operador lambda, que é lido como "vai para". O `num` à esquerda do operador é a variável de entrada que corresponde ao `num` na expressão de consulta. O compilador pode inferir o tipo de `num` porque ele sabe que `numbers` é um tipo <xref:System.Collections.Generic.IEnumerable%601> genérico. O corpo do lambda é exatamente igual à expressão na sintaxe de consulta ou em qualquer outra expressão ou instrução C#, ele pode incluir chamadas de método e outra lógica complexa. O "valor retornado" é apenas o resultado da expressão.  
  
 Para começar a usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], você não precisa usar lambdas extensivamente. No entanto, determinadas consultas só podem ser expressadas em sintaxe de método e algumas delas requerem expressões lambda. Após você se familiarizar mais com lambdas, verá que eles são uma ferramenta poderosa e flexível na sua caixa de ferramentas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. Para obter mais informações, consulte [Expressões Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Possibilidade de Composição das Consultas  
 No exemplo de código anterior, observe que o método `OrderBy` é invocado usando o operador ponto na chamada para `Where`. `Where` produz uma sequência filtrada e, em seguida, `Orderby` opera nessa sequência classificando-a. Como as consultas retornam uma `IEnumerable`, você pode escrevê-las na sintaxe de método encadeando as chamadas de método. Isso é o que o compilador faz nos bastidores quando você escreve consultas usando a sintaxe de consulta. E como uma variável de consulta não armazena os resultados da consulta, você pode modificá-la ou usá-la como base para uma nova consulta a qualquer momento, mesmo depois que ela foi executada.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
