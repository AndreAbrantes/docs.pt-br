---
title: Como exibir botões de opção em um MenuStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735518"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="97bd8-102">Como exibir botões de opção em um MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="97bd8-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="97bd8-103">Botões de opção são semelhantes a caixas de seleção, exceto que os usuários podem selecionar apenas um por vez.</span><span class="sxs-lookup"><span data-stu-id="97bd8-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="97bd8-104">Embora, por padrão, a classe <xref:System.Windows.Forms.ToolStripMenuItem> não forneça comportamento de botão de opção, a classe fornece o comportamento de caixa de seleção que você pode personalizar para implementar o comportamento de botão de opção para itens de menu em um controle de <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="97bd8-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="97bd8-105">Quando a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de um item de menu é `true`, os usuários podem clicar no item para alternar a exibição de uma marca de seleção.</span><span class="sxs-lookup"><span data-stu-id="97bd8-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="97bd8-106">A propriedade <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> indica o estado atual do item.</span><span class="sxs-lookup"><span data-stu-id="97bd8-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="97bd8-107">Para implementar o comportamento básico do botão de opção, você deve garantir que, quando um item for selecionado, defina a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> para o item selecionado anteriormente como `false`.</span><span class="sxs-lookup"><span data-stu-id="97bd8-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="97bd8-108">Os procedimentos a seguir descrevem como implementar isso e funcionalidade adicional em uma classe que herda a classe <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="97bd8-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="97bd8-109">A classe `ToolStripRadioButtonMenuItem` substitui membros como <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> e <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> para fornecer o comportamento de seleção e a aparência dos botões de opção.</span><span class="sxs-lookup"><span data-stu-id="97bd8-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="97bd8-110">Além disso, essa classe substitui a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> de forma que as opções em um submenu sejam desabilitadas, a menos que o item pai esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="97bd8-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="97bd8-111">Implementar o comportamento de seleção do botão de opção</span><span class="sxs-lookup"><span data-stu-id="97bd8-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="97bd8-112">Inicialize a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> como `true` para habilitar a seleção de itens.</span><span class="sxs-lookup"><span data-stu-id="97bd8-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="97bd8-113">Substitua o método <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> para limpar a seleção do item selecionado anteriormente quando um novo item for selecionado.</span><span class="sxs-lookup"><span data-stu-id="97bd8-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="97bd8-114">Substitua o método <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> para garantir que clicar em um item que já tenha sido selecionado não desmarcará a seleção.</span><span class="sxs-lookup"><span data-stu-id="97bd8-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="97bd8-115">Modificar a aparência dos itens do botão de opção</span><span class="sxs-lookup"><span data-stu-id="97bd8-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="97bd8-116">Substitua o método <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> para substituir a marca de seleção padrão por um botão de opção usando a classe <xref:System.Windows.Forms.RadioButtonRenderer>.</span><span class="sxs-lookup"><span data-stu-id="97bd8-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="97bd8-117">Substitua os métodos <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>e <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> para controlar o estado do mouse e garantir que o método <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pinta o estado de botão de opção correto.</span><span class="sxs-lookup"><span data-stu-id="97bd8-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="97bd8-118">Desabilitar as opções em um submenu quando o item pai não está selecionado</span><span class="sxs-lookup"><span data-stu-id="97bd8-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="97bd8-119">Substitua a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> para que o item seja desabilitado quando ele tiver um item pai com um valor de <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de `true` e um valor <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de `false`.</span><span class="sxs-lookup"><span data-stu-id="97bd8-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="97bd8-120">Substitua o método <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> para assinar o evento <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> do item pai.</span><span class="sxs-lookup"><span data-stu-id="97bd8-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="97bd8-121">No manipulador do evento pai-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>, invalida o item para atualizar a exibição com o novo estado habilitado.</span><span class="sxs-lookup"><span data-stu-id="97bd8-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="97bd8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97bd8-122">Example</span></span>

<span data-ttu-id="97bd8-123">O exemplo de código a seguir fornece a classe completa `ToolStripRadioButtonMenuItem` e uma classe <xref:System.Windows.Forms.Form> e `Program` classe para demonstrar o comportamento de botão de opção.</span><span class="sxs-lookup"><span data-stu-id="97bd8-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="97bd8-124">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="97bd8-124">Compiling the Code</span></span>

<span data-ttu-id="97bd8-125">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="97bd8-125">This example requires:</span></span>

- <span data-ttu-id="97bd8-126">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="97bd8-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="97bd8-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="97bd8-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="97bd8-128">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="97bd8-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="97bd8-129">Como implementar um ToolStripRenderer personalizado</span><span class="sxs-lookup"><span data-stu-id="97bd8-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
