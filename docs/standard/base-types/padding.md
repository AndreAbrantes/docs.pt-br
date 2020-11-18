---
title: Como preencher cadeias de caracteres no .NET
description: Saiba como preencher cadeias de caracteres no .NET. Use os métodos String. PadLeft preenche e String. PadRight para adicionar caracteres à esquerda ou à direita para atingir um comprimento total especificado.
ms.date: 03/15/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 9931db1e76e3737ab3803400928169b30c3ecbda
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822939"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="92844-104">Como preencher cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="92844-104">Padding Strings in .NET</span></span>

<span data-ttu-id="92844-105">Use um dos métodos <xref:System.String> a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-105">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="92844-106">O caractere de preenchimento pode ser um espaço ou um caractere especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-106">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="92844-107">A cadeia de caracteres resultante parece estar alinhada à direita ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="92844-107">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="92844-108">Se o tamanho da cadeia de caracteres original já for igual ou maior que o tamanho total desejado, os métodos de preenchimento retornarão a cadeia de caracteres original inalterada. Para obter mais informações, confira as seções **Retornos** das duas sobrecargas dos métodos <xref:System.String.PadLeft%2A?displayProperty=nameWithType> e <xref:System.String.PadRight%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92844-108">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="92844-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="92844-109">Method name</span></span>|<span data-ttu-id="92844-110">Use</span><span class="sxs-lookup"><span data-stu-id="92844-110">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="92844-111">Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-111">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="92844-112">Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-112">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="92844-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="92844-113">PadLeft</span></span>  
 <span data-ttu-id="92844-114">O método <xref:System.String.PadLeft%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-114">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="92844-115">O método <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="92844-115">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="92844-116">O exemplo de código a seguir usa o método <xref:System.String.PadLeft%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="92844-116">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="92844-117">O exemplo exibe “`--------Hello World!`” no console.</span><span class="sxs-lookup"><span data-stu-id="92844-117">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="92844-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="92844-118">PadRight</span></span>  
 <span data-ttu-id="92844-119">O método <xref:System.String.PadRight%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="92844-119">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="92844-120">O método <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="92844-120">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="92844-121">O exemplo de código a seguir usa o método <xref:System.String.PadRight%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="92844-121">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="92844-122">O exemplo exibe “`Hello World!--------`” no console.</span><span class="sxs-lookup"><span data-stu-id="92844-122">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="92844-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="92844-123">See also</span></span>

- [<span data-ttu-id="92844-124">Operações básicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="92844-124">Basic String Operations</span></span>](basic-string-operations.md)
