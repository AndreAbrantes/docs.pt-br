---
title: Adicionar ou remover imagens com o componente ImageList
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182294"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="e7215-102">Como adicionar ou remover imagens com o componente ImageList dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7215-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="e7215-103">O componente <xref:System.Windows.Forms.ImageList> Windows Forms é tipicamente preenchido com imagens antes de ser associado a um controle.</span><span class="sxs-lookup"><span data-stu-id="e7215-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="e7215-104">No entanto, você pode adicionar e remover imagens depois de associar a lista de imagens a um controle.</span><span class="sxs-lookup"><span data-stu-id="e7215-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7215-105">Ao remover imagens, <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> verifique se a propriedade de quaisquer controles associados ainda é válida.</span><span class="sxs-lookup"><span data-stu-id="e7215-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="e7215-106">Para adicionar imagens de forma programática</span><span class="sxs-lookup"><span data-stu-id="e7215-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="e7215-107">Use <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> o método de propriedade <xref:System.Windows.Forms.ImageList.Images%2A> da lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="e7215-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="e7215-108">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**.</span><span class="sxs-lookup"><span data-stu-id="e7215-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="e7215-109">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="e7215-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="e7215-110">Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7215-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="e7215-111">O exemplo de código a seguir <xref:System.Windows.Forms.ImageList> requer que você tenha um formulário com um controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="e7215-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="e7215-112">Para adicionar imagens com um valor de chave.</span><span class="sxs-lookup"><span data-stu-id="e7215-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="e7215-113">Use um <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> dos métodos de propriedade <xref:System.Windows.Forms.ImageList.Images%2A> da lista de imagens que leva um valor-chave.</span><span class="sxs-lookup"><span data-stu-id="e7215-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="e7215-114">No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **Meus documentos**.</span><span class="sxs-lookup"><span data-stu-id="e7215-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="e7215-115">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="e7215-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="e7215-116">Escolher esse local também permite que os usuários que têm níveis de acesso ao sistema mínimos executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7215-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="e7215-117">O exemplo de código a seguir <xref:System.Windows.Forms.ImageList> requer que você tenha um formulário com um controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="e7215-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="e7215-118">Para remover todas as imagens de forma programática</span><span class="sxs-lookup"><span data-stu-id="e7215-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="e7215-119">Use <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> o método para remover uma única imagem</span><span class="sxs-lookup"><span data-stu-id="e7215-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="e7215-120">,-ou-</span><span class="sxs-lookup"><span data-stu-id="e7215-120">,-or-</span></span>  
  
     <span data-ttu-id="e7215-121">Use <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> o método para limpar todas as imagens da lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="e7215-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="e7215-122">Para remover imagens por chave</span><span class="sxs-lookup"><span data-stu-id="e7215-122">To remove images by key</span></span>  
  
- <span data-ttu-id="e7215-123">Use <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> o método para remover uma única imagem por sua chave.</span><span class="sxs-lookup"><span data-stu-id="e7215-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7215-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7215-124">See also</span></span>

- [<span data-ttu-id="e7215-125">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="e7215-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="e7215-126">Visão geral do componente ImageList</span><span class="sxs-lookup"><span data-stu-id="e7215-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="e7215-127">Imagens, Bitmaps e Metaarquivos</span><span class="sxs-lookup"><span data-stu-id="e7215-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
