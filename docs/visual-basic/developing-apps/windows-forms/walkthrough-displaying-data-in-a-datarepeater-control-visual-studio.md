---
title: 'Passo a passo: Exibindo dados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 09f15c94c3d5a3387935c8d3f4758c0ecfd7cfcd
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)
Este passo a passo fornece um cenário básico do início ao fim para exibir dados associados em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="prerequisite"></a>Pré-requisito  
 Este passo a passo requer o banco de dados de exemplo Northwind.  
  
 Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).  
  
## <a name="overview"></a>Visão geral  
 A primeira parte deste passo a passo consiste em quatro tarefas principais:  
  
-   Criando uma solução.  
  
-   Adicionando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Adicionando uma fonte de dados.  
  
-   Adicionando controles ligados a dados.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Criando uma solução DataRepeater  
 Na primeira etapa, você pode criar um projeto e solução.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Para criar uma solução DataRepeater  
  
1.  No Visual Studio **arquivo** menu, clique em **novo projeto**.  
  
2.  No **tipos de projeto** painel o **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.  
  
3.  No **modelos** painel, clique em **Windows Forms Application**.  
  
4.  Na caixa **Nome**, digite `DataRepeaterApp`.  
  
5.  Clique em **OK**.  
  
     O Designer de Formulários do Windows é aberto.  
  
