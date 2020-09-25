---
title: Expressões de inicialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 93f590e1c177adf541baca85a48fee5f9eb8d1d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203625"
---
# <a name="initialization-expressions"></a><span data-ttu-id="a6c8b-102">Expressões de inicialização</span><span class="sxs-lookup"><span data-stu-id="a6c8b-102">Initialization Expressions</span></span>

<span data-ttu-id="a6c8b-103">Uma expressão de inicialização inicializa um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="a6c8b-104">A maioria das expressões de inicialização são suportadas, incluindo a maioria novo C# 3,0 e Visual Basic 9,0 expressões de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="a6c8b-105">Os seguintes tipos podem ser inicializados e retornado por uma consulta LINQ to Entities:</span><span class="sxs-lookup"><span data-stu-id="a6c8b-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="a6c8b-106">Uma coleção de zero ou mais objetos de entidade tipados ou uma projeção de tipos complexos que são definidos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="a6c8b-107">Tipos CLR com suporte no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-107">CLR types supported by the Entity Framework.</span></span>
  
- <span data-ttu-id="a6c8b-108">Coleções internas.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-108">Inline collections.</span></span>  
  
- <span data-ttu-id="a6c8b-109">Tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="a6c8b-110">A inicialização tipo anônimo é mostrada no exemplo a seguir na sintaxe da expressão de consulta:</span><span class="sxs-lookup"><span data-stu-id="a6c8b-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="a6c8b-111">O exemplo a seguir na sintaxe da consulta com base em método mostra a inicialização tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="a6c8b-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="a6c8b-112">A inicialização definido pelo usuário da classe também é suportado.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="a6c8b-113">O padrão de inicialização C# 3,0 e Visual Basic 9,0 é suportado e pressupõe que o getter e o setter de propriedade são simétricos.</span><span class="sxs-lookup"><span data-stu-id="a6c8b-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="a6c8b-114">O exemplo a seguir na sintaxe da expressão de consulta a seguir mostra uma classe personalizada que está sendo inicializada na consulta:</span><span class="sxs-lookup"><span data-stu-id="a6c8b-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="a6c8b-115">O exemplo a seguir na sintaxe da consulta com base em método mostra uma classe personalizada que está sendo inicializada na consulta:</span><span class="sxs-lookup"><span data-stu-id="a6c8b-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="a6c8b-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="a6c8b-116">See also</span></span>

- [<span data-ttu-id="a6c8b-117">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="a6c8b-117">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
