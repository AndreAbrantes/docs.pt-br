---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871707"
---
# <a name="c-visual-basic"></a><span data-ttu-id="04152-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04152-101">\<c> (Visual Basic)</span></span>

<span data-ttu-id="04152-102">Indica que o texto dentro de uma descrição é o código.</span><span class="sxs-lookup"><span data-stu-id="04152-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04152-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04152-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="04152-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04152-104">Parameters</span></span>  
  
|<span data-ttu-id="04152-105">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="04152-105">Parameter</span></span>|<span data-ttu-id="04152-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="04152-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="04152-107">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="04152-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04152-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="04152-108">Remarks</span></span>  

 <span data-ttu-id="04152-109">A `<c>` marca fornece uma maneira de indicar que o texto dentro de uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="04152-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="04152-110">Use [\<code>](code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="04152-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="04152-111">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="04152-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04152-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04152-112">Example</span></span>  

 <span data-ttu-id="04152-113">Este exemplo usa a `<c>` marca na seção de resumo para indicar que `Counter` é o código.</span><span class="sxs-lookup"><span data-stu-id="04152-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="04152-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="04152-114">See also</span></span>

- [<span data-ttu-id="04152-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="04152-115">XML Comment Tags</span></span>](index.md)
