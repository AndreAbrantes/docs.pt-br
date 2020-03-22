---
title: Tipo de Dados Long
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400809"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="5b82a-102">Tipo de dados longos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b82a-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="5b82a-103">Mantém-se assinado 64 bits (8 bytes) inteiros que variam em valor de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2...E+18).</span><span class="sxs-lookup"><span data-stu-id="5b82a-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="5b82a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b82a-104">Remarks</span></span>

<span data-ttu-id="5b82a-105">Use `Long` o tipo de dados para conter números inteiros `Integer` que são muito grandes para se encaixar no tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="5b82a-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="5b82a-106">O valor padrão de `Long` é 0.</span><span class="sxs-lookup"><span data-stu-id="5b82a-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="5b82a-107">Atribuições literais</span><span class="sxs-lookup"><span data-stu-id="5b82a-107">Literal assignments</span></span>

<span data-ttu-id="5b82a-108">Você pode declarar e `Long` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="5b82a-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="5b82a-109">Se o literal inteiro estiver fora do intervalo de `Long` (ou seja, se for menor que <xref:System.Int64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="5b82a-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="5b82a-110">No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `Long`.</span><span class="sxs-lookup"><span data-stu-id="5b82a-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="5b82a-111">Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="5b82a-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5b82a-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="5b82a-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5b82a-113">A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5b82a-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="5b82a-114">Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="5b82a-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5b82a-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="5b82a-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5b82a-116">Literais numéricos `L` também podem incluir `Long` o caractere [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5b82a-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="5b82a-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="5b82a-117">Programming tips</span></span>

- <span data-ttu-id="5b82a-118">**Interop Considerações.**</span><span class="sxs-lookup"><span data-stu-id="5b82a-118">**Interop Considerations.**</span></span> <span data-ttu-id="5b82a-119">Se você estiver interagindo com componentes não gravados para o .NET `Long` Framework, por exemplo Automação ou objetos COM, lembre-se que tem uma largura de dados diferente (32 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="5b82a-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="5b82a-120">Se você estiver passando um argumento de 32 bits para um componente, declare-o como `Integer` em vez de `Long` em seu novo código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b82a-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="5b82a-121">**Alargamento.**</span><span class="sxs-lookup"><span data-stu-id="5b82a-121">**Widening.**</span></span> <span data-ttu-id="5b82a-122">O `Long` tipo de `Decimal`dados `Single`se `Double`expande para, ou .</span><span class="sxs-lookup"><span data-stu-id="5b82a-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="5b82a-123">Isso significa que você pode converter `Long` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b82a-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="5b82a-124">**Digite caracteres.**</span><span class="sxs-lookup"><span data-stu-id="5b82a-124">**Type Characters.**</span></span> <span data-ttu-id="5b82a-125">Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`.</span><span class="sxs-lookup"><span data-stu-id="5b82a-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="5b82a-126">Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="5b82a-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="5b82a-127">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="5b82a-127">**Framework Type.**</span></span> <span data-ttu-id="5b82a-128">O tipo correspondente no .NET Framework é a estrutura <xref:System.Int64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b82a-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b82a-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b82a-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="5b82a-130">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5b82a-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="5b82a-131">Tipo de dados inteiros</span><span class="sxs-lookup"><span data-stu-id="5b82a-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="5b82a-132">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="5b82a-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="5b82a-133">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="5b82a-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5b82a-134">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="5b82a-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="5b82a-135">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5b82a-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
