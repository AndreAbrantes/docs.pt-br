---
title: "Como inserir um elemento em texto de forma programática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b200489c4b7fb06f2eb98c0ec9c84da42f18a395
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="e447b-102">Como inserir um elemento em texto de forma programática</span><span class="sxs-lookup"><span data-stu-id="e447b-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="e447b-103">O exemplo a seguir mostra como usar duas <xref:System.Windows.Documents.TextPointer> objetos para especificar um intervalo dentro do texto para aplicar um <xref:System.Windows.Documents.Span> elemento.</span><span class="sxs-lookup"><span data-stu-id="e447b-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e447b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e447b-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="e447b-105">A ilustração a seguir mostra a aparência de neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="e447b-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="e447b-106">![Um elemento Span aplicado a um intervalo de texto](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="e447b-106">![A Span element applied to a range of text](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e447b-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e447b-107">See Also</span></span>  
 [<span data-ttu-id="e447b-108">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="e447b-108">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
