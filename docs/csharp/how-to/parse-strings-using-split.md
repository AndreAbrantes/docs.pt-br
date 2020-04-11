---
title: Como analisar strings usando String.Split (Guia C#)
description: O String.Split retorna uma matriz de divisão de cadeias de caracteres com base em um conjunto de delimitadores. Esta á uma maneira fácil de analisar cadeias de caracteres.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: fb11ff59705188f9425beedfbbbf3c244d21f587
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121503"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="d31a0-104">Como analisar strings usando String.Split (Guia C#)</span><span class="sxs-lookup"><span data-stu-id="d31a0-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="d31a0-105">O método <xref:System.String.Split%2A?displayProperty=nameWithType> cria uma matriz de subcadeias, dividindo a cadeia de caracteres de entrada com base em um ou mais delimitadores.</span><span class="sxs-lookup"><span data-stu-id="d31a0-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="d31a0-106">Geralmente essa é a maneira mais fácil de separar uma cadeia de caracteres em limites de palavra.</span><span class="sxs-lookup"><span data-stu-id="d31a0-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="d31a0-107">Ele também é usado para dividir cadeias de caracteres em outros caracteres específicos ou cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d31a0-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d31a0-108">O código a seguir divide uma frase comum em uma matriz de cadeias de caracteres para cada palavra.</span><span class="sxs-lookup"><span data-stu-id="d31a0-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="d31a0-109">Cada instância de um caractere separador produz um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="d31a0-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="d31a0-110">Caracteres separadores consecutivos produzem a cadeia de caracteres vazia como um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="d31a0-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="d31a0-111">Você pode ver isso no exemplo a seguir, que usa espaço como um separador:</span><span class="sxs-lookup"><span data-stu-id="d31a0-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="d31a0-112">Esse comportamento facilita para formatos como arquivos CSV (valores separados por vírgula) que representam dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="d31a0-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="d31a0-113">Vírgulas consecutivas representam uma coluna em branco.</span><span class="sxs-lookup"><span data-stu-id="d31a0-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="d31a0-114">Você pode passar um parâmetro <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> opcional para excluir as cadeias de caracteres vazias da matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="d31a0-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="d31a0-115">Para um processamento mais complicado da coleção retornada, você pode usar o [LINQ](../programming-guide/concepts/linq/index.md) para manipular a sequência de resultado.</span><span class="sxs-lookup"><span data-stu-id="d31a0-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="d31a0-116">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode usar vários caracteres separadores.</span><span class="sxs-lookup"><span data-stu-id="d31a0-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="d31a0-117">O exemplo a seguir utiliza espaços, vírgulas, pontos, dois-pontos e tabulações, todos passados em uma matriz que contém esses caracteres de separação para <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="d31a0-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="d31a0-118">O loop, na parte inferior do código, exibe cada uma das palavras na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="d31a0-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="d31a0-119">As instâncias consecutivas de qualquer separador produzem a cadeia de caracteres vazia na matriz de saída:</span><span class="sxs-lookup"><span data-stu-id="d31a0-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="d31a0-120">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode receber uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).</span><span class="sxs-lookup"><span data-stu-id="d31a0-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="d31a0-121">Você pode experimentar essas amostras olhando para o código em nosso [repositório GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="d31a0-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="d31a0-122">Ou então, você pode baixar os exemplos [como um arquivo zip](../../../samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="d31a0-122">Or you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="d31a0-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="d31a0-123">See also</span></span>

- [<span data-ttu-id="d31a0-124">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="d31a0-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="d31a0-125">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d31a0-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="d31a0-126">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="d31a0-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
