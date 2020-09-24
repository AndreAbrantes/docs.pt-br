---
title: Literais (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 4402f4c6ee38432a0f606e39dd4a18639076ce04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161770"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="192c5-102">Literais (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="192c5-102">Literals (Entity SQL)</span></span>

<span data-ttu-id="192c5-103">Este tópico descreve o suporte de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para literais.</span><span class="sxs-lookup"><span data-stu-id="192c5-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="192c5-104">Nulo</span><span class="sxs-lookup"><span data-stu-id="192c5-104">Null</span></span>  

 <span data-ttu-id="192c5-105">O literal nulo é usado para representar o zero valor de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="192c5-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="192c5-106">Um literal nulo é compatível com qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="192c5-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="192c5-107">Tipado anula pode ser criado por uma conversão sobre um literal nulo.</span><span class="sxs-lookup"><span data-stu-id="192c5-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="192c5-108">Para obter mais informações, consulte [Cast](cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="192c5-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="192c5-109">Para regras sobre onde literais nulos flutuantes livres podem ser usados, consulte [literais nulos e inferência de tipos](null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="192c5-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="192c5-110">Booliano</span><span class="sxs-lookup"><span data-stu-id="192c5-110">Boolean</span></span>  

 <span data-ttu-id="192c5-111">Literais booleanos são representados pelas palavras-chave `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="192c5-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="192c5-112">Integer</span><span class="sxs-lookup"><span data-stu-id="192c5-112">Integer</span></span>  

 <span data-ttu-id="192c5-113">Literais inteiro podem ser do tipo <xref:System.Int32> ou <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="192c5-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="192c5-114">Um literal de <xref:System.Int32> é uma série de caracteres numéricos.</span><span class="sxs-lookup"><span data-stu-id="192c5-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="192c5-115">Um literal de <xref:System.Int64> é uma série de caracteres numéricos seguidos por um maiúsculas. L.</span><span class="sxs-lookup"><span data-stu-id="192c5-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="192c5-116">Decimal</span><span class="sxs-lookup"><span data-stu-id="192c5-116">Decimal</span></span>  

 <span data-ttu-id="192c5-117">Número de ponto fixo (decimal) é uma série de caracteres numéricos, um ponto (.) e de outras uma série de caracteres numéricos seguidos por um maiúsculas “M”.</span><span class="sxs-lookup"><span data-stu-id="192c5-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="192c5-118">Float, double</span><span class="sxs-lookup"><span data-stu-id="192c5-118">Float, Double</span></span>  

 <span data-ttu-id="192c5-119">Um número de precisão dupla de ponto flutuante é uma série de caracteres numéricos, um ponto (.) e de outras uma série de caracteres numéricos possivelmente seguidos por um expoente.</span><span class="sxs-lookup"><span data-stu-id="192c5-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="192c5-120">Um número de ponto flutuante de único precisões (ou o flutuante) são uma sintaxe de precisão dupla de números de ponto flutuante seguido pela minúsculas F.</span><span class="sxs-lookup"><span data-stu-id="192c5-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="192c5-121">String</span><span class="sxs-lookup"><span data-stu-id="192c5-121">String</span></span>  

 <span data-ttu-id="192c5-122">Uma cadeia de caracteres é uma série de caracteres incluídos em marcas de aspas.</span><span class="sxs-lookup"><span data-stu-id="192c5-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="192c5-123">As aspas podem ser ambas as aspas simples (`'`) ou ambas as com aspas (").</span><span class="sxs-lookup"><span data-stu-id="192c5-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="192c5-124">Literais de cadeia de caracteres podem ser Unicode ou não Unicode.</span><span class="sxs-lookup"><span data-stu-id="192c5-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="192c5-125">Para declarar um literal de cadeia de caracteres como Unicode, prefixe o literal com uma letra maiúscula “Em”.</span><span class="sxs-lookup"><span data-stu-id="192c5-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="192c5-126">O padrão é literais de cadeia de caracteres de não Unicode.</span><span class="sxs-lookup"><span data-stu-id="192c5-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="192c5-127">Não é possível que haja nenhum espaço entre o N e a carga útil do literal de cadeia de caracteres, e No deve ser maiúscula.</span><span class="sxs-lookup"><span data-stu-id="192c5-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="192c5-128">Datetime</span><span class="sxs-lookup"><span data-stu-id="192c5-128">DateTime</span></span>  

 <span data-ttu-id="192c5-129">Um literal de datetime é independente da localidade e é composto de uma parte da data e uma parte de tempo.</span><span class="sxs-lookup"><span data-stu-id="192c5-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="192c5-130">Partes de data e hora são imperativas e não há nenhum valor padrão.</span><span class="sxs-lookup"><span data-stu-id="192c5-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="192c5-131">A parte de data deve ter o formato: `YYYY` - `MM` - `DD` , em que `YYYY` é um valor de ano de quatro dígitos entre 0001 e 9999, `MM` é o mês entre 1 e 12 e `DD` é o valor de dia que é válido para o mês determinado `MM` .</span><span class="sxs-lookup"><span data-stu-id="192c5-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="192c5-132">A parte de tempo deve ter o formato: `HH`:`MM`[:`SS`[.fffffff]], onde `HH` é o valor de hora entre 0 e 23, `MM` é minúsculo o valor entre 0 e 59, `SS` é o segundo valor entre 0 e 59 e o fffffff são o segundo valor fracionário entre 0 e 9999999.</span><span class="sxs-lookup"><span data-stu-id="192c5-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="192c5-133">Todos os intervalos de valores são incluindo.</span><span class="sxs-lookup"><span data-stu-id="192c5-133">All value ranges are inclusive.</span></span> <span data-ttu-id="192c5-134">Os segundos fracionários são opcionais.</span><span class="sxs-lookup"><span data-stu-id="192c5-134">Fractional seconds are optional.</span></span> <span data-ttu-id="192c5-135">Os segundos são opcionais a menos que os segundos fracionários são especificados; nesse caso, os segundos são necessários.</span><span class="sxs-lookup"><span data-stu-id="192c5-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="192c5-136">Quando os segundos ou os segundos fracionários não for especificado, o valor padrão de zero será usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="192c5-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="192c5-137">Pode haver qualquer número de espaços entre o símbolo de DATETIME e a carga útil literal, mas nenhuma novas linhas.</span><span class="sxs-lookup"><span data-stu-id="192c5-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="192c5-138">Hora</span><span class="sxs-lookup"><span data-stu-id="192c5-138">Time</span></span>  

 <span data-ttu-id="192c5-139">Um literal hora é independente da localidade e composta de uma parte de tempo somente.</span><span class="sxs-lookup"><span data-stu-id="192c5-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="192c5-140">A parte de tempo é imperativa e não há nenhum valor padrão.</span><span class="sxs-lookup"><span data-stu-id="192c5-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="192c5-141">Deve ter o formato HH:MM[:SS[.fffffff]], onde HH é o valor de hora entre 0 e 23, MM são o minuto valor entre 0 e 59, SS são o segundo valor entre 0 e 59, e fffffff é o segundo valor da fração entre 0 e 9999999.</span><span class="sxs-lookup"><span data-stu-id="192c5-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="192c5-142">Todos os intervalos de valores são incluindo.</span><span class="sxs-lookup"><span data-stu-id="192c5-142">All value ranges are inclusive.</span></span> <span data-ttu-id="192c5-143">Os segundos fracionários são opcionais.</span><span class="sxs-lookup"><span data-stu-id="192c5-143">Fractional seconds are optional.</span></span> <span data-ttu-id="192c5-144">Os segundos são opcionais a menos que os segundos fracionários são especificados; nesse caso, os segundos são necessários.</span><span class="sxs-lookup"><span data-stu-id="192c5-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="192c5-145">Quando os segundos ou frações não for especificado, o valor padrão de zero será usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="192c5-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="192c5-146">Pode haver qualquer número de espaços entre o símbolo de TEMPOS e a carga útil literal, mas nenhuma novas linhas.</span><span class="sxs-lookup"><span data-stu-id="192c5-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="192c5-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="192c5-147">DateTimeOffset</span></span>  

 <span data-ttu-id="192c5-148">Um literal de datetimeoffset é independente da localidade e composta de uma parte da data, uma parte de tempo, e uma parte de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="192c5-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="192c5-149">Todos datam, multiplicado por, e as partes de deslocamento são imperativas e não há nenhum valor padrão.</span><span class="sxs-lookup"><span data-stu-id="192c5-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="192c5-150">A parte de data deve ter o formato YYYY YYYY-MM-DD, onde é um valor do ano de quatro dígitos entre 0001 e 9999, mm é o mês entre 1 e 12, e o DD é o valor do dia que é válido para o mês determinado.</span><span class="sxs-lookup"><span data-stu-id="192c5-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="192c5-151">A parte de tempo deve ter o formato HH:MM[:SS[.fffffff]], onde HH é o valor de hora entre 0 e 23, MM são o minuto valor entre 0 e 59, SS são o segundo valor entre 0 e 59, e fffffff é o segundo valor fracionário entre 0 e 9999999.</span><span class="sxs-lookup"><span data-stu-id="192c5-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="192c5-152">Todos os intervalos de valores são incluindo.</span><span class="sxs-lookup"><span data-stu-id="192c5-152">All value ranges are inclusive.</span></span> <span data-ttu-id="192c5-153">Os segundos fracionários são opcionais.</span><span class="sxs-lookup"><span data-stu-id="192c5-153">Fractional seconds are optional.</span></span> <span data-ttu-id="192c5-154">Os segundos são opcionais a menos que os segundos fracionários são especificados; nesse caso, os segundos são necessários.</span><span class="sxs-lookup"><span data-stu-id="192c5-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="192c5-155">Quando os segundos ou frações não for especificado, o valor padrão de zero será usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="192c5-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="192c5-156">A parte de deslocamento deve ter o formato {+&#124;-} HH: MM, em que HH e MM têm o mesmo significado que na parte de hora.</span><span class="sxs-lookup"><span data-stu-id="192c5-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="192c5-157">O intervalo de deslocamento, no entanto, deve estar entre o 14:00 e + -14:00</span><span class="sxs-lookup"><span data-stu-id="192c5-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="192c5-158">Pode haver qualquer número de espaços entre o símbolo de DATETIMEOFFSET e a carga útil literal, mas nenhuma novas linhas.</span><span class="sxs-lookup"><span data-stu-id="192c5-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="192c5-159">Um valor literal válido de Entity SQL pode cair fora dos intervalos suportados para CLR ou a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="192c5-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="192c5-160">Isso pode levar a uma exceção</span><span class="sxs-lookup"><span data-stu-id="192c5-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="192c5-161">Binário</span><span class="sxs-lookup"><span data-stu-id="192c5-161">Binary</span></span>  

 <span data-ttu-id="192c5-162">Um literal de cadeia de caracteres binário é uma sequência de dígitos hexadecimais delimitado por aspas simples que seguem binário de palavra-chave ou o símbolo `X` ou `x`de atalho.</span><span class="sxs-lookup"><span data-stu-id="192c5-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="192c5-163">O símbolo `X` de atalho não difere maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="192c5-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="192c5-164">Zero ou mais espaços são permitidos entre a palavra-chave `binary` e o valor da cadeia de caracteres binário.</span><span class="sxs-lookup"><span data-stu-id="192c5-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="192c5-165">Os caracteres hexadecimais também são não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="192c5-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="192c5-166">Se o literal é composta de um número ímpar de dígitos hexadecimais, o literal será alinhado ao mesmo dígito hexadecimal seguir prefixando o literal com um dígito hexadecimal zero.</span><span class="sxs-lookup"><span data-stu-id="192c5-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="192c5-167">Não há um limite formal no tamanho da cadeia de caracteres binário.</span><span class="sxs-lookup"><span data-stu-id="192c5-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="192c5-168">Guid</span><span class="sxs-lookup"><span data-stu-id="192c5-168">Guid</span></span>  

 <span data-ttu-id="192c5-169">Um literal de `GUID` representa um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="192c5-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="192c5-170">É uma sequência formada pela palavra-chave `GUID` seguida por dígitos hexadecimais no formulário conhecido como formato de *registro* : 8-4-4-4-12 entre aspas simples.</span><span class="sxs-lookup"><span data-stu-id="192c5-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="192c5-171">Os dígitos hexadecimais não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="192c5-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="192c5-172">Pode haver qualquer número de espaços entre o símbolo de TEMPOS e a carga útil literal, mas nenhuma novas linhas.</span><span class="sxs-lookup"><span data-stu-id="192c5-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="192c5-173">Confira também</span><span class="sxs-lookup"><span data-stu-id="192c5-173">See also</span></span>

- [<span data-ttu-id="192c5-174">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="192c5-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
