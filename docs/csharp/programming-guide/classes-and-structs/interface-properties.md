---
title: Propriedades de interface – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705529"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="ecf32-102">Propriedades de interface (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ecf32-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="ecf32-103">As propriedades podem ser declaradas em uma [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="ecf32-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="ecf32-104">Este é um exemplo de um acessador de propriedade de interface:</span><span class="sxs-lookup"><span data-stu-id="ecf32-104">The following is an example of an interface property accessor:</span></span>

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

<span data-ttu-id="ecf32-105">O acessador de uma propriedade de interface não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="ecf32-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="ecf32-106">Portanto, a finalidade dos acessadores é indicar se a propriedade é leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="ecf32-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>

## <a name="example"></a><span data-ttu-id="ecf32-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecf32-107">Example</span></span>

<span data-ttu-id="ecf32-108">Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="ecf32-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="ecf32-109">A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ecf32-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="ecf32-110">O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.</span><span class="sxs-lookup"><span data-stu-id="ecf32-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="ecf32-111">Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado.</span><span class="sxs-lookup"><span data-stu-id="ecf32-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="ecf32-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ecf32-112">For example:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="ecf32-113">Isso é denominado [Implementação explícita da interface](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="ecf32-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="ecf32-114">Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface.</span><span class="sxs-lookup"><span data-stu-id="ecf32-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="ecf32-115">Ou seja, a seguinte declaração de propriedade:</span><span class="sxs-lookup"><span data-stu-id="ecf32-115">That is, the following property declaration:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="ecf32-116">implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="ecf32-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

<span data-ttu-id="ecf32-117">implementa a propriedade `Name` na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="ecf32-117">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="ecf32-118">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="ecf32-118">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="ecf32-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="ecf32-119">See also</span></span>

- [<span data-ttu-id="ecf32-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ecf32-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ecf32-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ecf32-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="ecf32-122">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="ecf32-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="ecf32-123">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="ecf32-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="ecf32-124">Indexadores</span><span class="sxs-lookup"><span data-stu-id="ecf32-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="ecf32-125">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ecf32-125">Interfaces</span></span>](../interfaces/index.md)