6.  Selecione o formulário no Designer de formulários do Windows. No **propriedades** janela, defina a **tamanho** propriedade `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Adicionando um controle DataRepeater  
 Nesta etapa, você adiciona um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle ao formulário.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-datarepeater-control"></a>Para adicionar um controle DataRepeater  
  
1.  Sobre o **exibição** menu, clique em **ferramentas**.  
  
     O **Toolbox** é aberto.  
  
2.  Selecione o **Visual Basic PowerPacks** guia.  
  
3.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle para **Form1**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  Na janela Propriedades, defina o **local** propriedade `0, 25`.  
  
5.  Definir o **tamanho** propriedade `460, 600`.  
  
## <a name="adding-a-data-source"></a>Adicionando uma fonte de dados  
 Nesta etapa, você adiciona uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-data-source"></a>Para adicionar uma fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.  
  
3.  Selecione **banco de dados** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.  
  
4.  Sobre o **escolha sua Conexão de dados** , execute uma das seguintes etapas:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.  
  
         -ou-  
  
    -   Clique em **nova Conexão** para configurar uma nova conexão de dados. Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
5.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.  
  
    > [!NOTE]
    >  Se uma caixa de diálogo for exibida, clique em **Sim** para salvar o arquivo ao seu projeto.  
  
6.  Clique em **próximo** sobre o **salvar a cadeia de Conexão no arquivo de configuração de aplicativo** página.  
  
7.  Expanda o **tabelas** nó a **Choose Your Database Objects** página.  
  
8.  Marque as caixas de seleção ao lado de **clientes** e **pedidos** tabelas e clique **concluir**.  
  
     **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.  
  
## <a name="adding-data-bound-controls"></a>Adicionar controles ligados a dados  
 Nesta etapa, você adiciona controles ligados a dados para <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-data-bound-controls"></a>Para adicionar controles de associação de dados  
  
1.  No **fontes de dados** janela, selecione o nó de nível superior para o **clientes** tabela.  
  
2.  Altere o tipo subjacente da tabela para **detalhes** clicando **detalhes** na lista suspensa no nó da tabela.  
  
3.  Selecione o **clientes** nó da tabela e arraste-o para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Um <xref:System.Windows.Forms.BindingNavigator>controle é adicionado ao formulário e o **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, e **CustomersBindingNavigator** componentes são adicionados à bandeja de componentes.</xref:System.Windows.Forms.BindingNavigator>  
  
4.  Selecione todos os campos e seus rótulos associados e posicioná-las próximo à borda esquerda da região de modelo de item.  
  
5.  Selecione os últimos cinco campos (**região**, **CEP**, **país**, **Phone**, e **Fax**) e seus rótulos associados e movê-los até e à direita dos seis primeiros campos.  
  
6.  Selecione o modelo de item (região superior do controle).  
  
7.  Na janela Propriedades, defina o **tamanho** propriedade `427, 170`.  
  
 Neste ponto, você tem um aplicativo funcional que exibirá uma lista de repetição de clientes. Você pode pressionar F5 para executar o aplicativo, alterar os dados e adicionar ou excluir registros de cliente.  
  
 As próximas etapas opcionais, você aprenderá a personalizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="next-steps-optional"></a>Próximas etapas (opcionais)  
 Nesta parte do passo a passo consiste em quatro tarefas opcionais:  
  
-   Alterando a aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Impedindo que os usuários adicionem ou excluam registros.  
  
-   Adicionando recursos de pesquisa para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Adicionando uma tabela mestre e de detalhes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Alterando a aparência do controle DataRepeater  
 Esta etapa opcional, você altera o `BackColor` do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Você também adicionar código para exibir linhas em cores alternadas e alterar um rótulo `ForeColor` condicionalmente.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Para alterar a aparência do controle  
  
1.  No Windows Forms Designer, selecione a região principal (inferior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Na janela Propriedades, defina o `BackColor` propriedade em branco.  
  
3.  Clique duas vezes o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>para abrir o Editor de código.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  No Editor de código, lista suspensa de eventos, clique em **DrawItem**.  
  
5.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, adicione o código a seguir para alternar a `BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[&#1; VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, adicione o seguinte código para alterar o `ForeColor` de um rótulo, dependendo de uma condição:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[N º&2; VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Pressione F5 para executar o aplicativo e ver as personalizações.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Impedindo que os usuários adicionem ou excluam registros  
 Esta etapa opcional, você adiciona código que impede que os usuários adicionem ou excluam registros de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Para impedir que usuários adicionando e excluindo registros  
  
1.  No Windows Forms Designer, clique duas vezes no formulário para abrir o Editor de códigos.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!code-cs[N º&3; VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n º&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Na lista suspensa Nome da classe, clique em **BindingNavigatorDeleteItem**. Na lista suspensa Nome do método, clique em **EnabledChanged**.  
  
4.  Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-cs[N º&4; VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n º&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource>permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.</xref:System.Windows.Forms.BindingSource>  
  
5.  Pressione F5 para executar o aplicativo. Observe que o **DeleteItem** botão está desabilitado e você não pode excluir itens, pressionando a tecla DELETE.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Adicionando funcionalidade de pesquisa ao controle DataRepeater  
 Nesta etapa opcional, você implementa a capacidade de pesquisar um valor na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Se a cadeia de caracteres for encontrada, o controle seleciona o item que contém o valor e o item é movido para a exibição.  
  
#### <a name="to-add-search-capability"></a>Para adicionar o recurso de pesquisa  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox>  
  
     Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.  
  
3.  Arraste um <xref:System.Windows.Forms.Button>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button> Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  Na janela Propriedades, altere o **nome** propriedade **SearchButton**. Alterar o **texto** propriedade **pesquisa**.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button>de controle para abrir o Editor de códigos e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</xref:System.Windows.Forms.Button>  
  
     [!code-cs[N º&5; VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n º&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Pressione F5 para executar o aplicativo. Digite uma ID de cliente em **SearchTextBox** e clique no **pesquisa** botão.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Adicionando um mestre e a tabela de detalhes para DataRepeater  
 Nesta etapa opcional, você adicionar um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle para exibir os pedidos relacionados para cada cliente.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-master-and-detail-table"></a>Para adicionar uma tabela mestre e de detalhes  
  
1.  Arraste uma segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle de **Visual Basic PowerPacks** guia o **ferramentas** para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Na janela Propriedades, defina o **local** propriedade `465, 25`.  
  
3.  Definir o **tamanho** propriedade `315, 600`.  
  
4.  No **fontes de dados** janela, expanda o **clientes** nó e selecione o nó de detalhe para o **pedidos** tabela.  
  
5.  Altere o tipo subjacente desse **pedidos** tabela detalhes clicando em **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste esta **pedidos** nó de tabela para a região de modelo de item (região superior) do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Um **OrdersBindingSource** componente e uma **OrdersTableAdapter** componente são adicionados à bandeja de componentes.  
  
7.  Pressione F5 para executar o aplicativo. Quando você seleciona cada cliente na primeira <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controlar os pedidos para aquele cliente são exibidos na segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como: alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Como: exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [Como: pesquisar dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Como: desabilitar a adição e exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
