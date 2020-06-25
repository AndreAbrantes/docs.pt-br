---
title: Como navegar até uma URL com o controle WebBrowser
description: Saiba como usar o Windows Forms WebBrowser. navegar pelo controle para navegar até uma URL específica. Saiba também como determinar quando o novo documento será carregado.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325570"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="e1d5a-104">Como navegar até uma URL com o controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="e1d5a-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="e1d5a-105">O exemplo de código a seguir demonstra como navegar o <xref:System.Windows.Forms.WebBrowser> controle para uma URL específica.</span><span class="sxs-lookup"><span data-stu-id="e1d5a-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="e1d5a-106">Para determinar quando o novo documento está totalmente carregado, manipule o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento.</span><span class="sxs-lookup"><span data-stu-id="e1d5a-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="e1d5a-107">Para ver uma demonstração desse evento, consulte [como: imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="e1d5a-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1d5a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1d5a-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="e1d5a-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e1d5a-109">Compiling the Code</span></span>
 <span data-ttu-id="e1d5a-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e1d5a-110">This example requires:</span></span>

- <span data-ttu-id="e1d5a-111">Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="e1d5a-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="e1d5a-112">Referências aos assemblies `System` e `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="e1d5a-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1d5a-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="e1d5a-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="e1d5a-114">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="e1d5a-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="e1d5a-115">Como imprimir com um controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="e1d5a-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
