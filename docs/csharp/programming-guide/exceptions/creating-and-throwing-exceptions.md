---
title: "Criando e lançando exceções (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c3eab50a6a785676dd397498fbe95348187e2b7e
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Criando e lançando exceções (Guia de Programação em C#)
As exceções são usadas para indicar que ocorreu um erro durante a execução do programa. Objetos de exceção que descrevem um erro são criados e, em seguida, *lançados* com a palavra-chave [throw](../../../csharp/language-reference/keywords/throw.md). Então, o tempo de execução procura o manipulador de exceção mais compatível.  
  
 Os programadores devem lançar exceções quando uma ou mais das seguintes condições forem verdadeiras:  
  
-   O método não pode concluir sua funcionalidade definida.  
  
     Por exemplo, se um parâmetro para um método tem um valor inválido:  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   É feita uma chamada inadequada a um objeto, com base no estado do objeto.  
  
     Um exemplo pode ser a tentativa de gravar em um arquivo somente leitura. Em casos em que um estado do objeto não permite uma operação, lance uma instância de <xref:System.InvalidOperationException> ou um objeto com base em uma derivação dessa classe. Este é um exemplo de um método que lança um objeto <xref:System.InvalidOperationException>:  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Quando um argumento para um método causa uma exceção.  
  
     Nesse caso, a exceção original deve ser capturada e uma instância <xref:System.ArgumentException> deve ser criada. A exceção original deve ser passada para o construtor da <xref:System.ArgumentException> como o parâmetro <xref:System.Exception.InnerException%2A>:  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 As exceções contêm uma propriedade chamada <xref:System.Exception.StackTrace%2A>. Essa cadeia de caracteres contém o nome dos métodos na pilha de chamadas atual, junto com o nome de arquivo e o número de linha em que a exceção foi lançada para cada método. Um objeto <xref:System.Exception.StackTrace%2A> é criado automaticamente pelo CLR (Common Language Runtime) no ponto da instrução `throw`, de modo que as exceções devem ser lançadas do ponto em que o rastreamento de pilha deve começar.  
  
 Todas as exceções contêm uma propriedade chamada <xref:System.Exception.Message%2A>. Essa cadeia de caracteres deve ser definida para explicar o motivo da exceção. Observe que as informações que são sensíveis à segurança não devem ser colocadas no texto da mensagem. Além da <xref:System.Exception.Message%2A>, a <xref:System.ArgumentException> contém uma propriedade chamada <xref:System.ArgumentException.ParamName%2A> que deve ser definida como o nome do argumento que causou a exceção a ser lançada. No caso de um setter da propriedade, a <xref:System.ArgumentException.ParamName%2A> deve ser definida como `value`.  
  
 Os membros de métodos públicos e protegidos devem lançar exceções sempre que não puderem concluir suas funções pretendidas. A classe de exceção que é lançada deve ser a exceção mais específica disponível que se adapta às condições do erro. Essas exceções devem ser documentadas como parte da funcionalidade de classe e as classes derivadas ou as atualizações da classe original devem manter o mesmo comportamento para compatibilidade com versões anteriores.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Coisas a serem evitadas ao lançar exceções  
 A lista a seguir identifica as práticas a serem evitadas ao lançar exceções:  
  
-   As exceções não devem ser usadas para alterar o fluxo de um programa, como parte da execução normal. As exceções só devem ser usadas para relatar e tratar condições de erro.  
  
-   As exceções não devem ser retornadas como um valor retornado ou um parâmetro em vez de serem lançadas.  
  
-   Não lance <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName> ou <xref:System.IndexOutOfRangeException?displayProperty=fullName> intencionalmente do seu próprio código-fonte.  
  
-   Não crie exceções que podem ser lançadas no modo de depuração, mas não no modo de versão. Em vez disso, use o Debug Assert para identificar erros em tempo de execução durante a fase de desenvolvimento.  
  
## <a name="defining-exception-classes"></a>Definindo classes de exceção  
 Os programas podem lançar uma classe de exceção predefinida no namespace <xref:System> (exceto onde observado anteriormente) ou criar suas próprias classes de exceção, derivando de <xref:System.Exception>. As classes derivadas devem definir pelo menos quatro construtores: um construtor padrão, um que define a propriedade de mensagem e um que define as propriedades <xref:System.Exception.Message%2A> e <xref:System.Exception.InnerException%2A>. O quarto construtor é usado para serializar a exceção. Novas classes de exceção devem ser serializáveis. Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Novas propriedades só devem ser adicionadas à classe de exceção quando os dados que elas fornecem são úteis para resolver a exceção. Se forem adicionadas novas propriedades à classe de exceção derivada, `ToString()` deverá ser substituído para retornar as informações adicionadas.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Exceções e tratamento de exceções](../../../csharp/programming-guide/exceptions/index.md)   
 [Hierarquia de exceções](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [Tratamento de Exceção](../../../csharp/programming-guide/exceptions/exception-handling.md)
