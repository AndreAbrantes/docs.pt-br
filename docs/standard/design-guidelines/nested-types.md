---
title: Tipos aninhados
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: bc0aee32b5cc1d40afdd9cce8260d5b5341a687d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706392"
---
# <a name="nested-types"></a><span data-ttu-id="fd33e-102">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="fd33e-102">Nested Types</span></span>

<span data-ttu-id="fd33e-103">Um tipo aninhado é um tipo definido dentro do escopo de outro tipo, que é chamado de tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="fd33e-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="fd33e-104">Um tipo aninhado tem acesso a todos os membros de seu tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="fd33e-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="fd33e-105">Por exemplo, ele tem acesso a campos privados definidos no tipo delimitador e a campos protegidos definidos em todos os ascendentes do tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="fd33e-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="fd33e-106">Em geral, os tipos aninhados devem ser usados com moderação.</span><span class="sxs-lookup"><span data-stu-id="fd33e-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="fd33e-107">Há várias razões para isso.</span><span class="sxs-lookup"><span data-stu-id="fd33e-107">There are several reasons for this.</span></span> <span data-ttu-id="fd33e-108">Alguns desenvolvedores não estão totalmente familiarizados com o conceito.</span><span class="sxs-lookup"><span data-stu-id="fd33e-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="fd33e-109">Esses desenvolvedores podem, por exemplo, ter problemas com a sintaxe de declaração de variáveis de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="fd33e-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="fd33e-110">Os tipos aninhados também são rigidamente acoplados aos tipos delimitadores e, como tal, não são adequados para tipos de finalidade geral.</span><span class="sxs-lookup"><span data-stu-id="fd33e-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="fd33e-111">Os tipos aninhados são mais adequados para modelar detalhes de implementação de seus tipos delimitadores.</span><span class="sxs-lookup"><span data-stu-id="fd33e-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="fd33e-112">O usuário final raramente deve ter que declarar variáveis de um tipo aninhado e quase nunca deve ter que instanciar tipos aninhados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fd33e-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="fd33e-113">Por exemplo, o enumerador de uma coleção pode ser um tipo aninhado dessa coleção.</span><span class="sxs-lookup"><span data-stu-id="fd33e-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="fd33e-114">Enumeradores geralmente são instanciados por seu tipo delimitador e, como muitas linguagens dão suporte à instrução foreach, as variáveis do enumerador raramente precisam ser declaradas pelo usuário final.</span><span class="sxs-lookup"><span data-stu-id="fd33e-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="fd33e-115">✔️ usam tipos aninhados quando a relação entre o tipo aninhado e seu tipo externo é tal que a semântica de acessibilidade de membro é desejável.</span><span class="sxs-lookup"><span data-stu-id="fd33e-115">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="fd33e-116">❌ Não use tipos aninhados públicos como uma construção de agrupamento lógico; Use namespaces para isso.</span><span class="sxs-lookup"><span data-stu-id="fd33e-116">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="fd33e-117">❌ Evite tipos aninhados publicamente expostos.</span><span class="sxs-lookup"><span data-stu-id="fd33e-117">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="fd33e-118">A única exceção a isso é se as variáveis do tipo aninhado precisam ser declaradas apenas em cenários raros, como subclasse ou outros cenários de personalização avançada.</span><span class="sxs-lookup"><span data-stu-id="fd33e-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="fd33e-119">❌ Não use tipos aninhados se for provável que o tipo seja referenciado fora do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="fd33e-119">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="fd33e-120">Por exemplo, uma enumeração passada para um método definido em uma classe não deve ser definida como um tipo aninhado na classe.</span><span class="sxs-lookup"><span data-stu-id="fd33e-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="fd33e-121">❌ Não use tipos aninhados se eles precisarem ser instanciados pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="fd33e-121">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="fd33e-122">Se um tipo tiver um construtor público, ele provavelmente não deve ser aninhado.</span><span class="sxs-lookup"><span data-stu-id="fd33e-122">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="fd33e-123">Se um tipo puder ser instanciado, isso parecerá indicar que o tipo tem um local na estrutura por si só (você pode criá-lo, trabalhar com ele e destruí-lo sem nunca usar o tipo externo) e, portanto, não deve ser aninhado.</span><span class="sxs-lookup"><span data-stu-id="fd33e-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="fd33e-124">Os tipos internos não devem ser amplamente reutilizados fora do tipo externo sem nenhuma relação com o tipo externo.</span><span class="sxs-lookup"><span data-stu-id="fd33e-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="fd33e-125">❌ Não defina um tipo aninhado como membro de uma interface.</span><span class="sxs-lookup"><span data-stu-id="fd33e-125">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="fd33e-126">Muitas linguagens não oferecem suporte a tal construção.</span><span class="sxs-lookup"><span data-stu-id="fd33e-126">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="fd33e-127">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="fd33e-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fd33e-128">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fd33e-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fd33e-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd33e-129">See also</span></span>

- [<span data-ttu-id="fd33e-130">Diretrizes de design de tipo</span><span class="sxs-lookup"><span data-stu-id="fd33e-130">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="fd33e-131">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="fd33e-131">Framework Design Guidelines</span></span>](index.md)
