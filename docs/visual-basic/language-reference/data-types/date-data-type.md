---
title: Tipo de Dados de Data
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 46c25e14db56d4cc3c6d59ec7649b37c35676e2e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387420"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="10681-102">Tipo de dados Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10681-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="10681-103">Mantém os valores do IEEE 64 bits (8 bytes) que representam datas desde 1º de Janeiro do ano de 0001 até 31 de dezembro do ano 9999 e horas da 12:00:00 AM (meia-noite) até 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="10681-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="10681-104">Cada incremento representa 100 nanossegundos de tempo decorrido desde o início de 1º de Janeiro do ano 1 no calendário gregoriano.</span><span class="sxs-lookup"><span data-stu-id="10681-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="10681-105">O valor máximo representa 100 nanossegundos antes do início de 1º de Janeiro do ano 10000.</span><span class="sxs-lookup"><span data-stu-id="10681-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="10681-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="10681-106">Remarks</span></span>

<span data-ttu-id="10681-107">Use o `Date` tipo de dados para conter valores de data, valores de tempo ou valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="10681-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="10681-108">O valor padrão de `Date` é 0:00:00 (meia-noite) em 1º de janeiro de 0001.</span><span class="sxs-lookup"><span data-stu-id="10681-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="10681-109">Você pode obter a data e a hora atuais da <xref:Microsoft.VisualBasic.DateAndTime> classe.</span><span class="sxs-lookup"><span data-stu-id="10681-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="10681-110">Requisitos de formato</span><span class="sxs-lookup"><span data-stu-id="10681-110">Format Requirements</span></span>

<span data-ttu-id="10681-111">Você deve colocar um `Date` literal dentro de sinais numéricos ( `# #` ).</span><span class="sxs-lookup"><span data-stu-id="10681-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="10681-112">Você deve especificar o valor de data no formato M/d/AAAA, por exemplo `#5/31/1993#` , ou aaaa-mm-dd, por exemplo `#1993-5-31#` .</span><span class="sxs-lookup"><span data-stu-id="10681-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="10681-113">Você pode usar barras ao especificar o ano primeiro.</span><span class="sxs-lookup"><span data-stu-id="10681-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="10681-114">Esse requisito é independente da sua localidade e das configurações de data e formato de hora do computador.</span><span class="sxs-lookup"><span data-stu-id="10681-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="10681-115">O motivo para essa restrição é que o significado do seu código nunca deve ser alterado dependendo da localidade em que seu aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="10681-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="10681-116">Suponha que você codifique um `Date` literal de `#3/4/1998#` e pretenda que ele signifique 4 de março de 1998.</span><span class="sxs-lookup"><span data-stu-id="10681-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="10681-117">Em uma localidade que usa mm/dd/aaaa, o 3/4/1998 é compilado como pretendido.</span><span class="sxs-lookup"><span data-stu-id="10681-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="10681-118">Mas suponha que você implante seu aplicativo em muitos países/regiões.</span><span class="sxs-lookup"><span data-stu-id="10681-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="10681-119">Em uma localidade que usa dd/mm/aaaa, seu literal embutido em código seria compilado em 3 de abril de 1998.</span><span class="sxs-lookup"><span data-stu-id="10681-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="10681-120">Em uma localidade que usa aaaa/mm/dd, o literal seria inválido (abril de 1998, 0003) e causa um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="10681-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="10681-121">Soluções Alternativas</span><span class="sxs-lookup"><span data-stu-id="10681-121">Workarounds</span></span>

<span data-ttu-id="10681-122">Para converter um `Date` literal para o formato de sua localidade, ou para um formato personalizado, forneça o literal para a <xref:Microsoft.VisualBasic.Strings.Format%2A> função, especificando um formato de data predefinido ou definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="10681-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="10681-123">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="10681-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="10681-124">Como alternativa, você pode usar um dos construtores sobrecarregados da <xref:System.DateTime> estrutura para montar um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="10681-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="10681-125">O exemplo a seguir cria um valor para representar 31 de maio de 1993 às 12:14 na tarde.</span><span class="sxs-lookup"><span data-stu-id="10681-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="10681-126">Formato de hora</span><span class="sxs-lookup"><span data-stu-id="10681-126">Hour Format</span></span>

<span data-ttu-id="10681-127">Você pode especificar o valor de hora em formato de 12 horas ou 24 horas, por exemplo, `#1:15:30 PM#` ou `#13:15:30#` .</span><span class="sxs-lookup"><span data-stu-id="10681-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="10681-128">No entanto, se você não especificar os minutos ou os segundos, deverá especificar AM ou PM.</span><span class="sxs-lookup"><span data-stu-id="10681-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="10681-129">Padrões de data e hora</span><span class="sxs-lookup"><span data-stu-id="10681-129">Date and Time Defaults</span></span>

<span data-ttu-id="10681-130">Se você não incluir uma data em um literal de data/hora, Visual Basic definirá a parte de data do valor como 1º de janeiro de 0001.</span><span class="sxs-lookup"><span data-stu-id="10681-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="10681-131">Se você não incluir uma hora em um literal de data/hora, Visual Basic definirá a parte de hora do valor como o início do dia, ou seja, meia-noite (0:00:00).</span><span class="sxs-lookup"><span data-stu-id="10681-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="10681-132">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="10681-132">Type Conversions</span></span>

<span data-ttu-id="10681-133">Se você converter um `Date` valor para o `String` tipo, o Visual Basic renderiza a data de acordo com o formato de data abreviada especificado pela localidade de tempo de execução e renderiza a hora de acordo com o formato de hora (12 horas ou 24 horas) especificado pela localidade de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="10681-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="10681-134">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="10681-134">Programming Tips</span></span>

- <span data-ttu-id="10681-135">**Considerações sobre interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="10681-135">**Interop Considerations.**</span></span> <span data-ttu-id="10681-136">Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, tenha em mente que os tipos de data/hora em outros ambientes não são compatíveis com o tipo de Visual Basic `Date` .</span><span class="sxs-lookup"><span data-stu-id="10681-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="10681-137">Se você estiver passando um argumento de data/hora para esse componente, declare- `Double` o como em vez de `Date` em seu novo código de Visual Basic e use os métodos de conversão <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> e <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="10681-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="10681-138">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="10681-138">**Type Characters.**</span></span> <span data-ttu-id="10681-139">`Date`Não tem caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="10681-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="10681-140">No entanto, o compilador trata literais delimitados entre sinais numéricos ( `# #` ) como `Date` .</span><span class="sxs-lookup"><span data-stu-id="10681-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="10681-141">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="10681-141">**Framework Type.**</span></span> <span data-ttu-id="10681-142">O tipo correspondente no .NET Framework é a estrutura <xref:System.DateTime?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10681-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="10681-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10681-143">Example</span></span>

<span data-ttu-id="10681-144">Uma variável ou constante do `Date` tipo de dados contém a data e a hora.</span><span class="sxs-lookup"><span data-stu-id="10681-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="10681-145">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="10681-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="10681-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="10681-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="10681-147">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="10681-147">Data Types</span></span>](index.md)
- [<span data-ttu-id="10681-148">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="10681-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="10681-149">Cadeias de caracteres de formato de data e hora personalizadas</span><span class="sxs-lookup"><span data-stu-id="10681-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="10681-150">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="10681-150">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="10681-151">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="10681-151">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="10681-152">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="10681-152">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
