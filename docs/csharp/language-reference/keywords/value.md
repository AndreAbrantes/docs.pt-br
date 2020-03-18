---
title: Palavra-chave contextual value – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712891"
---
# <a name="value-c-reference"></a><span data-ttu-id="63706-102">value (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="63706-102">value (C# Reference)</span></span>

<span data-ttu-id="63706-103">`value` A palavra-chave contextual `set` é usada no acessório em declarações [de propriedade](../../programming-guide/classes-and-structs/properties.md) e [indexador.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="63706-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="63706-104">É semelhante a um parâmetro de entrada de um método.</span><span class="sxs-lookup"><span data-stu-id="63706-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="63706-105">A `value` palavra faz referência ao valor que o código do cliente está tentando atribuir à propriedade ou indexador.</span><span class="sxs-lookup"><span data-stu-id="63706-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="63706-106">No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`.</span><span class="sxs-lookup"><span data-stu-id="63706-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="63706-107">Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="63706-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="63706-108">Para obter mais informações, consulte os artigos [Propriedades](../../programming-guide/classes-and-structs/properties.md) e [Indexeres.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="63706-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63706-109">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="63706-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="63706-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="63706-110">See also</span></span>

- [<span data-ttu-id="63706-111">C# Referência</span><span class="sxs-lookup"><span data-stu-id="63706-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="63706-112">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="63706-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="63706-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="63706-113">C# Keywords</span></span>](index.md)
