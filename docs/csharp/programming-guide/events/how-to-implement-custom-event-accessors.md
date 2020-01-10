---
title: Como implementar acessadores de eventos personalizados C# – guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705347"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="8d10f-102">Como implementar acessadores de evento personalizadosC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="8d10f-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="8d10f-103">Um evento é um tipo especial de delegado multicast que só pode ser invocado de dentro da classe que ela está declarado.</span><span class="sxs-lookup"><span data-stu-id="8d10f-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="8d10f-104">O código cliente assina o evento ao fornecer uma referência a um método que deve ser invocado quando o evento for disparado.</span><span class="sxs-lookup"><span data-stu-id="8d10f-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="8d10f-105">Esses métodos são adicionados à lista de invocação do delegado por meio de acessadores de evento, que se assemelham aos acessadores de propriedade, com a exceção de que os acessadores de eventos são nomeados `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="8d10f-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="8d10f-106">Na maioria dos casos, não é necessário fornecer acessadores de eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8d10f-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="8d10f-107">Quando nenhum acessador de evento personalizado for fornecido no código, o compilador o adicionará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8d10f-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="8d10f-108">No entanto, em alguns casos será necessário fornecer um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="8d10f-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="8d10f-109">Um desses casos é mostrado no tópico [como implementar eventos de interface](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="8d10f-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="8d10f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d10f-110">Example</span></span>  
 <span data-ttu-id="8d10f-111">O exemplo a seguir mostra como implementar os acessadores de eventos personalizados adicionar e remover.</span><span class="sxs-lookup"><span data-stu-id="8d10f-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="8d10f-112">Embora seja possível substituir qualquer código dentro dos acessadores, é recomendável que você bloqueie o evento antes de adicionar ou remover um novo método de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8d10f-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="8d10f-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="8d10f-113">See also</span></span>

- [<span data-ttu-id="8d10f-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="8d10f-114">Events</span></span>](./index.md)
- [<span data-ttu-id="8d10f-115">event</span><span class="sxs-lookup"><span data-stu-id="8d10f-115">event</span></span>](../../language-reference/keywords/event.md)
