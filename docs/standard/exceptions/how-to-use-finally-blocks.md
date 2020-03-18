---
title: Como usar blocos finally
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708826"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="990eb-102">Como usar blocos finally</span><span class="sxs-lookup"><span data-stu-id="990eb-102">How to use finally blocks</span></span>

<span data-ttu-id="990eb-103">Quando ocorre uma exceção, a execução é interrompida e o controle é dado ao manipulador de exceção apropriado.</span><span class="sxs-lookup"><span data-stu-id="990eb-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="990eb-104">Geralmente, isso significa que linhas de código que você espera que sejam executadas são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="990eb-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="990eb-105">A limpeza de alguns recursos, assim como o fechamento de um arquivo, precisará ser feita mesmo se uma exceção for gerada.</span><span class="sxs-lookup"><span data-stu-id="990eb-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="990eb-106">Para fazer isso, você pode usar um bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="990eb-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="990eb-107">Um bloco `finally` sempre é executado, independentemente de uma exceção ser ou não gerada.</span><span class="sxs-lookup"><span data-stu-id="990eb-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="990eb-108">O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="990eb-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="990eb-109">O método `Main` cria duas matrizes e tenta copiar uma para a outra.</span><span class="sxs-lookup"><span data-stu-id="990eb-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="990eb-110">A ação gera um <xref:System.ArgumentOutOfRangeException> e o erro é gravado no console.</span><span class="sxs-lookup"><span data-stu-id="990eb-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="990eb-111">Este bloco `finally` é executado independentemente resultado da ação de cópia.</span><span class="sxs-lookup"><span data-stu-id="990eb-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="990eb-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="990eb-112">See also</span></span>

- [<span data-ttu-id="990eb-113">Exceções</span><span class="sxs-lookup"><span data-stu-id="990eb-113">Exceptions</span></span>](index.md)
