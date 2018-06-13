---
title: '#endif (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269971"
---
# <a name="endif-c-reference"></a><span data-ttu-id="2e2c9-102">#endif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2e2c9-102">#endif (C# Reference)</span></span>
<span data-ttu-id="2e2c9-103">O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="2e2c9-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="2e2c9-104">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="2e2c9-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e2c9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e2c9-105">Remarks</span></span>  
 <span data-ttu-id="2e2c9-106">Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="2e2c9-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="2e2c9-107">Consulte [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para obter um exemplo de como usar `#endif`.</span><span class="sxs-lookup"><span data-stu-id="2e2c9-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2c9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e2c9-108">See Also</span></span>  
 [<span data-ttu-id="2e2c9-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2e2c9-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2e2c9-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2e2c9-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2e2c9-111">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="2e2c9-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
