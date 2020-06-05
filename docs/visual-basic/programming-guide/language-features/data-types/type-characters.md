---
title: Caracteres de tipo
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393072"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="4e410-102">Caracteres de tipo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e410-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="4e410-103">Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação com um *caractere de tipo*.</span><span class="sxs-lookup"><span data-stu-id="4e410-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="4e410-104">O caractere de tipo deve seguir imediatamente o elemento, sem nenhum tipo de caracteres intermediários.</span><span class="sxs-lookup"><span data-stu-id="4e410-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="4e410-105">O caractere de tipo não faz parte do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="4e410-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="4e410-106">Um elemento definido com um caractere de tipo pode ser referenciado sem o caractere de tipo.</span><span class="sxs-lookup"><span data-stu-id="4e410-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="4e410-107">Caracteres do tipo identificador</span><span class="sxs-lookup"><span data-stu-id="4e410-107">Identifier type characters</span></span>

<span data-ttu-id="4e410-108">O Visual Basic fornece um conjunto de *caracteres de tipo de identificador* que você pode usar em uma declaração para especificar o tipo de dados de uma variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="4e410-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="4e410-109">A tabela a seguir mostra os caracteres de tipo de identificador disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="4e410-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="4e410-110">Caractere de tipo de identificador</span><span class="sxs-lookup"><span data-stu-id="4e410-110">Identifier type character</span></span>|<span data-ttu-id="4e410-111">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="4e410-111">Data type</span></span>|<span data-ttu-id="4e410-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e410-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="4e410-113">Não existem caracteres de tipo de identificador para os tipos de dados,,,,,,,, `Boolean` `Byte` `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` ou `UShort` para quaisquer tipos de dados compostos, como matrizes ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="4e410-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="4e410-114">Em alguns casos, você pode acrescentar o `$` caractere a uma função Visual Basic, por exemplo, `Left$` em vez de `Left` , para obter um valor retornado do tipo `String` .</span><span class="sxs-lookup"><span data-stu-id="4e410-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="4e410-115">Em todos os casos, o caractere de tipo de identificador deve seguir imediatamente o nome do identificador.</span><span class="sxs-lookup"><span data-stu-id="4e410-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="4e410-116">Caracteres do tipo literal</span><span class="sxs-lookup"><span data-stu-id="4e410-116">Literal type characters</span></span>

<span data-ttu-id="4e410-117">Um *literal* é uma representação textual de um valor específico de um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4e410-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="4e410-118">Tipos literais padrão</span><span class="sxs-lookup"><span data-stu-id="4e410-118">Default literal types</span></span>

<span data-ttu-id="4e410-119">A forma de um literal como ele aparece em seu código normalmente determina seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4e410-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="4e410-120">A tabela a seguir mostra esses tipos padrão.</span><span class="sxs-lookup"><span data-stu-id="4e410-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="4e410-121">Forma textual de literal</span><span class="sxs-lookup"><span data-stu-id="4e410-121">Textual form of literal</span></span>|<span data-ttu-id="4e410-122">Tipo de dados padrão</span><span class="sxs-lookup"><span data-stu-id="4e410-122">Default data type</span></span>|<span data-ttu-id="4e410-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e410-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="4e410-124">Numeric, sem parte fracionária</span><span class="sxs-lookup"><span data-stu-id="4e410-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="4e410-125">Numeric, sem parte fracionária, muito grande para`Integer`</span><span class="sxs-lookup"><span data-stu-id="4e410-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="4e410-126">Parte numérica, fracionária</span><span class="sxs-lookup"><span data-stu-id="4e410-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="4e410-127">Entre aspas duplas</span><span class="sxs-lookup"><span data-stu-id="4e410-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="4e410-128">Entre sinais de número</span><span class="sxs-lookup"><span data-stu-id="4e410-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="4e410-129">Tipos literais forçados</span><span class="sxs-lookup"><span data-stu-id="4e410-129">Forced literal types</span></span>

