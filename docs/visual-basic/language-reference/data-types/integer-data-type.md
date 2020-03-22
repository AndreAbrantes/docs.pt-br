---
title: Tipo de Dados Integer
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400732"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="9d5cc-102">Tipo de dados inteiros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d5cc-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="9d5cc-103">Armazena inteiros de 32 bits (4 bytes) com sinal que variam em valor de -2.147.483.648 a 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d5cc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d5cc-104">Remarks</span></span>

 <span data-ttu-id="9d5cc-105">O tipo de dados `Integer` proporciona um desempenho ideal em um processador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="9d5cc-106">Os outros tipos integrais são mais lentos para carregar e armazenar na memória.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="9d5cc-107">O valor padrão de `Integer` é 0.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="9d5cc-108">Atribuições literais</span><span class="sxs-lookup"><span data-stu-id="9d5cc-108">Literal assignments</span></span>

<span data-ttu-id="9d5cc-109">Você pode declarar e `Integer` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9d5cc-110">Se o literal inteiro estiver fora do intervalo de `Integer` (ou seja, se for menor que <xref:System.Int32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int32.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9d5cc-111">No exemplo a seguir, inteiros iguais a 90.946 representados como literais decimais, hexadecimais e binários são atribuídos a valores `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="9d5cc-112">Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9d5cc-113">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9d5cc-114">A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="9d5cc-115">Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9d5cc-116">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="9d5cc-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9d5cc-117">Literais numéricos `I` também podem incluir `Integer` o caractere [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="9d5cc-118">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="9d5cc-118">Programming tips</span></span>

- <span data-ttu-id="9d5cc-119">**Interop Considerações.**</span><span class="sxs-lookup"><span data-stu-id="9d5cc-119">**Interop Considerations.**</span></span> <span data-ttu-id="9d5cc-120">Se você estiver interagindo com componentes não gravados para o .NET `Integer` Framework, como automação ou objetos COM, lembre-se que tem uma largura de dados diferente (16 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="9d5cc-121">Se você estiver passando um argumento de 16 bits para esse componente, declare-o como `Short` em vez de `Integer` no seu novo código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="9d5cc-122">**Alargamento.**</span><span class="sxs-lookup"><span data-stu-id="9d5cc-122">**Widening.**</span></span> <span data-ttu-id="9d5cc-123">O tipo de dados `Integer` é ampliado para `Long`, `Decimal`, `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9d5cc-124">Isso significa que você pode converter `Integer` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="9d5cc-125">**Digite caracteres.**</span><span class="sxs-lookup"><span data-stu-id="9d5cc-125">**Type Characters.**</span></span> <span data-ttu-id="9d5cc-126">Acrescentar o caractere de tipo literal `I` a um literal o força ao tipo de dados `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="9d5cc-127">Acrescentar o caractere de tipo identificador `%` a qualquer identificador o força ao tipo `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="9d5cc-128">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="9d5cc-128">**Framework Type.**</span></span> <span data-ttu-id="9d5cc-129">O tipo correspondente no .NET Framework é a estrutura <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="9d5cc-130">Intervalo</span><span class="sxs-lookup"><span data-stu-id="9d5cc-130">Range</span></span>

<span data-ttu-id="9d5cc-131">Se você tentar definir uma variável de um tipo integral para um número fora do intervalo para esse tipo, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="9d5cc-132">Se você tentar defini-lo como uma fração, o número será arredondado para cima ou para baixo para o valor inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="9d5cc-133">Se o número for igualmente próximo de dois valores inteiros, o valor será arredondado para o inteiro par mais próximo.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="9d5cc-134">Esse comportamento minimiza erros de arredondamento gerados ao arredondar consistentemente um valor de ponto médio em uma única direção.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="9d5cc-135">O código a seguir mostra exemplos de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="9d5cc-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d5cc-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="9d5cc-137">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="9d5cc-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="9d5cc-138">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="9d5cc-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="9d5cc-139">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="9d5cc-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="9d5cc-140">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="9d5cc-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9d5cc-141">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="9d5cc-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="9d5cc-142">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="9d5cc-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
