---
title: "#<a name=\"warning-c-reference\"></a>warning (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#warning'
helpviewer_keywords: '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a><span data-ttu-id="78fb9-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="78fb9-102">#warning (C# Reference)</span></span>
<span data-ttu-id="78fb9-103">O `#warning` permite gerar um aviso de um nível um em um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="78fb9-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="78fb9-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="78fb9-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="78fb9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="78fb9-105">Remarks</span></span>  
 <span data-ttu-id="78fb9-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="78fb9-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="78fb9-107">Também é possível gerar um erro definido pelo usuário com [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="78fb9-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78fb9-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78fb9-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="78fb9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78fb9-109">See Also</span></span>  
 [<span data-ttu-id="78fb9-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="78fb9-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="78fb9-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="78fb9-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="78fb9-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="78fb9-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
