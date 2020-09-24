---
title: Expressões constantes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 163f73a7682d444214caa213751cb35f8f0e8743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153034"
---
# <a name="constant-expressions"></a><span data-ttu-id="7fe0d-102">Expressões constantes</span><span class="sxs-lookup"><span data-stu-id="7fe0d-102">Constant Expressions</span></span>

<span data-ttu-id="7fe0d-103">Uma expressão constante consiste em um valor constante.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="7fe0d-104">Os valores constantes são convertidos diretamente às expressões constantes da árvore de comando, sem nenhuma conversão no cliente.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="7fe0d-105">Isso inclui as expressões que levam a um valor constante.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="7fe0d-106">Portanto, o comportamento da fonte de dados deve ser esperado para todas as expressões que envolvem constantes.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="7fe0d-107">Isso pode levar ao comportamento que difere do comportamento de CLR.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="7fe0d-108">O exemplo a seguir mostra uma expressão constante que é avaliada no servidor.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="7fe0d-109">LINQ to Entities não dá suporte ao uso de uma classe de usuário como uma constante.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="7fe0d-110">No entanto, uma referência de propriedade em uma classe de usuário é considerada uma constante, e será convertida em uma expressão constante de árvore de comando e executada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7fe0d-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe0d-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fe0d-111">See also</span></span>

- [<span data-ttu-id="7fe0d-112">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7fe0d-112">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
