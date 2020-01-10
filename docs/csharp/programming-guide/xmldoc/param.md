---
title: <param> – Guia de Programação em C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711721"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="cbe1e-102">\<param> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="cbe1e-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cbe1e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbe1e-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbe1e-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbe1e-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="cbe1e-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-105">The name of a method parameter.</span></span> <span data-ttu-id="cbe1e-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="cbe1e-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="cbe1e-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbe1e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbe1e-108">Remarks</span></span>  
 <span data-ttu-id="cbe1e-109">A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="cbe1e-110">Para documentar vários parâmetros, use várias marcas \<param>.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="cbe1e-111">O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="cbe1e-112">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cbe1e-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe1e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cbe1e-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cbe1e-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="cbe1e-114">See also</span></span>

- [<span data-ttu-id="cbe1e-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cbe1e-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cbe1e-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="cbe1e-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
