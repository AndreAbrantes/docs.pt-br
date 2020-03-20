---
title: 'Como: Escolha as impressoras conectadas ao computador de um usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182608"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Como escolher as impressoras conectadas ao computador de um usuário no Windows Forms
Geralmente, os usuários escolhem uma impressora diferente da impressora padrão para imprimir. Você pode permitir que os usuários escolham uma impressora <xref:System.Windows.Forms.PrintDialog> entre as instaladas atualmente usando o componente. Através <xref:System.Windows.Forms.PrintDialog> do componente, <xref:System.Windows.Forms.DialogResult> <xref:System.Windows.Forms.PrintDialog> o componente é capturado e usado para selecionar a impressora.  
  
 No procedimento a seguir, um arquivo de texto é selecionado para ser impresso na impressora padrão. A <xref:System.Windows.Forms.PrintDialog> aula é então instanciada.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Para escolher uma impressora e imprimir um arquivo  
  
1. Selecione a impressora a <xref:System.Windows.Forms.PrintDialog> ser usada usando o componente.  
  
     No exemplo de código a seguir, há dois eventos que estão sendo manipulados. No primeiro, <xref:System.Windows.Forms.Button> um evento <xref:System.Windows.Forms.Control.Click> de <xref:System.Windows.Forms.PrintDialog> controle, a classe é instanciada e a <xref:System.Windows.Forms.DialogResult> impressora selecionada pelo usuário é capturada na propriedade.  
  
     No segundo evento, <xref:System.Drawing.Printing.PrintDocument.PrintPage> no <xref:System.Drawing.Printing.PrintDocument> caso do componente, um documento de amostra é impresso na impressora especificada.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Confira também

- [Suporte à impressão no Windows Forms](windows-forms-print-support.md)
