---
title: Instrução Erase
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873292"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="6b2b0-102">Instrução Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b2b0-102">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="6b2b0-103">Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b2b0-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="6b2b0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="6b2b0-105">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="6b2b0-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-106">Required.</span></span> <span data-ttu-id="6b2b0-107">Lista de variáveis de matriz a serem apagadas.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-107">List of array variables to be erased.</span></span> <span data-ttu-id="6b2b0-108">Várias variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b2b0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b2b0-109">Remarks</span></span>  

 <span data-ttu-id="6b2b0-110">A `Erase` instrução pode aparecer somente no nível do procedimento.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="6b2b0-111">Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou de módulo.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="6b2b0-112">A `Erase` instrução é equivalente a atribuir `Nothing` a cada variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b2b0-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b2b0-113">Example</span></span>  

 <span data-ttu-id="6b2b0-114">O exemplo a seguir usa a `Erase` instrução para limpar duas matrizes e liberar sua memória (1000 e 100 elementos de armazenamento, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="6b2b0-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="6b2b0-115">`ReDim`Em seguida, a instrução atribui uma nova instância de matriz à matriz tridimensional.</span><span class="sxs-lookup"><span data-stu-id="6b2b0-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="6b2b0-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b2b0-116">See also</span></span>

- [<span data-ttu-id="6b2b0-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="6b2b0-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="6b2b0-118">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="6b2b0-118">ReDim Statement</span></span>](redim-statement.md)
