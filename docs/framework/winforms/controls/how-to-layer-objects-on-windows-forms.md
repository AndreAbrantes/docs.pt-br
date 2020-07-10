---
title: colocar objetos em camadas
description: Saiba como encamar objetos em Windows Forms controles e formulários filho para criar interfaces de usuário mais complexas.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174504"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="87c7b-103">Como: objetos de camada no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87c7b-103">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="87c7b-104">Ao criar uma interface do usuário complexa ou trabalhar com um formulário MDI (interface de múltiplos documentos), geralmente se deseja dispor em camadas controles e formulários filho para criar interfaces do usuário (UI) mais complexas.</span><span class="sxs-lookup"><span data-stu-id="87c7b-104">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="87c7b-105">Para mover e acompanhar controles e janelas no contexto de um grupo, você manipula sua *ordem z*.</span><span class="sxs-lookup"><span data-stu-id="87c7b-105">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="87c7b-106">A ordem z consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário (profundidade).</span><span class="sxs-lookup"><span data-stu-id="87c7b-106">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="87c7b-107">A janela na parte superior da ordem z se sobrepõe a todas as outras janelas.</span><span class="sxs-lookup"><span data-stu-id="87c7b-107">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="87c7b-108">Todas as outras janelas se sobrepõe a janela na parte inferior da ordem z.</span><span class="sxs-lookup"><span data-stu-id="87c7b-108">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="87c7b-109">Dispondo controles em camadas no design time</span><span class="sxs-lookup"><span data-stu-id="87c7b-109">To layer controls at design time</span></span>

1. <span data-ttu-id="87c7b-110">No Visual Studio, selecione um controle que você deseja camada.</span><span class="sxs-lookup"><span data-stu-id="87c7b-110">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="87c7b-111">No menu **Formatar** , selecione **pedido**e, em seguida, selecione **trazer para frente** ou **Enviar para trás**.</span><span class="sxs-lookup"><span data-stu-id="87c7b-111">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="87c7b-112">Dispondo controles em camadas de forma programática</span><span class="sxs-lookup"><span data-stu-id="87c7b-112">To layer controls programmatically</span></span>

<span data-ttu-id="87c7b-113">Use os <xref:System.Windows.Forms.Control.BringToFront%2A> <xref:System.Windows.Forms.Control.SendToBack%2A> métodos e para manipular a ordem z dos controles.</span><span class="sxs-lookup"><span data-stu-id="87c7b-113">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="87c7b-114">Por exemplo, se um <xref:System.Windows.Forms.TextBox> controle, `txtFirstName` , estiver abaixo de outro controle e você quiser tê-lo na parte superior, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="87c7b-114">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> <span data-ttu-id="87c7b-115">Windows Forms dá suporte a *Contenção de controle*.</span><span class="sxs-lookup"><span data-stu-id="87c7b-115">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="87c7b-116">A contenção de controle envolve colocar um número de controles dentro de um controle recipiente, como um número de <xref:System.Windows.Forms.RadioButton> controles dentro de um <xref:System.Windows.Forms.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="87c7b-116">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="87c7b-117">Em seguida, é possível dispor os controles em camadas no controle de contenção.</span><span class="sxs-lookup"><span data-stu-id="87c7b-117">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="87c7b-118">Mover a caixa de grupo move também os controles, já que estes estão contidos dentro dela.</span><span class="sxs-lookup"><span data-stu-id="87c7b-118">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="87c7b-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="87c7b-119">See also</span></span>

- [<span data-ttu-id="87c7b-120">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87c7b-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="87c7b-121">Identificando controles dos Windows Forms individuais e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="87c7b-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="87c7b-122">Controles a serem usados em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87c7b-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="87c7b-123">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="87c7b-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
