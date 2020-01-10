---
title: Como executar o código de limpeza usando o C# guia de programação finally
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705269"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="0414a-102">Como executar o código de limpeza usando finallyC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="0414a-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="0414a-103">O propósito de uma instrução `finally` é garantir que a limpeza necessária de objetos, normalmente objetos que estão mantendo recursos externos, ocorra imediatamente, mesmo que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="0414a-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="0414a-104">Um exemplo dessa limpeza é chamar <xref:System.IO.Stream.Close%2A> em um <xref:System.IO.FileStream> imediatamente após o uso, em vez de esperar que o objeto passe pela coleta de lixo feita pelo Common Language Runtime, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0414a-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="0414a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0414a-105">Example</span></span>  
 <span data-ttu-id="0414a-106">Para transformar o código anterior em uma instrução `try-catch-finally`, o código de limpeza é separado do código funcional, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="0414a-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="0414a-107">Como uma exceção pode ocorrer a qualquer momento no bloco `try` antes da chamada `OpenWrite()` ou a própria chamada `OpenWrite()` poderia falhar, não há garantia de que o arquivo esteja aberto ao tentarmos fechá-lo.</span><span class="sxs-lookup"><span data-stu-id="0414a-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="0414a-108">O bloco `finally` adiciona uma verificação para verificar se o objeto <xref:System.IO.FileStream> não é `null` antes de chamar o método <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="0414a-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="0414a-109">Sem a verificação de `null`, o bloco `finally` poderia lançar sua própria <xref:System.NullReferenceException>, mas o lançamento de exceções em blocos `finally` deve ser evitado, se possível.</span><span class="sxs-lookup"><span data-stu-id="0414a-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="0414a-110">Uma conexão de banco de dados é outra boa candidata a ser fechada em um bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="0414a-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="0414a-111">Como o número de conexões permitidas para um servidor de banco de dados é, às vezes, limitado, você deve fechar conexões de banco de dados assim que possível.</span><span class="sxs-lookup"><span data-stu-id="0414a-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="0414a-112">Se uma exceção for lançada antes de fechar a conexão, este seria outro caso em que o uso do bloco `finally` é melhor que esperar pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0414a-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0414a-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="0414a-113">See also</span></span>

- [<span data-ttu-id="0414a-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0414a-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0414a-115">Exceções e manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="0414a-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="0414a-116">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="0414a-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="0414a-117">Instrução using</span><span class="sxs-lookup"><span data-stu-id="0414a-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="0414a-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="0414a-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="0414a-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="0414a-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="0414a-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="0414a-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
