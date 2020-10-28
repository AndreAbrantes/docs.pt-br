---
title: Manipulações básicas de cadeia de caracteres no .NET
description: Veja um exemplo que chama vários métodos de cadeia de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889121"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="509fb-103">Como: executar manipulações de cadeias de caracteres básicas no .NET</span><span class="sxs-lookup"><span data-stu-id="509fb-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="509fb-104">O exemplo a seguir usa alguns dos métodos discutidos nos tópicos de [Operações de cadeias de caracteres básicas](basic-string-operations.md) para construir uma classe que realiza manipulações de cadeia de caracteres de uma maneira que pode ser encontrada em um aplicativo real.</span><span class="sxs-lookup"><span data-stu-id="509fb-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="509fb-105">A classe `MailToData` armazena o nome e endereço de um indivíduo em propriedades separadas e fornece uma maneira de combinar os campos `City`, `State` e `Zip` em uma única cadeia de caracteres para exibição para o usuário.</span><span class="sxs-lookup"><span data-stu-id="509fb-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="509fb-106">Além disso, a classe permite que o usuário insira as informações de cidade, estado e CEP como uma única cadeia de caracteres. O aplicativo automaticamente analisa a única cadeia de caracteres e insere as informações adequadas na propriedade correspondente.</span><span class="sxs-lookup"><span data-stu-id="509fb-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="509fb-107">Para simplificar, este exemplo usa um aplicativo de console com uma interface de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="509fb-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="509fb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="509fb-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="509fb-109">Quando o código anterior é executado, o usuário é solicitado a inserir seu nome e endereço.</span><span class="sxs-lookup"><span data-stu-id="509fb-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="509fb-110">O aplicativo coloca as informações nas propriedades adequadas e exibe as informações de volta para o usuário, criando uma única cadeia de caracteres que exibe as informações de cidade, estado e CEP.</span><span class="sxs-lookup"><span data-stu-id="509fb-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509fb-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="509fb-111">See also</span></span>

- [<span data-ttu-id="509fb-112">Operações básicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="509fb-112">Basic String Operations</span></span>](basic-string-operations.md)
