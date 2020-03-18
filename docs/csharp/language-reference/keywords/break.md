---
title: Instrução break – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713760"
---
# <a name="break-c-reference"></a><span data-ttu-id="4bfad-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4bfad-102">break (C# Reference)</span></span>

<span data-ttu-id="4bfad-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](./switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4bfad-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="4bfad-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="4bfad-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="4bfad-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bfad-105">Example</span></span>

<span data-ttu-id="4bfad-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="4bfad-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="4bfad-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bfad-107">Example</span></span>

<span data-ttu-id="4bfad-108">Este exemplo demonstra o uso de `break` em uma instrução [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="4bfad-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="4bfad-109">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="4bfad-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="4bfad-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bfad-110">Example</span></span>

<span data-ttu-id="4bfad-111">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="4bfad-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="4bfad-112">O controle _só_ é devolvido um nível acima nos loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="4bfad-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="4bfad-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bfad-113">Example</span></span>

<span data-ttu-id="4bfad-114">Neste exemplo, `break` a declaração só é usada para sair do ramo atual durante cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="4bfad-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="4bfad-115">O loop em si não `break` é afetado pelas instâncias que pertencem à declaração de [switch](./switch.md) aninhada.</span><span class="sxs-lookup"><span data-stu-id="4bfad-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="4bfad-116">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4bfad-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4bfad-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="4bfad-117">See also</span></span>

- [<span data-ttu-id="4bfad-118">C# Referência</span><span class="sxs-lookup"><span data-stu-id="4bfad-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4bfad-119">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="4bfad-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4bfad-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4bfad-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4bfad-121">Interruptor</span><span class="sxs-lookup"><span data-stu-id="4bfad-121">switch</span></span>](./switch.md)
