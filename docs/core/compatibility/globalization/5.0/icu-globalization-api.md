---
title: 'Alteração significativa: as APIs de globalização usam bibliotecas ICU no Windows'
description: Saiba mais sobre a alteração significativa de globalização no .NET 5,0 em que as bibliotecas ICU são usadas para a funcionalidade de globalização em vez do NLS.
ms.date: 05/19/2020
ms.openlocfilehash: efc20e21969ea4a83c9122e40b262e1dc38e6770
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760539"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="61d17-103">APIs de globalização usam bibliotecas ICU no Windows</span><span class="sxs-lookup"><span data-stu-id="61d17-103">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="61d17-104">O .NET 5,0 e versões posteriores usam bibliotecas [internacionais para](http://site.icu-project.org/home) a funcionalidade de globalização na execução no Windows 10 pode ser 2019 atualização ou posterior.</span><span class="sxs-lookup"><span data-stu-id="61d17-104">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

## <a name="change-description"></a><span data-ttu-id="61d17-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="61d17-105">Change description</span></span>

<span data-ttu-id="61d17-106">No .NET Core 1,0-3,1 e .NET Framework 4 e versões posteriores, as bibliotecas do .NET usam APIs [NLS (suporte a idioma nacional)](/windows/win32/intl/national-language-support) para a funcionalidade de globalização no Windows.</span><span class="sxs-lookup"><span data-stu-id="61d17-106">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="61d17-107">Por exemplo, as funções NLS foram usadas para comparar cadeias de caracteres, obter informações de cultura e executar maiúsculas e minúsculas na cultura apropriada.</span><span class="sxs-lookup"><span data-stu-id="61d17-107">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="61d17-108">A partir do .NET 5,0, se um aplicativo estiver em execução no Windows 10 pode ser 2019 Update ou posterior, as bibliotecas do .NET usarão APIs de globalização [ICU](http://site.icu-project.org/home) , por padrão.</span><span class="sxs-lookup"><span data-stu-id="61d17-108">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="61d17-109">O Windows 10 pode 2019 atualização e versões posteriores são fornecidas com a biblioteca nativa do ICU.</span><span class="sxs-lookup"><span data-stu-id="61d17-109">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="61d17-110">Se o tempo de execução do .NET não puder carregar o ICU, ele usará o NLS.</span><span class="sxs-lookup"><span data-stu-id="61d17-110">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="61d17-111">Diferenças de comportamento</span><span class="sxs-lookup"><span data-stu-id="61d17-111">Behavioral differences</span></span>

<span data-ttu-id="61d17-112">Você poderá ver as alterações em seu aplicativo mesmo se não perceber que está usando instalações de globalização.</span><span class="sxs-lookup"><span data-stu-id="61d17-112">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="61d17-113">Esta seção lista algumas das alterações comportamentais que você pode ver, mas também há outras.</span><span class="sxs-lookup"><span data-stu-id="61d17-113">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

### <a name="stringindexof"></a><span data-ttu-id="61d17-114">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="61d17-114">String.IndexOf</span></span>

<span data-ttu-id="61d17-115">Considere o código a seguir que chama <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> para localizar o índice do caractere de nova linha em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="61d17-115">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="61d17-116">Nas versões anteriores do .NET no Windows, o trecho é impresso `6` .</span><span class="sxs-lookup"><span data-stu-id="61d17-116">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="61d17-117">No .NET 5,0 e versões posteriores no Windows 19H1 e versões posteriores, o trecho de código é impresso `-1` .</span><span class="sxs-lookup"><span data-stu-id="61d17-117">In .NET 5.0 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="61d17-118">Para corrigir esse código realizando uma pesquisa ordinal em vez de uma pesquisa sensível à cultura, chame a <xref:System.String.IndexOf(System.String,System.StringComparison)> sobrecarga e passe <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> como um argumento.</span><span class="sxs-lookup"><span data-stu-id="61d17-118">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="61d17-119">Você pode executar as regras [de análise de código CA1307: especificar StringComparison para clareza](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) e [CA1309: Use o ordinal StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) para encontrar esses sites de chamada em seu código.</span><span class="sxs-lookup"><span data-stu-id="61d17-119">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="61d17-120">Para obter mais informações, consulte [comportamento de alterações ao comparar cadeias de caracteres no .NET 5 +](../../../../standard/base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="61d17-120">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../standard/base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="currency-symbol"></a><span data-ttu-id="61d17-121">Símbolo de moeda</span><span class="sxs-lookup"><span data-stu-id="61d17-121">Currency symbol</span></span>

<span data-ttu-id="61d17-122">Considere o código a seguir que formata uma cadeia de caracteres usando o especificador de formato de moeda `C` .</span><span class="sxs-lookup"><span data-stu-id="61d17-122">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="61d17-123">A cultura do thread atual é definida como uma cultura que inclui apenas o idioma e não o país.</span><span class="sxs-lookup"><span data-stu-id="61d17-123">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="61d17-124">Nas versões anteriores do .NET no Windows, o valor do texto é `"100,00 €"` .</span><span class="sxs-lookup"><span data-stu-id="61d17-124">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="61d17-125">No .NET 5,0 e versões posteriores no Windows 19H1 e versões posteriores, o valor de Text é `"100,00 ¤"` , que usa o símbolo de moeda internacional em vez do euro.</span><span class="sxs-lookup"><span data-stu-id="61d17-125">In .NET 5.0 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="61d17-126">No ICU, o design é que uma moeda é uma propriedade de um país ou região, não um idioma.</span><span class="sxs-lookup"><span data-stu-id="61d17-126">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="61d17-127">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="61d17-127">Reason for change</span></span>

<span data-ttu-id="61d17-128">Essa alteração foi introduzida para unificar. Comportamento de globalização da rede em todos os sistemas operacionais com suporte.</span><span class="sxs-lookup"><span data-stu-id="61d17-128">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="61d17-129">Ele também fornece a capacidade de os aplicativos agruparem suas próprias bibliotecas de globalização em vez de depender das bibliotecas internas do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="61d17-129">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="61d17-130">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="61d17-130">Version introduced</span></span>

<span data-ttu-id="61d17-131">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="61d17-131">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="61d17-132">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="61d17-132">Recommended action</span></span>

<span data-ttu-id="61d17-133">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="61d17-133">No action is required on the part of the developer.</span></span> <span data-ttu-id="61d17-134">No entanto, se você quiser continuar usando as APIs de globalização NLS, poderá definir uma [opção de tempo de execução](../../../run-time-config/globalization.md#nls) para reverter para esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="61d17-134">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="61d17-135">Para obter mais informações sobre as opções disponíveis, consulte o artigo [globalização .net e ICU](../../../../standard/globalization-localization/globalization-icu.md) .</span><span class="sxs-lookup"><span data-stu-id="61d17-135">For more information about the available switches, see the [.NET globalization and ICU](../../../../standard/globalization-localization/globalization-icu.md) article.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="61d17-136">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="61d17-136">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="61d17-137">Maioria dos tipos no <xref:System.Globalization?displayProperty=fullName> namespace</span><span class="sxs-lookup"><span data-stu-id="61d17-137">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="61d17-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (ao classificar uma matriz de cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="61d17-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="61d17-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (quando os elementos da lista são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="61d17-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="61d17-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (quando as chaves são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="61d17-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="61d17-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (quando as chaves são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="61d17-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="61d17-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (quando o conjunto contém cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="61d17-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
