---
title: "&lt;permissão&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="4ea77-102">&lt;permissão&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ea77-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="4ea77-103">Especifica uma permissão necessária para o membro.</span><span class="sxs-lookup"><span data-stu-id="4ea77-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ea77-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ea77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ea77-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="4ea77-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="4ea77-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4ea77-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="4ea77-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4ea77-108">Coloque `member` entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="4ea77-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4ea77-109">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="4ea77-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ea77-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ea77-110">Remarks</span></span>  
 <span data-ttu-id="4ea77-111">Use o `<permission>` marca para documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="4ea77-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="4ea77-112">Use o <xref:System.Security.PermissionSet> classe para especificar o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="4ea77-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="4ea77-113">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4ea77-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea77-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ea77-114">Example</span></span>  
 <span data-ttu-id="4ea77-115">Este exemplo usa o `<permission>` marcas para descrever que o <xref:System.Security.Permissions.FileIOPermission> é necessária para o `ReadFile` método.</span><span class="sxs-lookup"><span data-stu-id="4ea77-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4ea77-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ea77-116">See Also</span></span>  
 [<span data-ttu-id="4ea77-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="4ea77-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
