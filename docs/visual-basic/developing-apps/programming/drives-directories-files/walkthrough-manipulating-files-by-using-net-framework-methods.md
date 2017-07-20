---
title: "Manipulando arquivos usando métodos do .NET Framework (Visual Basic) | Microsoft Docs"
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
- I/O [Visual Basic], walkthroughs
- text files, writing to
- reading text files
- text, writing to files
- files, searching
- StreamReader class, walkthroughs
- files, accessing
- I/O [Visual Basic], writing text to files
- writing to files, walkthroughs
- StreamWriter class, walkthroughs
- text files, reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
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
ms.openlocfilehash: a16d2168548dadf9210b653d90ce229d99469b64
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework (Visual Basic)
Estas instruções passo a passo demonstram como abrir e ler um arquivo usando a classe <xref:System.IO.StreamReader>, verificar se um arquivo está sendo acessado, pesquisar uma cadeia de caracteres dentro de um arquivo lido com uma instância da classe <xref:System.IO.StreamReader> e gravar em um arquivo usando a classe <xref:System.IO.StreamWriter>.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-application"></a>Criando o aplicativo  
 Inicie o [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] e comece o projeto criando um formulário que o usuário pode usar para gravar no arquivo designado.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  No menu **Arquivo**, selecione **Novo Projeto**.  
  
2.  No painel **Novo Projeto**, clique em **Aplicativos do Windows**.  
  
3.  Na caixa **Nome**, digite `MyDiary` e clique em **OK**.  
  
     O [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] adiciona o projeto ao **Gerenciador de Soluções** e o **Designer de Formulários do Windows** é aberto.  
  
4.  Adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.  
  
|**Object**|**Propriedades**|**Value**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Submit`<br /><br /> **Enviar entrada**|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Clear`<br /><br /> **Limpar entrada**|  
|<xref:System.Windows.Forms.TextBox>|**Nome**<br /><br /> **Texto**<br /><br /> **Multilinha**|`Entry`<br /><br /> **Digite algo.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Gravando no arquivo  
 Para adicionar a capacidade de gravar em um arquivo por meio do aplicativo, use a classe <xref:System.IO.StreamWriter>. <xref:System.IO.StreamWriter> foi criado para a saída de caracteres em uma determinada codificação, enquanto a classe <xref:System.IO.Stream> foi criada para entrada e saída em bytes. Use <xref:System.IO.StreamWriter> para gravar linhas de informações em um arquivo de texto padrão. Para saber mais sobre a classe <xref:System.IO.StreamWriter>, veja <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Para adicionar a funcionalidade de gravação  
  
1.  No menu **Exibição**, escolha **Código** para abrir o Editor de código.  
  
2.  Como o aplicativo faz referência ao namespace <xref:System.IO>, adicione as seguintes instruções ao início do seu código, antes da declaração de classe para o formulário, que inicia `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Antes de gravar no arquivo, você precisa criar uma instância de uma classe <xref:System.IO.StreamWriter>.  
  
3.  No menu **Exibição**, escolha **Designer** para voltar para o **Designer de Formulários do Windows**. Clique duas vezes no botão `Submit` para criar um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão e adicione o código a seguir.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  O IDE (ambiente de desenvolvimento integrado) do Visual Studio retornará ao Editor de código e posicionará o ponto de inserção dentro do manipulador de eventos, no qual você deve adicionar o código.  
  
1.  Para gravar o arquivo, use o método <xref:System.IO.StreamWriter.Write%2A> da classe <xref:System.IO.StreamWriter>. Adicione o código a seguir diretamente após `Dim fw As StreamWriter`. Você não precisa se preocupar se uma exceção será gerada caso o arquivo não seja encontrado, porque ele será criado se ainda não existir.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Certifique-se de que o usuário não possa enviar uma entrada em branco adicionando o código a seguir diretamente após `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Como este é uma diário, o usuário desejará atribuir uma data a cada entrada. Insira o código a seguir após `fw = New StreamWriter("C:\MyDiary.txt", True)` para definir a variável `Today` como a data atual.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Por fim, anexe o código para limpar a <xref:System.Windows.Forms.TextBox>. Adicione o seguinte código ao evento <xref:System.Windows.Forms.Control.Click> do botão `Clear`.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>Adicionando recursos de exibição ao diário  
 Nesta seção, você adiciona um recurso que exibe a última entrada em `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Você também pode adicionar uma <xref:System.Windows.Forms.ComboBox> que exiba várias entradas e a partir da qual um usuário pode selecionar uma entrada para exibir o `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Uma instância da classe <xref:System.IO.StreamReader> é lida de `MyDiary.txt`. Como a classe <xref:System.IO.StreamWriter>, o <xref:System.IO.StreamReader> deve ser usado com arquivos de texto.  
  
 Para esta seção do passo a passo, adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.  
  
