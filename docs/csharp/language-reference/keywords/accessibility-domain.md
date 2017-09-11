---
title: "Domínio de acessibilidade (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 90faf22d8a7d515ae8bd062f0b95f4be5e051f79
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="cf98f-102">Domínio de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cf98f-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="cf98f-103">O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="cf98f-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="cf98f-104">Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="cf98f-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="cf98f-105">O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="cf98f-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="cf98f-106">Isto é, o domínio inclui todos os arquivos de origem deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cf98f-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="cf98f-107">O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="cf98f-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="cf98f-108">Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="cf98f-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="cf98f-109">O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="cf98f-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="cf98f-110">Esses conceitos são demonstrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cf98f-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf98f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf98f-111">Example</span></span>  
 <span data-ttu-id="cf98f-112">Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`.</span><span class="sxs-lookup"><span data-stu-id="cf98f-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="cf98f-113">As classes contêm campos que têm diferentes acessibilidades declaradas.</span><span class="sxs-lookup"><span data-stu-id="cf98f-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="cf98f-114">No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro.</span><span class="sxs-lookup"><span data-stu-id="cf98f-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="cf98f-115">Observe que as instruções que tentam fazer referência aos membros inacessíveis são tornadas inertes ao serem transformadas em comentários.</span><span class="sxs-lookup"><span data-stu-id="cf98f-115">Notice that the statements that try to reference the inaccessible members are commented out.</span></span> <span data-ttu-id="cf98f-116">Se você quiser ver os erros de compilador causados ao referenciar um membro inacessível, remova os comentários um por vez.</span><span class="sxs-lookup"><span data-stu-id="cf98f-116">If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
 <span data-ttu-id="cf98f-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cf98f-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cf98f-118">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cf98f-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf98f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf98f-119">See Also</span></span>  
 <span data-ttu-id="cf98f-120">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cf98f-121">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cf98f-122">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="cf98f-123">[Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-123">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="cf98f-124">[Níveis de Acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-124">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="cf98f-125">[Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-125">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="cf98f-126">[Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="cf98f-127">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-127">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="cf98f-128">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-128">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="cf98f-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="cf98f-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="cf98f-130">internal</span><span class="sxs-lookup"><span data-stu-id="cf98f-130">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

