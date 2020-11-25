---
title: Nomes de membros de tipo
description: Conheça as diretrizes para nomear membros de tipo no .NET, como métodos, propriedades, eventos e campos.
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 409e881198a359fa28356e22ea73d5b724742a0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706470"
---
# <a name="names-of-type-members"></a><span data-ttu-id="54c84-103">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="54c84-103">Names of Type Members</span></span>

<span data-ttu-id="54c84-104">Tipos são compostos de membros: métodos, propriedades, eventos, construtores e campos.</span><span class="sxs-lookup"><span data-stu-id="54c84-104">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="54c84-105">As seções a seguir descrevem as diretrizes de nomenclatura de membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="54c84-105">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="54c84-106">Nomes de métodos</span><span class="sxs-lookup"><span data-stu-id="54c84-106">Names of Methods</span></span>

 <span data-ttu-id="54c84-107">Como os métodos são os meios para executar uma ação, as diretrizes de design exigem que os nomes de métodos sejam verbos ou frases verbais.</span><span class="sxs-lookup"><span data-stu-id="54c84-107">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="54c84-108">Seguir essa diretriz também serve para distinguir os nomes de métodos de nomes de propriedades e tipos, que são substantivos ou frases adjetivas.</span><span class="sxs-lookup"><span data-stu-id="54c84-108">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="54c84-109">✔️ fornecem nomes de métodos que são verbos ou frases de verbo.</span><span class="sxs-lookup"><span data-stu-id="54c84-109">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="54c84-110">Nomes de propriedades</span><span class="sxs-lookup"><span data-stu-id="54c84-110">Names of Properties</span></span>

 <span data-ttu-id="54c84-111">Diferentemente de outros membros, as propriedades devem ser nomeadas com uma frase substantivada ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="54c84-111">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="54c84-112">Isso porque uma propriedade se refere a dados, e o nome da propriedade reflete isso.</span><span class="sxs-lookup"><span data-stu-id="54c84-112">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="54c84-113">PascalCasing sempre é usado para nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="54c84-113">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="54c84-114">✔️ as propriedades de nome usando um substantivo, uma frase de substantivo ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="54c84-114">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="54c84-115">❌ Não têm propriedades que correspondam ao nome dos métodos "Get", como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="54c84-115">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="54c84-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="54c84-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="54c84-117">Esse padrão geralmente indica que a propriedade deveria realmente ser um método.</span><span class="sxs-lookup"><span data-stu-id="54c84-117">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="54c84-118">✔️ as propriedades da coleção de nomes com uma frase plural que descreve os itens na coleção em vez de usar uma frase singular seguida de "List" ou "Collection".</span><span class="sxs-lookup"><span data-stu-id="54c84-118">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="54c84-119">✔️ as propriedades booleanas de nome com uma frase afirmativo ( `CanSeek` em vez de `CantSeek` ).</span><span class="sxs-lookup"><span data-stu-id="54c84-119">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="54c84-120">Opcionalmente, você também pode prefixar propriedades booleanas com "is", "Can" ou "tem", mas apenas onde ele agrega valor.</span><span class="sxs-lookup"><span data-stu-id="54c84-120">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="54c84-121">✔️ Considere atribuir uma propriedade com o mesmo nome que o seu tipo.</span><span class="sxs-lookup"><span data-stu-id="54c84-121">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="54c84-122">Por exemplo, a seguinte propriedade obtém e define corretamente um valor de enumeração denominado `Color`, portanto, a propriedade é chamada `Color`:</span><span class="sxs-lookup"><span data-stu-id="54c84-122">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="54c84-123">Nomes de eventos</span><span class="sxs-lookup"><span data-stu-id="54c84-123">Names of Events</span></span>

 <span data-ttu-id="54c84-124">Eventos sempre fazem referência a uma ação, seja uma ação que está acontecendo ou que já ocorreu.</span><span class="sxs-lookup"><span data-stu-id="54c84-124">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="54c84-125">Portanto, assim como acontece com os métodos, os eventos são nomeados com verbos e o tempo verbal é usado para indicar o horário em que o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="54c84-125">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="54c84-126">✔️ eventos de nome com um verbo ou uma frase verbal.</span><span class="sxs-lookup"><span data-stu-id="54c84-126">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="54c84-127">Os exemplos incluem `Clicked`, `Painting`, `DroppedDown`, etc.</span><span class="sxs-lookup"><span data-stu-id="54c84-127">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="54c84-128">✔️ fornecer nomes de eventos com um conceito de antes e depois, usando as dezenas e as últimas.</span><span class="sxs-lookup"><span data-stu-id="54c84-128">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="54c84-129">Por exemplo, um evento de fechamento gerado antes de uma janela ser fechada seria chamado de `Closing`, e um gerado após a janela ser fechada seria chamado de `Closed`.</span><span class="sxs-lookup"><span data-stu-id="54c84-129">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="54c84-130">❌ Não use prefixos "Before" ou "After" ou as pós-correções para indicar pré e eventos Post.</span><span class="sxs-lookup"><span data-stu-id="54c84-130">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="54c84-131">Use os tempos verbais Pretérito e Presente conforme descrito.</span><span class="sxs-lookup"><span data-stu-id="54c84-131">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="54c84-132">✔️ manipuladores de eventos de nome (delegados usados como tipos de eventos) com o sufixo "EventHandler", conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="54c84-132">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="54c84-133">✔️ usar dois parâmetros chamados `sender` e `e` em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="54c84-133">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="54c84-134">O parâmetro do remetente representa o objeto que acionou o evento.</span><span class="sxs-lookup"><span data-stu-id="54c84-134">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="54c84-135">O parâmetro do remetente normalmente é do tipo `object`, mesmo se for possível empregar um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="54c84-135">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="54c84-136">✔️ classes de argumento de evento de nome com o sufixo "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="54c84-136">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="54c84-137">Nomes de campos</span><span class="sxs-lookup"><span data-stu-id="54c84-137">Names of Fields</span></span>

 <span data-ttu-id="54c84-138">As diretrizes de nomenclatura de campo se aplicam a campos públicos e protegidos estáticos.</span><span class="sxs-lookup"><span data-stu-id="54c84-138">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="54c84-139">Campos particulares e internos não são cobertos pelas diretrizes, e campos de instância pública ou protegida não são permitidos pelas [diretrizes de design de membro](member.md).</span><span class="sxs-lookup"><span data-stu-id="54c84-139">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="54c84-140">✔️ Use PascalCasing em nomes de campo.</span><span class="sxs-lookup"><span data-stu-id="54c84-140">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="54c84-141">✔️ os campos de nome usando um substantivo, uma frase de substantivo ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="54c84-141">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="54c84-142">❌ Não use um prefixo para nomes de campo.</span><span class="sxs-lookup"><span data-stu-id="54c84-142">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="54c84-143">Por exemplo, não use "g_" ou "s_" para indicar campos estáticos.</span><span class="sxs-lookup"><span data-stu-id="54c84-143">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="54c84-144">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="54c84-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="54c84-145">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="54c84-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="54c84-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="54c84-146">See also</span></span>

- [<span data-ttu-id="54c84-147">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="54c84-147">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="54c84-148">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="54c84-148">Naming Guidelines</span></span>](naming-guidelines.md)