<span data-ttu-id="4e410-130">Visual Basic fornece um conjunto de *caracteres de tipo literal*, que você pode usar para forçar um literal a assumir um tipo de dados diferente daquele que seu formulário indica.</span><span class="sxs-lookup"><span data-stu-id="4e410-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="4e410-131">Você faz isso acrescentando o caractere ao final do literal.</span><span class="sxs-lookup"><span data-stu-id="4e410-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="4e410-132">A tabela a seguir mostra os caracteres de tipo literal disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="4e410-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="4e410-133">Caractere de tipo literal</span><span class="sxs-lookup"><span data-stu-id="4e410-133">Literal type character</span></span>|<span data-ttu-id="4e410-134">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="4e410-134">Data type</span></span>|<span data-ttu-id="4e410-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e410-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="4e410-136">Não existem caracteres de tipo literal para os tipos de dados,,,, `Boolean` `Byte` `Date` `Object` `SByte` ou `String` para quaisquer tipos de dados compostos, como matrizes ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="4e410-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="4e410-137">Os literais também podem usar os caracteres de tipo de identificador (,,,, `%` `&` `@` `!` `#` , `$` ), como variáveis, constantes e expressões.</span><span class="sxs-lookup"><span data-stu-id="4e410-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="4e410-138">No entanto, os caracteres do tipo literal (,,,,, `S` `I` `L` `D` `F` `R` , `C` ) podem ser usados somente com literais.</span><span class="sxs-lookup"><span data-stu-id="4e410-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="4e410-139">Em todos os casos, o caractere de tipo literal deve seguir imediatamente o valor literal.</span><span class="sxs-lookup"><span data-stu-id="4e410-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="4e410-140">Literais hexadecimais, binários e octais</span><span class="sxs-lookup"><span data-stu-id="4e410-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="4e410-141">Normalmente, o compilador interpreta um inteiro literal para estar no sistema numérico decimal (base 10).</span><span class="sxs-lookup"><span data-stu-id="4e410-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="4e410-142">Você também pode definir um literal inteiro como um número hexadecimal (base 16) com o `&H` prefixo, como um número binário (base 2) com o `&B` prefixo, e como um número octal (base 8) com o `&O` prefixo.</span><span class="sxs-lookup"><span data-stu-id="4e410-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="4e410-143">Os dígitos que seguem o prefixo devem ser apropriados para o sistema numérico.</span><span class="sxs-lookup"><span data-stu-id="4e410-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="4e410-144">A tabela a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="4e410-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="4e410-145">Base do número</span><span class="sxs-lookup"><span data-stu-id="4e410-145">Number base</span></span>|<span data-ttu-id="4e410-146">Prefixo</span><span class="sxs-lookup"><span data-stu-id="4e410-146">Prefix</span></span>|<span data-ttu-id="4e410-147">Valores de dígito válidos</span><span class="sxs-lookup"><span data-stu-id="4e410-147">Valid digit values</span></span>|<span data-ttu-id="4e410-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e410-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="4e410-149">Hexadecimal (base 16)</span><span class="sxs-lookup"><span data-stu-id="4e410-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="4e410-150">0-9 e A-F</span><span class="sxs-lookup"><span data-stu-id="4e410-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="4e410-151">Binary (base 2)</span><span class="sxs-lookup"><span data-stu-id="4e410-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="4e410-152">0-1</span><span class="sxs-lookup"><span data-stu-id="4e410-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="4e410-153">Octal (base 8)</span><span class="sxs-lookup"><span data-stu-id="4e410-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="4e410-154">0-7</span><span class="sxs-lookup"><span data-stu-id="4e410-154">0-7</span></span>|`&O77`|

<span data-ttu-id="4e410-155">A partir do Visual Basic 2017, você pode usar o caractere de sublinhado ( `_` ) como um separador de grupo para melhorar a legibilidade de um literal integral.</span><span class="sxs-lookup"><span data-stu-id="4e410-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="4e410-156">O exemplo a seguir usa o `_` caractere para agrupar um literal binário em grupos de 8 bits:</span><span class="sxs-lookup"><span data-stu-id="4e410-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="4e410-157">Você pode seguir um literal prefixado com um caractere de tipo literal.</span><span class="sxs-lookup"><span data-stu-id="4e410-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="4e410-158">O exemplo a seguir mostra a isso.</span><span class="sxs-lookup"><span data-stu-id="4e410-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="4e410-159">No exemplo anterior, `counter` tem o valor decimal de-32768 e `flags` tem o valor decimal de + 32768.</span><span class="sxs-lookup"><span data-stu-id="4e410-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="4e410-160">A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado ( `_` ) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="4e410-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4e410-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4e410-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="4e410-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e410-162">See also</span></span>

- [<span data-ttu-id="4e410-163">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="4e410-163">Data Types</span></span>](index.md)
- [<span data-ttu-id="4e410-164">Tipos de dados elementares</span><span class="sxs-lookup"><span data-stu-id="4e410-164">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="4e410-165">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="4e410-165">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="4e410-166">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e410-166">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="4e410-167">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="4e410-167">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="4e410-168">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="4e410-168">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="4e410-169">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="4e410-169">Data Types</span></span>](../../../language-reference/data-types/index.md)
