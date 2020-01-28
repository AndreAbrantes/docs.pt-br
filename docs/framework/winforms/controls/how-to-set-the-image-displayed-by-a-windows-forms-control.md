---
title: Definir a imagem exibida por um controle
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746878"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="84c1c-102">Como definir a imagem exibida por um controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84c1c-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="84c1c-103">Vários controles de Windows Forms podem exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="84c1c-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="84c1c-104">Essas imagens podem ser ícones que esclarecem a finalidade do controle, como um ícone de disquete em um botão que indica o comando salvar.</span><span class="sxs-lookup"><span data-stu-id="84c1c-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="84c1c-105">Como alternativa, os ícones podem ser imagens de plano de fundo para dar ao controle a aparência e o comportamento que você deseja.</span><span class="sxs-lookup"><span data-stu-id="84c1c-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="84c1c-106">Program</span><span class="sxs-lookup"><span data-stu-id="84c1c-106">Programmatic</span></span>

<span data-ttu-id="84c1c-107">Defina a propriedade `Image` ou `BackgroundImage` do controle como um objeto do tipo <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="84c1c-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="84c1c-108">Em geral, você carregará a imagem de um arquivo usando o método <xref:System.Drawing.Image.FromFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="84c1c-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="84c1c-109">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **minhas imagens** .</span><span class="sxs-lookup"><span data-stu-id="84c1c-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="84c1c-110">A maioria dos computadores que executam o sistema operacional Windows inclui esse diretório.</span><span class="sxs-lookup"><span data-stu-id="84c1c-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="84c1c-111">Isso também permite que os usuários com níveis mínimos de acesso do sistema executem o aplicativo com segurança.</span><span class="sxs-lookup"><span data-stu-id="84c1c-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="84c1c-112">O exemplo de código a seguir requer que você já tenha um formulário com um controle de <xref:System.Windows.Forms.PictureBox> adicionado.</span><span class="sxs-lookup"><span data-stu-id="84c1c-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="84c1c-113">Designer</span><span class="sxs-lookup"><span data-stu-id="84c1c-113">Designer</span></span>

1. <span data-ttu-id="84c1c-114">Na janela **Propriedades** do Visual Studio, selecione a propriedade **Image** ou **BackgroundImage** do controle e, em seguida, selecione as reticências (![botão de reticências no Visual Studio](./media/visual-studio-ellipsis-button.png)) para exibir a caixa de diálogo **selecionar recurso** .</span><span class="sxs-lookup"><span data-stu-id="84c1c-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="84c1c-115">Selecione a imagem que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="84c1c-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="84c1c-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="84c1c-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
