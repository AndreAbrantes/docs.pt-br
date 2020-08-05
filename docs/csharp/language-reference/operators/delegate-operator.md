---
title: operador delegate – referência do C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 85f960d236e35379180ec1d7f7dcc49e1ccddf55
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556671"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="132ba-102">operador delegate (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="132ba-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="132ba-103">O operador `delegate` cria um método anônimo que pode ser convertido em um tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="132ba-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="132ba-104">Começando com o C# 3, as expressões lambda fornecem uma maneira mais concisa e expressiva de criar uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="132ba-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="132ba-105">Use o [operador =>](lambda-operator.md) para construir uma expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="132ba-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="132ba-106">Para saber mais sobre recursos de expressões lambda, por exemplo, que capturam variáveis externas, confira [Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="132ba-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="132ba-107">Você pode omitir a lista de parâmetros quando usa o operador `delegate`.</span><span class="sxs-lookup"><span data-stu-id="132ba-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="132ba-108">Se você fizer isso, o método anônimo criado poderá ser convertido em um tipo delegado com qualquer lista de parâmetros, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="132ba-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="132ba-109">Essa é a única funcionalidade de métodos anônimos que não tem suporte por expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="132ba-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="132ba-110">Em todos os outros casos, uma expressão lambda é a forma preferida de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="132ba-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="132ba-111">Você também usa a palavra-chave `delegate` para declarar um [tipo delegado](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="132ba-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="132ba-112">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="132ba-112">C# language specification</span></span>

<span data-ttu-id="132ba-113">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="132ba-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="132ba-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="132ba-114">See also</span></span>

- [<span data-ttu-id="132ba-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="132ba-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="132ba-116">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="132ba-116">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="132ba-117">= Operador de></span><span class="sxs-lookup"><span data-stu-id="132ba-117">=> operator</span></span>](lambda-operator.md)
