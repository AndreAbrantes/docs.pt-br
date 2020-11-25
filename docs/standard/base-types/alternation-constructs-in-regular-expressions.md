---
title: Constructos de alternância em expressões regulares do .NET
description: Saiba como usar constructos de alternância para a correspondência condicional em expressões regulares.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 0a1b46443d5cd9f8a19f4cfb9f9b07a5e33e719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714686"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="c2834-103">Construtores de alternância em expressões regulares</span><span class="sxs-lookup"><span data-stu-id="c2834-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="c2834-104">Os constructos de alternância modificam uma expressão regular para permitir uma correspondência condicional ou do tipo um/ou outro.</span><span class="sxs-lookup"><span data-stu-id="c2834-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="c2834-105">O .NET dá suporte a três constructos de alternância:</span><span class="sxs-lookup"><span data-stu-id="c2834-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="c2834-106">Correspondência de padrões com &#124;</span><span class="sxs-lookup"><span data-stu-id="c2834-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="c2834-107">Correspondência condicional com (?(expression)yes&#124;no)</span><span class="sxs-lookup"><span data-stu-id="c2834-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="c2834-108">Correspondência condicional com base em um grupo capturado válido</span><span class="sxs-lookup"><span data-stu-id="c2834-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>

## <a name="pattern-matching-with-124"></a><span data-ttu-id="c2834-109">Correspondência de padrões com &#124;</span><span class="sxs-lookup"><span data-stu-id="c2834-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="c2834-110">Você pode usar o caractere de barra vertical (`|`) para corresponder a qualquer um de uma série de padrões, no qual o caractere `|` separa cada padrão.</span><span class="sxs-lookup"><span data-stu-id="c2834-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="c2834-111">Como a classe de caracteres positivos, o caractere `|` pode ser usado para corresponder a qualquer um de vários caracteres únicos.</span><span class="sxs-lookup"><span data-stu-id="c2834-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="c2834-112">O exemplo a seguir usa uma classe de caracteres positivos e um padrão do tipo um/ou outro correspondendo ao caractere `|` para localizar ocorrências das palavras “gray” ou “grey” em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c2834-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="c2834-113">Nesse caso, o caractere `|` produz uma expressão regular que é mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="c2834-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="c2834-114">A expressão regular que usa o `|` caractere, `\bgr(a|e)y\b` , é interpretada conforme mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2834-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="c2834-115">Padrão</span><span class="sxs-lookup"><span data-stu-id="c2834-115">Pattern</span></span>|<span data-ttu-id="c2834-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2834-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c2834-117">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="c2834-118">Corresponder aos caracteres "gr".</span><span class="sxs-lookup"><span data-stu-id="c2834-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="c2834-119">Corresponder a um "a" ou "e".</span><span class="sxs-lookup"><span data-stu-id="c2834-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="c2834-120">Corresponder a um “y” em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="c2834-121">O caractere `|` também pode ser usado para executar uma correspondência do tipo um/ou outro com vários caracteres ou subexpressões, que podem incluir qualquer combinação de literais de caracteres e elementos de linguagem de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="c2834-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="c2834-122">(A classe Character não fornece essa funcionalidade.) O exemplo a seguir usa o `|` caractere para extrair um número de previdência social (SSN) dos EUA, que é um número de 9 dígitos com o formato *DDD* - *DD* - *dddd* ou um número de identificação de empregador dos EUA (Ein), que é um número de 9 dígitos com o formato *DD* - *ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="c2834-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="c2834-123">A expressão regular `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretada conforme mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2834-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="c2834-124">Padrão</span><span class="sxs-lookup"><span data-stu-id="c2834-124">Pattern</span></span>|<span data-ttu-id="c2834-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2834-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c2834-126">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="c2834-127">Corresponde a uma das seguintes opções: dois dígitos decimais seguidos por um hífen seguido por sete dígitos decimais ou três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="c2834-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c2834-128">Termina a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>

## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="c2834-129">Correspondência condicional com uma expressão</span><span class="sxs-lookup"><span data-stu-id="c2834-129">Conditional matching with an expression</span></span>

<span data-ttu-id="c2834-130">Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele pode corresponder a um padrão inicial.</span><span class="sxs-lookup"><span data-stu-id="c2834-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="c2834-131">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="c2834-131">Its syntax is:</span></span>  

