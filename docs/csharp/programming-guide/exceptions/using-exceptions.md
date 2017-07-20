---
title: "Usando exceções (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: a8c29002ae2287df60996ed2b23068eec1e2739b
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="using-exceptions-c-programming-guide"></a>Usando exceções (Guia de Programação em C#)
No C#, os erros no programa em tempo de execução são propagados pelo programa usando um mecanismo chamado exceções. As exceções são geradas pelo código que encontra um erro e capturadas pelo código que pode corrigir o erro. As exceções podem ser geradas pelo CLR (Common Language Runtime) do .NET Framework ou pelo código em um programa. Uma vez que uma exceção é gerada, ela é propagada acima na pilha de chamadas até uma instrução `catch` para a exceção ser encontrada. As exceções não capturadas são tratadas por um manipulador de exceção genérico fornecido pelo sistema que exibe uma caixa de diálogo.  
  
 As exceções são representadas por classes derivadas de <xref:System.Exception>. Essa classe identifica o tipo de exceção e contém propriedades que têm detalhes sobre a exceção. Gerar uma exceção envolve criar uma instância de uma classe derivada de exceção, opcionalmente configurar propriedades da exceção e, em seguida, gerar o objeto usando a palavra-chave `throw`. Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Depois que uma exceção é gerada, o tempo de execução verifica a instrução atual para ver se ela está dentro de um bloco `try`. Se estiver, todos os blocos `catch` associados ao bloco `try` serão verificados para ver se eles podem capturar a exceção. Os blocos `Catch` normalmente especificam os tipos de exceção. Se o tipo do bloco `catch` for do mesmo tipo que a exceção ou uma classe base da exceção, o bloco `catch` poderá manipular o método. Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Se a instrução que gera uma exceção não estiver dentro de um bloco `try` ou se o bloco `try` que o contém não tiver um bloco `catch` correspondente, o tempo de execução verificará o método de chamada quanto a uma instrução `try` e blocos `catch`. O tempo de execução continuará acima na pilha de chamada, pesquisando um bloco `catch` compatível. Depois que o bloco `catch` for localizado e executado, o controle será passado para a próxima instrução após aquele bloco `catch`.  
  
 Uma instrução `try` pode conter mais de um bloco `catch`. A primeira instrução `catch` que pode manipular a exceção é executado, todas as instruções `catch` posteriores, mesmo se forem compatíveis, são ignoradas. Portanto, os blocos de captura devem sempre ser ordenados do mais específico (ou mais derivado) para o menos específico. Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Antes de o bloco `catch` ser executado, o tempo de execução verifica se há blocos `finally`. Os blocos `Finally` permitem que o programador limpe qualquer estado ambíguo que pode ser deixado de um bloco `try` cancelado ou libere quaisquer recursos externos (como identificadores de gráfico, conexões de banco de dados ou fluxos de arquivo) sem esperar o coletor de lixo no tempo de execução finalizar os objetos. Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Se `WriteByte()` gerou uma exceção, o código no segundo bloco `try` que tentar reabrir o arquivo falhará se `file.Close()` não for chamado e o arquivo permanecerá bloqueado. Como os blocos `finally` são executados mesmo se uma exceção for gerada, o bloco `finally` no exemplo anterior permite que o arquivo seja fechado corretamente e ajuda a evitar um erro.  
  
 Se não for encontrado nenhum bloco `catch` compatível na pilha de chamadas após uma exceção ser gerada, ocorrerá uma das três coisas:  
  
-   Se a exceção estiver em um finalizador, o finalizador será anulado e o finalizador base, se houver, será chamado.  
  
-   Se a pilha de chamadas contiver um construtor estático ou um inicializador de campo estático, uma <xref:System.TypeInitializationException> será gerada, com a exceção original atribuída à propriedade <xref:System.Exception.InnerException%2A> da nova exceção.  
  
-   Se o início do thread for atingido, o thread será encerrado.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/index.md)
