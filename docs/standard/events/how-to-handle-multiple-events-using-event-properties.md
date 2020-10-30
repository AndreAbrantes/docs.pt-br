---
title: Como manipular vários eventos usando propriedades de evento
description: Saiba como lidar com muitos eventos usando as propriedades do evento. Defina coleções de delegados, chaves de evento & Propriedades de evento. Implemente adicionar & remover métodos de acessador.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET]
- multiple events [.NET]
- event handling [.NET], with multiple events
- events [.NET], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: fa0bdc26eba872a62cd5f7a773df0d7a53c83975
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064230"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="94295-105">Como manipular vários eventos usando propriedades de evento</span><span class="sxs-lookup"><span data-stu-id="94295-105">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="94295-106">Para usar as propriedades de evento, defina as propriedades de evento na classe que gera os eventos e, em seguida, defina os representantes das propriedades de evento nas classes que tratam dos eventos.</span><span class="sxs-lookup"><span data-stu-id="94295-106">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="94295-107">Para implementar várias propriedades de evento em uma classe, a classe deve armazenar e manter internamente o representante definido para cada evento.</span><span class="sxs-lookup"><span data-stu-id="94295-107">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="94295-108">Uma abordagem típica é implementar uma coleção de representantes indexada por uma chave de evento.</span><span class="sxs-lookup"><span data-stu-id="94295-108">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="94295-109">Para armazenar os representantes para cada evento, você pode usar a classe <xref:System.ComponentModel.EventHandlerList> ou implementar sua própria coleção.</span><span class="sxs-lookup"><span data-stu-id="94295-109">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="94295-110">A classe da coleção deve fornecer métodos para configurar, acessar e recuperar o representante do manipulador de eventos com base na chave de evento.</span><span class="sxs-lookup"><span data-stu-id="94295-110">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="94295-111">Por exemplo, você poderia usar uma classe <xref:System.Collections.Hashtable> ou derivar uma classe personalizada da classe <xref:System.Collections.DictionaryBase>.</span><span class="sxs-lookup"><span data-stu-id="94295-111">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="94295-112">Os detalhes da implementação da coleção de representantes não precisam ser expostos fora de sua classe.</span><span class="sxs-lookup"><span data-stu-id="94295-112">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="94295-113">Cada propriedade de evento dentro da classe define um método adicionar acessador e um método remover acessador.</span><span class="sxs-lookup"><span data-stu-id="94295-113">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="94295-114">O método adicionar acessador de uma propriedade de eventos adiciona a instância do representante de entrada à coleção de representantes.</span><span class="sxs-lookup"><span data-stu-id="94295-114">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="94295-115">O acessador de remoção de uma propriedade de evento remove a instância do representante de entrada da coleção de representantes.</span><span class="sxs-lookup"><span data-stu-id="94295-115">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="94295-116">Os acessadores de propriedades de evento usam a chave predefinida na propriedade de evento para adicionar e remover instâncias da coleção de representantes.</span><span class="sxs-lookup"><span data-stu-id="94295-116">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="94295-117">Para manipular vários eventos usando propriedades de evento</span><span class="sxs-lookup"><span data-stu-id="94295-117">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="94295-118">Defina a coleção de representantes na classe que gera os eventos.</span><span class="sxs-lookup"><span data-stu-id="94295-118">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="94295-119">Defina uma chave para cada evento.</span><span class="sxs-lookup"><span data-stu-id="94295-119">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="94295-120">Defina as propriedades de evento na classe que gera os eventos.</span><span class="sxs-lookup"><span data-stu-id="94295-120">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="94295-121">Use a coleção de representantes para implementar os métodos adicionar e remover acessador nas propriedades de evento.</span><span class="sxs-lookup"><span data-stu-id="94295-121">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="94295-122">Use as propriedades de evento públicas para adicionar e remover representantes do manipulador de eventos nas classes que tratam dos eventos.</span><span class="sxs-lookup"><span data-stu-id="94295-122">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94295-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94295-123">Example</span></span>  
 <span data-ttu-id="94295-124">O exemplo de C# a seguir implementa as propriedades de evento `MouseDown` e `MouseUp` usando uma <xref:System.ComponentModel.EventHandlerList> para armazenar o representante de cada evento.</span><span class="sxs-lookup"><span data-stu-id="94295-124">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="94295-125">As palavras-chave dos constructos de propriedade de evento estão em negrito.</span><span class="sxs-lookup"><span data-stu-id="94295-125">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="94295-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94295-126">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="94295-127">Eventos</span><span class="sxs-lookup"><span data-stu-id="94295-127">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="94295-128">Como declarar eventos personalizados para conservar memória</span><span class="sxs-lookup"><span data-stu-id="94295-128">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
