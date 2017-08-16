---
title: "Genéricos em tempo de execução (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dc0bd1d44192bce0adffc8efd5a089771539f62f
ms.lasthandoff: 03/13/2017

---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Genéricos em tempo de execução (Guia de Programação em C#)
Um tipo genérico ou método compilado em Microsoft Intermediate Language (MSIL) conterá metadados que o identificarão como possuidor de parâmetros de tipo. O uso de MSIL em um tipo genérico será diferente de acordo com o parâmetro de tipo fornecido, ou seja, se ele é um tipo de valor ou um tipo de referência.  
  
 Quando um tipo genérico é construído pela primeira vez com um tipo de valor como parâmetro, o tempo de execução cria um tipo genérico especializado com o(s) parâmetro(s) fornecido(s) substituído(s) nos locais apropriados do MSIL. Os tipos genéricos especializados são criados uma vez para cada tipo de valor único usado como parâmetro.  
  
 Por exemplo, caso o código do programa declarar uma pilha construída de inteiros:  
  
 [!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 Neste ponto, o tempo de execução gerará uma versão especializada da classe <xref:System.Collections.Generic.Stack%601> com o inteiro substituído corretamente, de acordo com seu parâmetro. Agora, sempre que o código do programa utilizar uma pilha de inteiros, o tempo de execução reutilizará a classe especializada <xref:System.Collections.Generic.Stack%601> gerada. No exemplo a seguir, são criadas duas instâncias de uma pilha de inteiros e eles compartilham uma única instância do código `Stack<int>`:  
  
 [!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 No entanto, suponha que outra classe <xref:System.Collections.Generic.Stack%601> com um tipo de valor diferente – como `long` ou uma estrutura definida pelo usuário como parâmetro – foi criada em outro ponto do código. Como resultado, o tempo de execução gerará outra versão do tipo genérico e substituirá um `long` nos locais apropriados no MSIL. Conversões não são mais necessárias, pois cada classe genérica especializada contém o tipo de valor nativamente.  
  
 Os genéricos funcionam de outro modo nos tipos de referência. Na primeira vez em que um genérico é construído com qualquer tipo de referência, o tempo de execução cria um tipo genérico especializado com referências de objeto substituídas por parâmetros no MSIL. Em seguida, sempre que um tipo construído for instanciado com um tipo de referência como parâmetro, independentemente do tipo, o tempo de execução reutilizará a versão especializada do tipo genérico criada anteriormente. Isso é possível porque todas as referências são do mesmo tamanho.  
  
 Por exemplo, suponha que há dois tipos de referência, uma classe `Customer` e uma classe `Order` e que uma pilha de tipos `Customer` foi criada:  
  
 [!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 Neste ponto, o tempo de execução gerará uma versão especializada da classe <xref:System.Collections.Generic.Stack%601> que armazenará referências de objeto que serão preenchidas posteriormente, em vez de armazenar dados. Suponha que a próxima linha de código crie uma pilha de outro tipo de referência, com o nome `Order`:  
  
 [!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 Ao contrário dos tipos de valor, outra versão especializada da classe <xref:System.Collections.Generic.Stack%601> não será criada para o tipo `Order`. Em vez disso, uma instância da versão especializada da classe <xref:System.Collections.Generic.Stack%601> será criada e a variável `orders` será definida para referenciá-la. Imagine que uma linha de código foi encontrada para criar uma pilha de um tipo `Customer`:  
  
 [!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Assim como no uso anterior da classe <xref:System.Collections.Generic.Stack%601> criada por meio do tipo `Order`, outra instância da classe especializada <xref:System.Collections.Generic.Stack%601> será criada. Os ponteiros contidos nela são definidos para referenciar uma área de memória do tamanho de um tipo `Customer`. Como a quantidade de tipos de referência pode variar muito entre os programas, a implementação de genéricos no C# reduz significativamente a quantidade de código ao diminuir para um o número de classes especializadas criadas pelo compilador para classes genéricas ou tipos de referência.  
  
 Além disso, quando uma classe genérica do C# for instanciada usando um tipo de valor ou parâmetro de tipo de referência, a reflexão pode consultá-la em tempo de execução e o seu tipo real e parâmetro de tipo podem ser determinados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Genéricos](https://msdn.microsoft.com/library/ms172192)
