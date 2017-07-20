---
title: "Armazenando dados e lendo na Área de Transferência (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 06a97ffe88fdae344b07d04b6ce560d4c163d431
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Armazenando dados e lendo na Área de Transferência (Visual Basic)
A Área de Transferência pode ser usada para armazenar dados, como texto e imagens. Como a Área de Transferência é compartilhada por todos os processos ativos, ela pode ser usada para transferir dados entre eles. O objeto `My.Computer.Clipboard` permite que você acesse facilmente a Área de Transferência e leia e grave nela.  
  
## <a name="reading-from-the-clipboard"></a>Lendo da Área de Transferência  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> para ler o texto da Área de Transferência. O código a seguir lê o texto e o mostra em uma caixa de mensagem. Deve haver texto armazenado na Área de Transferência para que o exemplo seja executado corretamente.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Área de Transferência**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> para recuperar uma imagem da Área de Transferência. Este exemplo verifica se há alguma imagem na Área de Transferência antes de recuperá-la e atribuí-la à `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Área de Transferência**. Para obter mais informações, consulte [Trechos de código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
 Itens colocados na Área de Transferência persistirão mesmo após o aplicativo ser encerrado.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Determinando o tipo de arquivo armazenado na Área de Transferência  
 Os dados na área de transferência podem ter várias formas diferentes, como texto, um arquivo de áudio ou uma imagem. Para determinar que tipo de arquivo está na Área de Transferência, você pode usar métodos como <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> e <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Você poderá usar o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> se quiser verificar um formato personalizado.  
  
 Use a função `ContainsImage` para determinar se os dados contidos na Área de Transferência são uma imagem. O código a seguir verifica se os dados são uma imagem e relata de acordo.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Limpando a Área de Transferência  
 O método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> limpa a Área de Transferência. Como a Área de Transferência é compartilhada por outros processos, limpá-la pode ter nesses processos.  
  
 O código a seguir mostra como usar o método `Clear`.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Gravando na Área de Transferência  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> para gravar texto na Área de Transferência. O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 O método `SetText` pode aceitar um parâmetro de formato que contém um tipo de <xref:System.Windows.Forms.TextDataFormat>. O código a seguir grava a cadeia de caracteres "This is a test string" na Área de Transferência como um texto RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> para gravar dados na Área de Transferência. Este exemplo grava o `DataObject``dataChunk` na Área de Transferência no formato personalizado `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Use o método <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> para gravar dados de áudio na Área de Transferência. Este exemplo cria a matriz de bytes `musicReader`, lê o arquivo `cool.wav` nela e o grava na Área de Transferência.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Como a Área de Transferência pode ser acessada por outros usuários, não a use para armazenar informações confidenciais, como senhas ou dados confidenciais.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [Como ler dados de objeto de um arquivo XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [Como gravar dados de objeto em um arquivo XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
