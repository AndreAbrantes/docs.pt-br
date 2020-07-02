---
title: 'Exemplo de expressão regular: Alterando formatos de data'
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 3b657ac6c88a1ee846f7f1d2156a18fd34621808
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803944"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="54d46-102">Exemplo de expressão regular: Alterando formatos de data</span><span class="sxs-lookup"><span data-stu-id="54d46-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="54d46-103">O exemplo de código a seguir usa o <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> método para substituir datas que têm a forma *mm* / *DD* / *AA* com datas que têm a forma *DD* - *mm* - *AA*.</span><span class="sxs-lookup"><span data-stu-id="54d46-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="54d46-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54d46-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="54d46-105">O código a seguir mostra como o método `MDYToDMY` pode ser chamado em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54d46-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="54d46-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="54d46-106">Comments</span></span>  
 <span data-ttu-id="54d46-107">O padrão de expressão regular `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="54d46-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="54d46-108">Padrão</span><span class="sxs-lookup"><span data-stu-id="54d46-108">Pattern</span></span>|<span data-ttu-id="54d46-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="54d46-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="54d46-110">Começar a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="54d46-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="54d46-111">Corresponder a um ou dois dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="54d46-111">Match one or two decimal digits.</span></span> <span data-ttu-id="54d46-112">Este é o grupo capturado do `month`.</span><span class="sxs-lookup"><span data-stu-id="54d46-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="54d46-113">Corresponde à barra.</span><span class="sxs-lookup"><span data-stu-id="54d46-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="54d46-114">Corresponder a um ou dois dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="54d46-114">Match one or two decimal digits.</span></span> <span data-ttu-id="54d46-115">Este é o grupo capturado do `day`.</span><span class="sxs-lookup"><span data-stu-id="54d46-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="54d46-116">Corresponde à barra.</span><span class="sxs-lookup"><span data-stu-id="54d46-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="54d46-117">Corresponder de dois a quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="54d46-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="54d46-118">Este é o grupo capturado do `year`.</span><span class="sxs-lookup"><span data-stu-id="54d46-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="54d46-119">Termina a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="54d46-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="54d46-120">O padrão `${day}-${month}-${year}` define a cadeia de caracteres de substituição conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="54d46-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="54d46-121">Padrão</span><span class="sxs-lookup"><span data-stu-id="54d46-121">Pattern</span></span>|<span data-ttu-id="54d46-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="54d46-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="54d46-123">Adicionar a cadeia de caracteres capturada pelo grupo de captura `day`.</span><span class="sxs-lookup"><span data-stu-id="54d46-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="54d46-124">Adicionar um hífen.</span><span class="sxs-lookup"><span data-stu-id="54d46-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="54d46-125">Adicionar a cadeia de caracteres capturada pelo grupo de captura `month`.</span><span class="sxs-lookup"><span data-stu-id="54d46-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="54d46-126">Adicionar um hífen.</span><span class="sxs-lookup"><span data-stu-id="54d46-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="54d46-127">Adicionar a cadeia de caracteres capturada pelo grupo de captura `year`.</span><span class="sxs-lookup"><span data-stu-id="54d46-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54d46-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54d46-128">See also</span></span>

- [<span data-ttu-id="54d46-129">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="54d46-129">.NET Regular Expressions</span></span>](regular-expressions.md)
