---
title: Definir atributos de fonte para controle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744857"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="2d97f-102">Como definir atributos de fonte para o controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d97f-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="2d97f-103">O controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms tem várias opções para formatar o texto exibido.</span><span class="sxs-lookup"><span data-stu-id="2d97f-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="2d97f-104">Você pode tornar os caracteres selecionados em negrito, sublinhados ou itálicos usando a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d97f-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="2d97f-105">Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="2d97f-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="2d97f-106">A propriedade <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> permite que você altere a cor dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="2d97f-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="2d97f-107">Para alterar a aparência dos caracteres</span><span class="sxs-lookup"><span data-stu-id="2d97f-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="2d97f-108">Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> como uma fonte apropriada.</span><span class="sxs-lookup"><span data-stu-id="2d97f-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="2d97f-109">Para permitir que os usuários definam a família de fontes, o tamanho e a face de tipos em um aplicativo, você normalmente usará o componente <xref:System.Windows.Forms.FontDialog>.</span><span class="sxs-lookup"><span data-stu-id="2d97f-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="2d97f-110">Para obter uma visão geral, consulte [Visão geral do componente FontDialog](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2d97f-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="2d97f-111">Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> como uma cor apropriada.</span><span class="sxs-lookup"><span data-stu-id="2d97f-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="2d97f-112">Para permitir que os usuários definam a cor em um aplicativo, você normalmente usará o componente <xref:System.Windows.Forms.ColorDialog>.</span><span class="sxs-lookup"><span data-stu-id="2d97f-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="2d97f-113">Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2d97f-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="2d97f-114">Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção.</span><span class="sxs-lookup"><span data-stu-id="2d97f-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="2d97f-115">Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d97f-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d97f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d97f-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="2d97f-117">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2d97f-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="2d97f-118">Controles a serem usados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d97f-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
