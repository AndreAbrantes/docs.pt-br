---
title: "event (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
dev_langs:
- CSharp
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
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
ms.openlocfilehash: 60a6322f8e120c6a443638b4f6e409acdfa0b235
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="event-c-reference"></a>event (Referência de C#)
A palavra-chave `event` é usada para declarar um evento em uma classe publicadora.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar e acionar um evento que usa o <xref:System.EventHandler> como o tipo delegado subjacente. Para obter o exemplo de código completo, que também mostra como usar o tipo delegado <xref:System.EventHandler%601> genérico e como assinar um evento e criar um método de manipulador de eventos, consulte [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]  
  
 Os eventos são um tipo especial de delegado multicast que só podem ser invocados de dentro da classe ou struct em que eles são declarados (a classe publicadora). Se outras classes ou structs assinarem o evento, seus respectivos métodos de manipulador de eventos serão chamados quando a classe publicadora acionar o evento. Para obter mais informações e exemplos de código, consulte [Eventos](../../../csharp/programming-guide/events/index.md) e [Delegados](../../../csharp/programming-guide/delegates/index.md).  
  
 Os eventos podem ser marcados como [públicos](../../../csharp/language-reference/keywords/public.md), [particulares](../../../csharp/language-reference/keywords/private.md), [protegidos](../../../csharp/language-reference/keywords/protected.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou `protected``internal`. Esses modificadores de acesso definem como os usuários da classe podem acessar o evento. Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Palavras-chave e eventos  
 As palavras-chave a seguir aplicam-se a eventos.  
  
|Palavra-chave|Descrição|Para obter mais informações|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe.|[Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Permite que classes derivadas substituam o comportamento do evento, usando a palavra-chave [override](../../../csharp/language-reference/keywords/override.md).|[Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Especifica que, para classes derivadas, o evento não é mais virtual.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|O compilador não gerará mais os blocos de acessador de evento `add` e `remove`, portanto, as classes derivadas devem fornecer sua própria implementação.||  
  
 Um evento pode ser declarado como um evento estático, usando apalavra-chave [static](../../../csharp/language-reference/keywords/static.md). Isso torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Um evento pode ser marcado como um evento virtual, usando a palavra-chave [virtual](../../../csharp/language-reference/keywords/virtual.md). Isso habilita as classes derivadas a substituírem o comportamento do evento, usando a palavra-chave [override](../../../csharp/language-reference/keywords/override.md). Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Um evento que substitui um evento virtual também pode ser [sealed](../../../csharp/language-reference/keywords/sealed.md), o que especifica que ele não é mais virtual para classes derivadas. Por fim, um evento pode ser declarado [abstract](../../../csharp/language-reference/keywords/abstract.md), o que significa que o compilador não gerará os blocos de acessador de evento `add` e `remove`. Portanto, classes derivadas devem fornecer sua própria implementação.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [add](../../../csharp/language-reference/keywords/add.md)   
 [remove](../../../csharp/language-reference/keywords/remove.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Como combinar delegados (delegados multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