<span data-ttu-id="c2834-132">`(?(`*expressão* `)` de *Sim* `|` *não*`)`</span><span class="sxs-lookup"><span data-stu-id="c2834-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="c2834-133">em que *expressão* é o padrão inicial para corresponder *, sim* é o padrão para corresponder se a *expressão* for correspondida e *não* for o padrão opcional para corresponder se a *expressão* não for correspondida.</span><span class="sxs-lookup"><span data-stu-id="c2834-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="c2834-134">O mecanismo de expressões regulares trata a *expressão* como uma asserção de largura zero, isto é, o mecanismo de expressões regulares não avança no fluxo de entrada após avaliar a *expressão*.</span><span class="sxs-lookup"><span data-stu-id="c2834-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="c2834-135">Portanto, esse constructo é equivalente ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2834-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="c2834-136">`(?(?=`*expressão* `)` de *Sim* `|` *não*`)`</span><span class="sxs-lookup"><span data-stu-id="c2834-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="c2834-137">`(?=` *expressão* Where `)` é uma construção de asserção de largura zero.</span><span class="sxs-lookup"><span data-stu-id="c2834-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="c2834-138">(Para obter mais informações, consulte [agrupando construções](grouping-constructs-in-regular-expressions.md).) Como o mecanismo de expressões regulares interpreta a *expressão* como uma âncora (uma declaração de largura zero), a *expressão* deve ser uma asserção de largura zero (para obter mais informações, consulte [âncoras](anchors-in-regular-expressions.md)) ou uma subexpressão que também esteja contida em *Sim*.</span><span class="sxs-lookup"><span data-stu-id="c2834-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="c2834-139">Caso contrário, o padrão *sim* não pode ser correspondido.</span><span class="sxs-lookup"><span data-stu-id="c2834-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2834-140">Se *expression* for um grupo de captura nomeado ou numerado, o constructo de alternância será interpretado como um teste de captura; para obter mais informações, consulte a próxima seção, [correspondência condicional com base em um grupo de captura válido](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="c2834-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="c2834-141">Em outras palavras, o mecanismo de expressões regulares não tenta corresponder a subcadeia de caracteres capturada, mas em vez disso, testa a presença ou ausência do grupo.</span><span class="sxs-lookup"><span data-stu-id="c2834-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="c2834-142">O exemplo a seguir é uma variação do exemplo que aparece na seção [E/Ou Correspondência de Padrões com &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="c2834-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c2834-143">Ele usa a correspondência condicional para determinar se os três primeiros caracteres após um limite de palavra são dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="c2834-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="c2834-144">Se estiverem, ele tentará corresponder a um número de identificação do empregador (EIN) dos EUA.</span><span class="sxs-lookup"><span data-stu-id="c2834-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c2834-145">Caso contrário, ele tentará corresponder a um número de seguro social (SSN) dos EUA.</span><span class="sxs-lookup"><span data-stu-id="c2834-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="c2834-146">O padrão de expressão regular `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2834-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="c2834-147">Padrão</span><span class="sxs-lookup"><span data-stu-id="c2834-147">Pattern</span></span>|<span data-ttu-id="c2834-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2834-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c2834-149">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="c2834-150">Determinar se os próximos três caracteres são compostos por dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="c2834-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="c2834-151">Se o padrão anterior corresponder, corresponder a dois dígitos seguidos por um hífen seguido por sete dígitos.</span><span class="sxs-lookup"><span data-stu-id="c2834-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="c2834-152">Se o padrão anterior não corresponder, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="c2834-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c2834-153">Corresponder a um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>

## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="c2834-154">Correspondência condicional com base em um grupo capturado válido</span><span class="sxs-lookup"><span data-stu-id="c2834-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="c2834-155">Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele correspondeu a um grupo de captura especificado.</span><span class="sxs-lookup"><span data-stu-id="c2834-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="c2834-156">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="c2834-156">Its syntax is:</span></span>

<span data-ttu-id="c2834-157">`(?(` *nome* `)` *sim* `|` *não* `)`</span><span class="sxs-lookup"><span data-stu-id="c2834-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="c2834-158">ou</span><span class="sxs-lookup"><span data-stu-id="c2834-158">or</span></span>

<span data-ttu-id="c2834-159">`(?(`*número* `)` de *Sim* `|` *não*`)`</span><span class="sxs-lookup"><span data-stu-id="c2834-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="c2834-160">em que *Name* é o nome e o *número* é o número de um grupo de captura, *Sim* é a expressão a ser correspondida se o *nome* ou o *número* tiver uma correspondência e *não* for a expressão opcional para corresponder se não tiver.</span><span class="sxs-lookup"><span data-stu-id="c2834-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="c2834-161">Se *name* não corresponder ao nome de um grupo de captura que é usado no padrão de expressão regular, o constructo de alternância será interpretado como teste de expressão, conforme explicado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="c2834-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="c2834-162">Normalmente, isso significa que a *expressão* é avaliada como `false` .</span><span class="sxs-lookup"><span data-stu-id="c2834-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="c2834-163">Se *number* não corresponder a um grupo de captura numerado que é usado no padrão de expressão regular, o mecanismo de expressões regulares gerará um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c2834-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="c2834-164">O exemplo a seguir é uma variação do exemplo que aparece na seção [E/Ou Correspondência de Padrões com &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="c2834-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c2834-165">Ele usa um grupo de captura chamado `n2` que consiste em dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="c2834-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="c2834-166">O constructo de alternância testa se este grupo de captura foi correspondido na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="c2834-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="c2834-167">Se tiver, a construção de alternância tentará corresponder aos últimos sete dígitos de um número de identificação de empregador (EIN) de nove dígitos.</span><span class="sxs-lookup"><span data-stu-id="c2834-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c2834-168">Se não tiver, ele tentará corresponder a um número de seguro social (SSN) de nove dígitos.</span><span class="sxs-lookup"><span data-stu-id="c2834-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="c2834-169">O padrão de expressão regular `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2834-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="c2834-170">Padrão</span><span class="sxs-lookup"><span data-stu-id="c2834-170">Pattern</span></span>|<span data-ttu-id="c2834-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2834-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c2834-172">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="c2834-173">Corresponder a zero ou uma ocorrência de dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="c2834-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="c2834-174">Atribua um nome ao grupo de captura `n2`.</span><span class="sxs-lookup"><span data-stu-id="c2834-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="c2834-175">Testar se `n2` foi correspondido na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="c2834-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="c2834-176">Se `n2` tiver sido correspondido, corresponder a sete dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="c2834-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="c2834-177">Se `n2` não tiver sido correspondido, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="c2834-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c2834-178">Corresponder a um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="c2834-178">Match a word boundary.</span></span>|  

<span data-ttu-id="c2834-179">Uma variação desse exemplo que usa um grupo numerado em vez de um grupo nomeado é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2834-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="c2834-180">O padrão da expressão regular é `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="c2834-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="c2834-181">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2834-181">See also</span></span>

- [<span data-ttu-id="c2834-182">Linguagem de expressões regulares – referência rápida</span><span class="sxs-lookup"><span data-stu-id="c2834-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
