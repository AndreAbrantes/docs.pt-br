---
title: 'Como: usar procedimentos armazenados mapeados para várias formas de resultado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 26cc30790da26949fba889106d060cdef89013a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184996"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="06581-102">Como: usar procedimentos armazenados mapeados para várias formas de resultado</span><span class="sxs-lookup"><span data-stu-id="06581-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="06581-103">Quando um procedimento armazenado pode retornar várias formas de resultado, o tipo de retorno não pode ser fortemente tipado a uma única forma de projeção.</span><span class="sxs-lookup"><span data-stu-id="06581-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="06581-104">Embora [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o possa gerar todos os tipos de projeção possíveis, ele não pode saber a ordem na qual eles serão retornados.</span><span class="sxs-lookup"><span data-stu-id="06581-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="06581-105">Compare este cenário com procedimentos armazenados que gerenciar várias formas de resultado seqüencialmente.</span><span class="sxs-lookup"><span data-stu-id="06581-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="06581-106">Para obter mais informações, consulte [como: usar procedimentos armazenados mapeados para formas de resultados sequenciais](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="06581-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="06581-107">O atributo de <xref:System.Data.Linq.Mapping.ResultTypeAttribute> é aplicado aos procedimentos armazenados que vários tipos de retorno de resultado para especificar o conjunto de tipos podem retornar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="06581-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06581-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06581-108">Example</span></span>  

 <span data-ttu-id="06581-109">No exemplo de código SQL, a forma de resultado depende de entrada (`shape =1` ou `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="06581-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="06581-110">Você não sabe que projeção será retornada primeiro.</span><span class="sxs-lookup"><span data-stu-id="06581-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="06581-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06581-111">Example</span></span>  

 <span data-ttu-id="06581-112">Você usaria código semelhante ao seguinte para executar este procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="06581-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06581-113">Você deve usar o padrão de <xref:System.Data.Linq.IMultipleResults.GetResult%2A> para obter um enumerador do tipo correto, com base no seu conhecimento do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="06581-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="06581-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="06581-114">See also</span></span>

- [<span data-ttu-id="06581-115">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="06581-115">Stored Procedures</span></span>](stored-procedures.md)
