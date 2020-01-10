---
title: Matrizes multidimensionais – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715044"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="34983-102">Matrizes multidimensionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="34983-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="34983-103">As matrizes podem ter mais de uma dimensão.</span><span class="sxs-lookup"><span data-stu-id="34983-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="34983-104">Por exemplo, a declaração a seguir cria uma matriz bidimensional de quatro linhas e duas colunas.</span><span class="sxs-lookup"><span data-stu-id="34983-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="34983-105">A declaração a seguir cria uma matriz de três dimensões, 4, 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="34983-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="34983-106">Inicialização de Matriz</span><span class="sxs-lookup"><span data-stu-id="34983-106">Array Initialization</span></span>

 <span data-ttu-id="34983-107">É possível inicializar a matriz na declaração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34983-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="34983-108">Também é possível inicializar a matriz sem especificar a classificação.</span><span class="sxs-lookup"><span data-stu-id="34983-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="34983-109">Caso você escolha declarar uma variável de matriz sem inicialização, será necessário usar o operador `new` ao atribuir uma matriz a essa variável.</span><span class="sxs-lookup"><span data-stu-id="34983-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="34983-110">O uso de `new` é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34983-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="34983-111">O exemplo a seguir atribui um valor a um elemento de matriz específico.</span><span class="sxs-lookup"><span data-stu-id="34983-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="34983-112">Da mesma forma, o exemplo a seguir obtém o valor de um elemento de matriz específico e o atribui à variável `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="34983-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="34983-113">O exemplo de código a seguir inicializa os elementos da matriz com valores padrão (exceto em matrizes denteadas).</span><span class="sxs-lookup"><span data-stu-id="34983-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="34983-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="34983-114">See also</span></span>

- [<span data-ttu-id="34983-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="34983-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34983-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="34983-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="34983-117">Matrizes unidimensionais</span><span class="sxs-lookup"><span data-stu-id="34983-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="34983-118">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="34983-118">Jagged Arrays</span></span>](./jagged-arrays.md)
