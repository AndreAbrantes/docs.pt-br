---
title: Eventos – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: e15c3d124b4d1c30e2f9bb9f44b40e25b6a72346
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240714"
---
# <a name="events-c-programming-guide"></a>Eventos (Guia de Programação em C#)
Eventos permitem que uma [classe](../../language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre. A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.  
  
Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem. Você pode usar o IDE (ambiente de desenvolvimento integrado) do Visual C# para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular. O IDE oferece uma maneira fácil de adicionar automaticamente um método de manipulador de eventos vazio e o código para assinar o evento. Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](./how-to-subscribe-to-and-unsubscribe-from-events.md).
  
## <a name="events-overview"></a>Visão geral sobre eventos  
 Os eventos têm as seguintes propriedades:  
  
- O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.  
  
- Um evento pode ter vários assinantes. Um assinante pode manipular vários eventos de vários publicadores.  
  
- Eventos que não têm assinantes nunca são acionados.  
  
- Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.  
  
- Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado. Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- Na biblioteca de classes .NET Framework, os eventos são baseados no delegado <xref:System.EventHandler> e na classe base <xref:System.EventArgs>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter mais informações, consulte:  
  
- [Como realizar e cancelar a assinatura de eventos](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Como publicar eventos que estão em conformidade com as diretrizes do .NET](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Como acionar eventos de classe base em classes derivadas](./how-to-raise-base-class-events-in-derived-classes.md)

- [Como implementar eventos de interface](./how-to-implement-interface-events.md)

- [Como implementar acessadores de eventos personalizados](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Eventos](~/_csharplang/spec/classes.md#events) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="featured-book-chapters"></a>Capítulos do Livro em Destaque  
 [Expressões lambda, eventos e delegados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegados e eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) em [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.EventHandler>
- [Guia de programação C#](../index.md)
- [Delegados](../delegates/index.md)
- [Criando manipuladores de eventos no Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
