---
title: Como inicializar uma variável de matriz
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 1add054a6cb6468f4581f92ca3a258c5b0cdc77d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058853"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="42ee4-102">Como inicializar uma variável de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42ee4-102">How to: Initialize an Array Variable in Visual Basic</span></span>

<span data-ttu-id="42ee4-103">Você Inicializa uma variável de matriz, incluindo um literal de matriz em uma `New` cláusula e especificando os valores iniciais da matriz.</span><span class="sxs-lookup"><span data-stu-id="42ee4-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="42ee4-104">Você pode especificar o tipo ou permitir que ele seja inferido com base nos valores no literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="42ee4-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="42ee4-105">Para obter mais informações sobre como o tipo é inferido, consulte "populando uma matriz com valores iniciais" em [matrizes](index.md).</span><span class="sxs-lookup"><span data-stu-id="42ee4-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="42ee4-106">Para inicializar uma variável de matriz usando um literal de matriz</span><span class="sxs-lookup"><span data-stu-id="42ee4-106">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="42ee4-107">Na `New` cláusula ou quando você atribui o valor de matriz, forneça os valores de elemento entre chaves ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="42ee4-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="42ee4-108">O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz que tem elementos do tipo `Char` .</span><span class="sxs-lookup"><span data-stu-id="42ee4-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="42ee4-109">Depois que cada instrução é executada, a matriz que é criada tem um comprimento de 3, com elementos no índice 0 até o índice 2 que contém os valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="42ee4-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="42ee4-110">Se você fornecer o limite superior e os valores, deverá incluir um valor para cada elemento do índice 0 por meio do limite superior.</span><span class="sxs-lookup"><span data-stu-id="42ee4-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="42ee4-111">Observe que você não precisa especificar o limite superior do índice se fornecer valores de elemento em um literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="42ee4-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="42ee4-112">Se nenhum limite superior for especificado, o tamanho da matriz será inferido com base no número de valores no literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="42ee4-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="42ee4-113">Para inicializar uma variável de matriz multidimensional usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="42ee4-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="42ee4-114">Aninhe valores entre chaves ( `{}` ) entre chaves.</span><span class="sxs-lookup"><span data-stu-id="42ee4-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="42ee4-115">Verifique se os literais de matriz aninhada inferem como matrizes do mesmo tipo e comprimento.</span><span class="sxs-lookup"><span data-stu-id="42ee4-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="42ee4-116">O exemplo de código a seguir mostra vários exemplos de inicialização de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="42ee4-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="42ee4-117">Você pode especificar explicitamente os limites da matriz ou deixá-los fora e fazer com que o compilador inferir os limites da matriz com base nos valores no literal da matriz.</span><span class="sxs-lookup"><span data-stu-id="42ee4-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="42ee4-118">Se você fornecer os limites superiores e os valores, deverá incluir um valor para cada elemento do índice 0 por meio do limite superior em cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="42ee4-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="42ee4-119">O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz bidimensional que tem elementos do tipo `Short`</span><span class="sxs-lookup"><span data-stu-id="42ee4-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="42ee4-120">Depois que cada instrução é executada, a matriz criada contém seis elementos inicializados que têm índices `(0,0)` ,,,, `(0,1)` `(0,2)` `(1,0)` `(1,1)` e `(1,2)` .</span><span class="sxs-lookup"><span data-stu-id="42ee4-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="42ee4-121">Cada local da matriz contém o valor `10` .</span><span class="sxs-lookup"><span data-stu-id="42ee4-121">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="42ee4-122">O exemplo a seguir itera por meio de uma matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="42ee4-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="42ee4-123">Em um aplicativo de console do Windows que é gravado em Visual Basic, Cole o código dentro do `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="42ee4-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="42ee4-124">Os últimos comentários mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="42ee4-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="42ee4-125">Para inicializar uma variável de matriz denteada usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="42ee4-125">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="42ee4-126">Aninhe os valores de objeto entre chaves ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="42ee4-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="42ee4-127">Embora você também possa aninhar literais de matriz que especificam matrizes de comprimentos diferentes, no caso de uma matriz denteada, certifique-se de que os literais de matriz aninhada sejam colocados entre parênteses ( `()` ).</span><span class="sxs-lookup"><span data-stu-id="42ee4-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="42ee4-128">Os parênteses forçam a avaliação dos literais de matriz aninhada e as matrizes resultantes são usadas como os valores iniciais da matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="42ee4-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="42ee4-129">O exemplo de código a seguir mostra dois exemplos de inicialização de matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="42ee4-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="42ee4-130">O exemplo a seguir itera por meio de uma matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="42ee4-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="42ee4-131">Em um aplicativo de console do Windows que é gravado em Visual Basic, Cole o código dentro do `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="42ee4-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="42ee4-132">Os últimos comentários no código mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="42ee4-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="42ee4-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="42ee4-133">See also</span></span>

- [<span data-ttu-id="42ee4-134">matrizes</span><span class="sxs-lookup"><span data-stu-id="42ee4-134">Arrays</span></span>](index.md)
- [<span data-ttu-id="42ee4-135">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="42ee4-135">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
