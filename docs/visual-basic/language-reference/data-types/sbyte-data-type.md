---
title: Tipo de Dados SByte
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415564"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="ee5f4-102">Tipo de dados SByte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee5f4-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="ee5f4-103">Mantém números inteiros de 8 bits assinados (1 byte) que variam em valor de-128 até 127.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee5f4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee5f4-104">Remarks</span></span>

<span data-ttu-id="ee5f4-105">Use o `SByte` tipo de dados para conter valores inteiros que não exigem a largura total dos dados de `Integer` ou até a metade da largura de dados de `Short` .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="ee5f4-106">Em alguns casos, a Common Language Runtime pode ser capaz de empacotar suas `SByte` variáveis em conjunto e economizar o consumo de memória.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="ee5f4-107">O valor padrão de `SByte` é 0.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ee5f4-108">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="ee5f4-108">Literal assignments</span></span>

<span data-ttu-id="ee5f4-109">Você pode declarar e inicializar uma `SByte` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="ee5f4-110">No exemplo a seguir, números inteiros iguais a-102 que são representados como decimais, hexadecimais e literais binários são atribuídos a `SByte` valores.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="ee5f4-111">Este exemplo requer que você compile com a `/removeintchecks` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="ee5f4-112">Você usa o prefixo `&h` ou `&H` para denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário, e o prefixo `&o` ou `&O` para indicar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ee5f4-113">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ee5f4-114">A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_` , como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="ee5f4-115">A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado ( `_` ) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ee5f4-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ee5f4-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ee5f4-117">Se o literal inteiro estiver fora do intervalo de `SByte` (ou seja, se for menor que <xref:System.SByte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.SByte.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="ee5f4-118">Quando um inteiro literal não tem nenhum sufixo, um [inteiro](integer-data-type.md) é inferido.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="ee5f4-119">Se o literal inteiro estiver fora do intervalo do `Integer` tipo, um [longo](long-data-type.md) será inferido.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="ee5f4-120">Isso significa que, nos exemplos anteriores, os literais numéricos `0x9A` e `0b10011010` são interpretados como inteiros com sinal de 32 bits com um valor de 156, que excede <xref:System.SByte.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ee5f4-121">Para compilar com êxito um código como esse que atribui um inteiro não decimal a um `SByte` , você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee5f4-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="ee5f4-122">Desabilite as verificações de limites de inteiros compilando com a `/removeintchecks` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="ee5f4-123">Use um [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para definir explicitamente o valor literal que você deseja atribuir ao `SByte` .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="ee5f4-124">O exemplo a seguir atribui um valor literal negativo `Short` a um `SByte` .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="ee5f4-125">Observe que, para números negativos, o bit de ordem superior da palavra de ordem superior do literal numérico deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="ee5f4-126">No caso de nosso exemplo, este é o bit 15 do valor literal `Short` .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="ee5f4-127">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="ee5f4-127">Programming tips</span></span>

- <span data-ttu-id="ee5f4-128">**Conformidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="ee5f4-128">**CLS Compliance.**</span></span> <span data-ttu-id="ee5f4-129">O `SByte` tipo de dados não faz parte do [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto o código em conformidade com CLS não pode consumir um componente que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="ee5f4-130">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="ee5f4-130">**Widening.**</span></span> <span data-ttu-id="ee5f4-131">O `SByte` tipo de dados amplia para `Short` , `Integer` ,,, `Long` `Decimal` `Single` e `Double` .</span><span class="sxs-lookup"><span data-stu-id="ee5f4-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ee5f4-132">Isso significa que você pode converter `SByte` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ee5f4-133">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="ee5f4-133">**Type Characters.**</span></span> <span data-ttu-id="ee5f4-134">`SByte`Não tem caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="ee5f4-135">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="ee5f4-135">**Framework Type.**</span></span> <span data-ttu-id="ee5f4-136">O tipo correspondente no .NET Framework é a estrutura <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee5f4-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee5f4-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee5f4-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="ee5f4-138">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ee5f4-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="ee5f4-139">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="ee5f4-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ee5f4-140">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="ee5f4-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ee5f4-141">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="ee5f4-141">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="ee5f4-142">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="ee5f4-142">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="ee5f4-143">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="ee5f4-143">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="ee5f4-144">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ee5f4-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
