---
title: Como lançar exceções explicitamente
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708856"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="bc7f1-102">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="bc7f1-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="bc7f1-103">Você pode explicitamente lançar uma exceção usando o C# [`throw`](../../csharp/language-reference/keywords/throw.md) ou a instrução Visual Basic. [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f1-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="bc7f1-104">Você também pode lançar novamente uma exceção capturada usando a instrução `throw`.</span><span class="sxs-lookup"><span data-stu-id="bc7f1-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="bc7f1-105">É uma boa prática adicionar informações a uma exceção que é lançada novamente para fornecer mais informações durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="bc7f1-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="bc7f1-106">O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma possível <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="bc7f1-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="bc7f1-107">Após o bloco `try`, há um bloco `catch` que captura a <xref:System.IO.FileNotFoundException> e grava uma mensagem no console se o arquivo de dados não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="bc7f1-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="bc7f1-108">A próxima instrução é a instrução `throw`, que gera uma nova <xref:System.IO.FileNotFoundException> e adiciona informações de texto à exceção.</span><span class="sxs-lookup"><span data-stu-id="bc7f1-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="bc7f1-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc7f1-109">See also</span></span>

- [<span data-ttu-id="bc7f1-110">Exceções</span><span class="sxs-lookup"><span data-stu-id="bc7f1-110">Exceptions</span></span>](index.md)
