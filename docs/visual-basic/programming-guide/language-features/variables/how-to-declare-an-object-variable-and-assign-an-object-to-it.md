---
title: Como declarar uma variável de objeto e atribuir um objeto a ela
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410497"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="71a22-102">Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71a22-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="71a22-103">Você declara uma variável do [tipo de dados Object](../../../language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="71a22-103">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="71a22-104">Você atribui um objeto a tal variável colocando o objeto após o sinal de igual ( `=` ) em uma instrução de atribuição ou uma cláusula de inicialização.</span><span class="sxs-lookup"><span data-stu-id="71a22-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="71a22-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71a22-105">Example</span></span>

<span data-ttu-id="71a22-106">O exemplo a seguir declara uma `Object` variável e atribui a instância atual a ela.</span><span class="sxs-lookup"><span data-stu-id="71a22-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="71a22-107">Você pode combinar a declaração e a atribuição inicializando a variável como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="71a22-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="71a22-108">O exemplo a seguir é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="71a22-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="71a22-109">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="71a22-109">Compile the code</span></span>

<span data-ttu-id="71a22-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="71a22-110">This example requires:</span></span>

- <span data-ttu-id="71a22-111">Uma referência ao <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="71a22-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="71a22-112">Uma classe, estrutura ou módulo no qual colocar a `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="71a22-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="71a22-113">Um procedimento no qual colocar a instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="71a22-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="71a22-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="71a22-114">See also</span></span>

- [<span data-ttu-id="71a22-115">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="71a22-115">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="71a22-116">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="71a22-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="71a22-117">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="71a22-117">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="71a22-118">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="71a22-118">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="71a22-119">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="71a22-119">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="71a22-120">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="71a22-120">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="71a22-121">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="71a22-121">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
