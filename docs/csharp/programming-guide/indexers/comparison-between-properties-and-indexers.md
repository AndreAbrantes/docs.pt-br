---
title: "Comparação entre propriedades e indexadores (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4bb2de1cfdcf4a8a7c847dfabe8d69124a4adf90
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="1027b-102">Comparação entre propriedades e indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1027b-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="1027b-103">Os indexadores são como propriedades.</span><span class="sxs-lookup"><span data-stu-id="1027b-103">Indexers are like properties.</span></span> <span data-ttu-id="1027b-104">Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.</span><span class="sxs-lookup"><span data-stu-id="1027b-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="1027b-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1027b-105">Property</span></span>|<span data-ttu-id="1027b-106">Indexador</span><span class="sxs-lookup"><span data-stu-id="1027b-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1027b-107">Permite que os métodos sejam chamados como se fossem membros de dados públicos.</span><span class="sxs-lookup"><span data-stu-id="1027b-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="1027b-108">Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="1027b-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="1027b-109">Acessado por meio de um nome simples.</span><span class="sxs-lookup"><span data-stu-id="1027b-109">Accessed through a simple name.</span></span>|<span data-ttu-id="1027b-110">Acessado por meio de um índice.</span><span class="sxs-lookup"><span data-stu-id="1027b-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="1027b-111">Pode ser estático ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="1027b-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="1027b-112">Deve ser um membro da instância.</span><span class="sxs-lookup"><span data-stu-id="1027b-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="1027b-113">Um acessador [get](../../../csharp/language-reference/keywords/get.md) de uma propriedade não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1027b-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="1027b-114">Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.</span><span class="sxs-lookup"><span data-stu-id="1027b-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="1027b-115">Um acessador [set](../../../csharp/language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.</span><span class="sxs-lookup"><span data-stu-id="1027b-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="1027b-116">Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../../csharp/language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="1027b-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="1027b-117">Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1027b-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="1027b-118">Não oferece suporte a sintaxe reduzida.</span><span class="sxs-lookup"><span data-stu-id="1027b-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1027b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1027b-119">See Also</span></span>  
 <span data-ttu-id="1027b-120">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1027b-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1027b-121">[Indexadores](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="1027b-121">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="1027b-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1027b-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