|Controle|Propriedades|Valores|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Nome**<br /><br /> **Visível**<br /><br /> **Size**<br /><br /> **Multilinha**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`Display`<br /><br /> **Vídeo**|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**|`GetEntries`<br /><br /> **Obter entradas**|  
|<xref:System.Windows.Forms.ComboBox>|**Nome**<br /><br /> **Texto**<br /><br /> **Habilitado**|`PickEntries`<br /><br /> **Selecionar uma entrada**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>Para popular a caixa de combinação  
  
1.  A `PickEntries`<xref:System.Windows.Forms.ComboBox> é usada para exibir as datas em que um usuário envia cada entrada, para que o usuário possa selecionar uma entrada de uma data específica. Crie um identificador de evento <xref:System.Windows.Forms.Control.Click> para o botão `GetEntries` e adicione o seguinte código.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  Para testar seu código, pressione F5 para compilar o aplicativo e, então, clique em **Obter entradas**. Clique na seta do menu suspenso no <xref:System.Windows.Forms.ComboBox> para exibir as datas de entrada.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Para escolher e exibir entradas individuais  
  
1.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `Display` e adicione o seguinte código.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  Para testar seu código, pressione F5 para compilar o aplicativo e, então, envie uma entrada. Clique em **Obter Entradas**, selecione uma entrada da <xref:System.Windows.Forms.ComboBox> e clique em **Exibir**. Os conteúdos da entrada selecionada são exibidos no `DisplayEntry`<xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Habilitando usuários a excluir ou modificar entradas  
 Por fim, você pode incluir uma funcionalidade adicional que permite que os usuários excluam ou modifiquem uma entrada usando os botões `DeleteEntry` e `EditEntry`. Os dois botões permanecem desabilitados a menos que uma entrada seja exibida.  
  
 Adicione os controles na tabela a seguir ao formulário e defina os valores correspondentes para as respectivas propriedades.  
  
|Controle|Propriedades|Valores|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Habilitado**|`DeleteEntry`<br /><br /> **Excluir entrada**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Habilitado**|`EditEntry`<br /><br /> **Editar entrada**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nome**<br /><br /> **Texto**<br /><br /> **Habilitado**|`SubmitEdit`<br /><br /> **Enviar edição**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Para habilitar a exclusão e modificação de entradas  
  
1.  Adicione o seguinte código ao evento <xref:System.Windows.Forms.Control.Click> do botão `Display` , depois de `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `DeleteEntry` e adicione o seguinte código.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Quando um usuário exibe uma entrada, o botão `EditEntry` fica habilitado. Adicione o seguinte código ao evento <xref:System.Windows.Forms.Control.Click> do botão `Display`, depois de `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `EditEntry` e adicione o seguinte código.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Crie um manipulador de eventos <xref:System.Windows.Forms.Control.Click> para o botão `SubmitEdit` e adicione o seguinte código  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 Para testar seu código, pressione F5 para compilar o aplicativo. Clique em **Obter Entradas**, selecione uma entrada e clique em **Exibir**. A entrada aparece na `DisplayEntry`<xref:System.Windows.Forms.TextBox>. Clique em **Editar entrada**. A entrada aparece na `Entry`<xref:System.Windows.Forms.TextBox>. Edite a entrada na `Entry`<xref:System.Windows.Forms.TextBox> e clique em **Enviar Edição**. Abra o arquivo `MyDiary.txt` para confirmar a correção. Agora, selecione uma entrada e clique em **Excluir entrada**. Quando o <xref:System.Windows.Forms.MessageBox> solicita confirmação, clique em **OK**. Feche o aplicativo e abra `MyDiary.txt` para confirmar a exclusão.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [Explicações Passo a Passo](../../../../visual-basic/walkthroughs.md)

