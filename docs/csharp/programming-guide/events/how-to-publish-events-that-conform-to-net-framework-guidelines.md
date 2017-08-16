---
title: "Como publicar eventos em conformidade com as diretrizes do .NET Framework (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
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
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 6d529e60643966fbabd5290543146977b4dc83c5
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Como publicar eventos em conformidade com as diretrizes do .NET Framework (Guia de Programação em C#)
O procedimento a seguir demonstra como adicionar eventos que seguem o padrão do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] para classes e structs. Todos os eventos na biblioteca de classes do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] se baseiam no delegado <xref:System.EventHandler>, que é definido da seguinte maneira:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  O [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] apresenta uma versão genérica desse delegado, o <xref:System.EventHandler%601>. Os exemplos a seguir mostram como usar as duas versões.  
  
 Embora os eventos nas classes que você define possam ser baseados em qualquer tipo delegado válido, até mesmo nos delegados que retornam um valor, é geralmente recomendável que você baseie seus eventos no padrão do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], usando o <xref:System.EventHandler>, conforme mostrado no exemplo a seguir.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Para publicar eventos com base no padrão EventHandler  
  
1.  (Pule esta etapa e vá para a etapa 3a se você não precisa enviar dados personalizados com o evento). Declare a classe dos seus dados personalizados em um escopo que seja visível para as classes publicadora e assinante. Em seguida, adicione os membros necessários para manter seus dados de evento personalizados. Neste exemplo, uma cadeia de caracteres simples é retornada.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  (Pule esta etapa se você estiver usando a versão genérica de <xref:System.EventHandler%601>). Declare um delegado na sua classe de publicação. Dê a ela um nome que termina com *EventHandler*. O segundo parâmetro especifica o tipo personalizado de EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Declare o evento em sua classe de publicação, usando uma das etapas a seguir.  
  
    1.  Se você não tiver uma classe EventArgs personalizada, o tipo de evento será o delegado EventHandler não genérico. Você não precisa declarar o delegado porque ele já está declarado no namespace <xref:System> que está incluído quando você cria seu projeto do C#. Adicione o seguinte código à sua classe publicadora.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Se você estiver usando a versão não genérica de <xref:System.EventHandler> e você tem uma classe personalizada derivada de <xref:System.EventArgs>, declare o evento dentro de sua classe de publicação e use o delegado da etapa 2 como o tipo.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Se você estiver usando a versão genérica, não é necessário um delegado personalizado. Em vez disso, na sua classe de publicação, especifique o tipo de evento como `EventHandler<CustomEventArgs>`, substituindo o nome da sua própria classe entre os colchetes angulares.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra as etapas anteriores, usando uma classe EventArgs personalizada e o <xref:System.EventHandler%601> como o tipo de evento.  
  
 [!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Delegate>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)
