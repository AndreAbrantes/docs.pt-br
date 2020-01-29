---
title: Criar uma interface do usuário de multipainel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
ms.openlocfilehash: 4b168a6d566e20814d4403f90e157d80efe3bf12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731343"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Como criar uma interface do usuário multipainel com Windows Forms
No procedimento a seguir, você vai criar uma interface do usuário com vários painéis semelhante à que é usada no Microsoft Outlook, com uma lista **Pasta**, um painel **Mensagens** e um painel **Visualização**. Essa organização é obtida principalmente por meio de controles de encaixe com o formulário.  
  
 Ao encaixar um controle, você determina a qual borda do contêiner pai um controle é fixado. Portanto, se você definir a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Right>, a borda direita do controle será encaixada na borda direita de seu controle pai. Além disso, a borda encaixada do controle será redimensionada para corresponder à borda de sua caixa de controles. Para obter mais informações sobre como a propriedade de <xref:System.Windows.Forms.SplitContainer.Dock%2A> funciona, consulte [como: encaixar controles em Windows Forms](how-to-dock-controls-on-windows-forms.md).  
  
 Este procedimento se concentra em organizar o <xref:System.Windows.Forms.SplitContainer> e os outros controles no formulário, não na adição de funcionalidade para fazer com que o aplicativo simule o Microsoft Outlook.  
  
 Para criar essa interface do usuário, coloque todos os controles dentro de um controle de <xref:System.Windows.Forms.SplitContainer>, que contém um controle de <xref:System.Windows.Forms.TreeView> no painel esquerdo. O painel à direita do controle de <xref:System.Windows.Forms.SplitContainer> contém um segundo controle de <xref:System.Windows.Forms.SplitContainer> com um controle de <xref:System.Windows.Forms.ListView> acima de um controle de <xref:System.Windows.Forms.RichTextBox>. Esses <xref:System.Windows.Forms.SplitContainer> controles habilitam o redimensionamento independente dos outros controles no formulário. Você pode adaptar as técnicas neste procedimento para criar interfaces do usuário personalizadas.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Para criar uma interface do usuário no estilo do Outlook de forma programática  
  
1. Em um formulário, declare cada controle que compõe a interface do usuário. Para este exemplo, use os controles <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>e <xref:System.Windows.Forms.RichTextBox> para imitar a interface do usuário do Microsoft Outlook.  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2. Crie um procedimento que define a interface do usuário. O código a seguir define as propriedades para que o formulário seja semelhante à interface do usuário no Microsoft Outlook. No entanto, usando outros controles ou encaixando-os de maneira diferente, é fácil criar outras interfaces do usuário igualmente flexíveis.  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3. Em Visual Basic, adicione uma chamada para o procedimento que você acabou de criar no procedimento de `New()`. No Visual C#, adicione esta linha de código ao construtor para a classe Form.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.SplitContainer>
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
- [Como criar uma interface do usuário com vários painéis com o Windows Forms usando o designer](create-a-multipane-user-interface-with-wf-using-the-designer.md)
