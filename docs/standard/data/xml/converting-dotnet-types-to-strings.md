---
title: Convertendo tipos .NET em cadeias de caracteres
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 9744224b4346b865a112b0eb6957f12553e1ec5f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830981"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="22ba0-102">Converter tipos .NET em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="22ba0-102">Convert .NET types to strings</span></span>

<span data-ttu-id="22ba0-103">Se você quiser converter um tipo .NET em uma cadeia de caracteres, use o método **ToString** .</span><span class="sxs-lookup"><span data-stu-id="22ba0-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="22ba0-104">O método **ToString** retorna uma representação de cadeia de caracteres do tipo passado.</span><span class="sxs-lookup"><span data-stu-id="22ba0-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="22ba0-105">A tabela a seguir lista os tipos .NET que retornam uma cadeia de caracteres em um formato que mapeia para as especificações XSD (esquema XML).</span><span class="sxs-lookup"><span data-stu-id="22ba0-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="22ba0-106">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="22ba0-106">.NET type</span></span>|<span data-ttu-id="22ba0-107">Tipo cadeia de caracteres retornado</span><span class="sxs-lookup"><span data-stu-id="22ba0-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="22ba0-108">Booliano</span><span class="sxs-lookup"><span data-stu-id="22ba0-108">Boolean</span></span>|<span data-ttu-id="22ba0-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="22ba0-109">"true", "false"</span></span>|  
|<span data-ttu-id="22ba0-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="22ba0-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="22ba0-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="22ba0-111">"INF"</span></span>|  
|<span data-ttu-id="22ba0-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="22ba0-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="22ba0-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="22ba0-113">"-INF"</span></span>|  
|<span data-ttu-id="22ba0-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="22ba0-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="22ba0-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="22ba0-115">"INF"</span></span>|  
|<span data-ttu-id="22ba0-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="22ba0-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="22ba0-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="22ba0-117">"-INF"</span></span>|  
|<span data-ttu-id="22ba0-118">Datetime</span><span class="sxs-lookup"><span data-stu-id="22ba0-118">DateTime</span></span>|<span data-ttu-id="22ba0-119">O formato é yyyy-MM-ddTHH:mm:sszzzzzz e seus subconjuntos.</span><span class="sxs-lookup"><span data-stu-id="22ba0-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="22ba0-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="22ba0-120">Timespan</span></span>|<span data-ttu-id="22ba0-121">O formato é PnYnMnTnHnMnS, por exemplo, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, meses 10, 15 dias, 10hours, 30 minutos e 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="22ba0-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22ba0-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="22ba0-122">See also</span></span>

- [<span data-ttu-id="22ba0-123">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="22ba0-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="22ba0-124">Convertendo cadeias de caracteres em tipos de dados .NET</span><span class="sxs-lookup"><span data-stu-id="22ba0-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
