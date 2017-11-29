---
title: "Como criar um formulário do Windows Form com uma forma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 981256c2447a53aef8e1ea676db38ce693d1337e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shaped-windows-form"></a><span data-ttu-id="40bf2-102">Como criar um formulário do Windows Form com uma forma</span><span class="sxs-lookup"><span data-stu-id="40bf2-102">How to: Create a Shaped Windows Form</span></span>
<span data-ttu-id="40bf2-103">Este exemplo dá uma forma elíptica redimensiona com o formulário de um formulário.</span><span class="sxs-lookup"><span data-stu-id="40bf2-103">This example gives a form an elliptical shape that resizes with the form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40bf2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40bf2-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40bf2-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="40bf2-105">Compiling the Code</span></span>  
 <span data-ttu-id="40bf2-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="40bf2-106">This example requires:</span></span>  
  
-   <span data-ttu-id="40bf2-107">Referências aos namespaces <xref:System.Windows.Forms> e <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="40bf2-107">References to the <xref:System.Windows.Forms> and <xref:System.Drawing> namespaces.</span></span>  
  
 <span data-ttu-id="40bf2-108">Este exemplo substitui o <xref:System.Windows.Forms.Control.OnPaint%2A> método para alterar a forma do formulário.</span><span class="sxs-lookup"><span data-stu-id="40bf2-108">This example overrides the <xref:System.Windows.Forms.Control.OnPaint%2A> method to change the shape of the form.</span></span> <span data-ttu-id="40bf2-109">Para usar esse código, copie a declaração de método, bem como o código de desenho dentro do método.</span><span class="sxs-lookup"><span data-stu-id="40bf2-109">To use this code, copy the method declaration as well as the drawing code inside the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bf2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40bf2-110">See Also</span></span>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Drawing.Region>  
 <xref:System.Drawing>  
 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 [<span data-ttu-id="40bf2-111">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="40bf2-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
