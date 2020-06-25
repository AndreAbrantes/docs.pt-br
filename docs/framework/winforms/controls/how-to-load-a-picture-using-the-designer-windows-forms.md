---
title: Como carregar uma imagem usando o designer
description: Saiba como usar o controle PictureBox Windows Forms para carregar e exibir uma imagem em um formulário em tempo de design.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325595"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="b9b22-103">Como carregar uma imagem usando o designer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b9b22-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="b9b22-104">Com o controle de Windows Forms <xref:System.Windows.Forms.PictureBox> , você pode carregar e exibir uma imagem em um formulário em tempo de design, definindo a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade como uma imagem válida.</span><span class="sxs-lookup"><span data-stu-id="b9b22-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="b9b22-105">A tabela a seguir mostra os tipos de arquivo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b9b22-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="b9b22-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="b9b22-106">Type</span></span>|<span data-ttu-id="b9b22-107">Extensão de nome de arquivo</span><span class="sxs-lookup"><span data-stu-id="b9b22-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="b9b22-108">Bitmap</span><span class="sxs-lookup"><span data-stu-id="b9b22-108">Bitmap</span></span>|<span data-ttu-id="b9b22-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="b9b22-109">.bmp</span></span>|
|<span data-ttu-id="b9b22-110">Ícone</span><span class="sxs-lookup"><span data-stu-id="b9b22-110">Icon</span></span>|<span data-ttu-id="b9b22-111">.ico</span><span class="sxs-lookup"><span data-stu-id="b9b22-111">.ico</span></span>|
|<span data-ttu-id="b9b22-112">GIF</span><span class="sxs-lookup"><span data-stu-id="b9b22-112">GIF</span></span>|<span data-ttu-id="b9b22-113">.gif</span><span class="sxs-lookup"><span data-stu-id="b9b22-113">.gif</span></span>|
|<span data-ttu-id="b9b22-114">Metarquivo</span><span class="sxs-lookup"><span data-stu-id="b9b22-114">Metafile</span></span>|<span data-ttu-id="b9b22-115">.wmf</span><span class="sxs-lookup"><span data-stu-id="b9b22-115">.wmf</span></span>|
|<span data-ttu-id="b9b22-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="b9b22-116">JPEG</span></span>|<span data-ttu-id="b9b22-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="b9b22-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="b9b22-118">Para exibir uma imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="b9b22-118">To display a picture at design time</span></span>

1. <span data-ttu-id="b9b22-119">Desenhe um <xref:System.Windows.Forms.PictureBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="b9b22-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="b9b22-120">Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade e, em seguida, selecione o botão de reticências para exibir a caixa de diálogo **abrir** .</span><span class="sxs-lookup"><span data-stu-id="b9b22-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="b9b22-121">Se você estiver procurando um tipo de arquivo específico (por exemplo, arquivos. gif), selecione-o na caixa **arquivos do tipo** .</span><span class="sxs-lookup"><span data-stu-id="b9b22-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="b9b22-122">Selecione o arquivo que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="b9b22-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="b9b22-123">Para limpar a imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="b9b22-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="b9b22-124">Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b9b22-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="b9b22-125">Clique com o botão direito do mouse na pequena imagem em miniatura que aparece à esquerda do nome do objeto de imagem e escolha **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="b9b22-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9b22-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9b22-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="b9b22-127">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="b9b22-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="b9b22-128">Como modificar o tamanho ou a colocação de uma imagem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b9b22-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="b9b22-129">Como definir imagens em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b9b22-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="b9b22-130">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="b9b22-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
