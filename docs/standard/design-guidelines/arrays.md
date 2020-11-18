---
title: Matrizes
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: c3545c609b6544e6528bbae08889d0ef20473802
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821600"
---
# <a name="arrays"></a><span data-ttu-id="d8155-102">Matrizes</span><span class="sxs-lookup"><span data-stu-id="d8155-102">Arrays</span></span>
<span data-ttu-id="d8155-103">✔️ preferir usar coleções em matrizes em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="d8155-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="d8155-104">A seção [coleções](guidelines-for-collections.md) fornece detalhes sobre como escolher entre coleções e matrizes.</span><span class="sxs-lookup"><span data-stu-id="d8155-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="d8155-105">❌ Não use campos de matriz somente leitura.</span><span class="sxs-lookup"><span data-stu-id="d8155-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="d8155-106">O próprio campo é somente leitura e não pode ser alterado, mas os elementos na matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="d8155-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="d8155-107">✔️ Considere o uso de matrizes denteadas em vez de matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="d8155-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="d8155-108">Uma matriz denteada é uma matriz com elementos que também são matrizes.</span><span class="sxs-lookup"><span data-stu-id="d8155-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="d8155-109">As matrizes que compõem os elementos podem ser de tamanhos diferentes, levando a menos espaço desperdiçado para alguns conjuntos de dados (por exemplo, matriz esparsa) em comparação com matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="d8155-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="d8155-110">Além disso, o CLR otimiza as operações de índice em matrizes denteadas, para que possam apresentar um melhor desempenho de tempo de execução em alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="d8155-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="d8155-111">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d8155-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d8155-112">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d8155-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d8155-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8155-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="d8155-114">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="d8155-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d8155-115">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="d8155-115">Usage Guidelines</span></span>](usage-guidelines.md)
