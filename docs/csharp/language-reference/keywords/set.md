---
description: Palavra-chave set – Referência de C#
title: Palavra-chave set – Referência de C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136909"
---
# <a name="set-c-reference"></a><span data-ttu-id="e172c-103">set (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e172c-103">set (C# Reference)</span></span>

<span data-ttu-id="e172c-104">A palavra-chave `set` define um método *acessador* em uma propriedade ou indexador que atribui um valor ao elemento da propriedade ou do elemento.</span><span class="sxs-lookup"><span data-stu-id="e172c-104">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="e172c-105">Para obter mais informações e exemplos, consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e172c-105">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="e172c-106">O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="e172c-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="e172c-107">Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e172c-107">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="e172c-108">Geralmente, o acessador `set` consiste em uma única instrução que retorna um valor, como no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="e172c-108">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="e172c-109">Começando com o C# 7.0, você pode implementar o acessador `set` como um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="e172c-109">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="e172c-110">O exemplo a seguir implementa os acessadores `get` e `set` como membros com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="e172c-110">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="e172c-111">Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação, a não ser a configuração ou a recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="e172c-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="e172c-112">O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="e172c-112">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="e172c-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e172c-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e172c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e172c-114">See also</span></span>

- [<span data-ttu-id="e172c-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="e172c-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e172c-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e172c-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e172c-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e172c-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e172c-118">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e172c-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
