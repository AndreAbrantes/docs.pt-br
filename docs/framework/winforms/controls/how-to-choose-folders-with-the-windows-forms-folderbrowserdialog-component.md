---
title: Escolher pastas com o componente FolderBrowserDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742235"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="0f6a8-102">Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f6a8-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="0f6a8-103">Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="0f6a8-104">O componente Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> permite que você realize essa tarefa facilmente.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="0f6a8-105">Escolher pastas com o componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="0f6a8-105">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="0f6a8-106">Em um procedimento, verifique a propriedade <xref:System.Windows.Forms.Form.DialogResult%2A> do componente de <xref:System.Windows.Forms.FolderBrowserDialog> para ver como a caixa de diálogo foi fechada e obter o valor da propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> do componente de <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="0f6a8-107">Se você precisar definir a pasta superior que aparecerá dentro do modo de exibição de árvore da caixa de diálogo, defina a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, que usa um membro da enumeração <xref:System.Environment.SpecialFolder>.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="0f6a8-108">Além disso, você pode definir a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, que especifica a cadeia de texto que aparece na parte superior da exibição de árvore de navegador de pasta.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="0f6a8-109">No exemplo a seguir, o componente <xref:System.Windows.Forms.FolderBrowserDialog> é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e é solicitado a selecionar uma pasta na qual salvá-la.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="0f6a8-110">Neste exemplo, o nome da pasta é exibido em um controle <xref:System.Windows.Forms.TextBox> no formulário.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="0f6a8-111">É uma boa ideia posicionar o local em uma área editável, como um controle de <xref:System.Windows.Forms.TextBox>, para que os usuários possam editar sua seleção em caso de erro ou outros problemas.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="0f6a8-112">Este exemplo pressupõe um formulário com um componente <xref:System.Windows.Forms.FolderBrowserDialog> e um controle <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

    ```vb
    Public Sub ChooseFolder()
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then
            TextBox1.Text = FolderBrowserDialog1.SelectedPath
        End If
    End Sub
    ```

    ```csharp
    public void ChooseFolder()
    {
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)
        {
            textBox1.Text = folderBrowserDialog1.SelectedPath;
        }
    }
    ```

    ```cpp
    public:
       void ChooseFolder()
       {
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)
          {
             textBox1->Text = folderBrowserDialog1->SelectedPath;
          }
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0f6a8-113">Para usar essa classe, seu assembly requer um nível de privilégio concedido pela propriedade <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>, que faz parte da enumeração <xref:System.Security.Permissions.FileIOPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="0f6a8-114">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="0f6a8-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="0f6a8-115">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0f6a8-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="0f6a8-116">Para obter informações sobre como salvar arquivos, consulte [Como salvar arquivos usando o componente SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="0f6a8-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f6a8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f6a8-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="0f6a8-118">Visão geral do componente FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0f6a8-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="0f6a8-119">Componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="0f6a8-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
