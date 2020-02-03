---
title: Criar uma tabela de pesquisa para o controle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737373"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Como criar uma tabela de pesquisa para um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
Às vezes, é útil exibir dados em um formato amigável em um formulário do Windows Forms, porém, armazene os dados em um formato que seja mais significativo para o programa. Por exemplo, um formulário de pedido de alimentos pode exibir os itens de menu por nome em uma caixa de listagem. No entanto, a tabela de dados que registra a ordem conteria os números de identificação exclusivos que representam os alimentos. As tabelas a seguir mostram um exemplo de como armazenar e exibir dados de formulários de pedidos de alimentos.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Quantidade|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|{1&gt;Nome&lt;1}|  
|--------|----------|  
|12|Batata|  
|13|Frango|  
  
 Nesse cenário, uma tabela, **OrderDetailsTable**, armazena as informações reais que serão exibidas e salvas. Porém, para economizar espaço, isso é feito de maneira bastante enigmática. A outra tabela, **ItemTable**, contém apenas informações relacionadas à aparência sobre qual número de ID é equivalente a qual nome de alimento, e nada sobre os pedidos de alimentos.  
  
 O **MyTable** está conectado ao <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>ou <xref:System.Windows.Forms.CheckedListBox> controle por meio de três propriedades. A propriedade `DataSource` contém o nome dessa tabela. A propriedade `DisplayMember` contém a coluna de dados da tabela que você deseja exibir no controle (o nome do alimento). A propriedade `ValueMember` contém a coluna de dados dessa tabela com as informações armazenadas (o número de ID).  
  
 O **OrderDetailsTable** é conectado ao controle por sua coleção de associações, acessada por meio da propriedade <xref:System.Windows.Forms.Control.DataBindings%2A>. Ao adicionar um objeto de associação à coleção, uma propriedade de controle será conectada a um membro de dados específico (a coluna de números de ID) em uma fonte de dados (**OrderDetailsTable**). Quando uma seleção é feita no controle, a entrada de formulário será salva nessa tabela.  
  
### <a name="to-create-a-lookup-table"></a>Criar uma tabela de pesquisa  
  
1. Adicione um controle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>ou <xref:System.Windows.Forms.CheckedListBox> ao formulário.  
  
2. Conecte-se à fonte de dados.  
  
3. Estabeleça uma relação de dados entre as duas tabelas. Consulte [Introdução a Objetos DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).  
  
4. Defina as propriedades a seguir. Elas podem ser definidos no código ou no designer.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|A tabela que contém informações sobre qual número de ID é equivalente a qual item. No cenário anterior, isso é `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|A coluna da tabela de fonte de dados a ser exibida no controle. No cenário anterior, isso é `"Name"` (para definir no código, use aspas).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|A coluna da tabela de fonte de dados que contém as informações armazenadas. No cenário anterior, isso é `"ID"` (para definir no código, use aspas).|  
  
5. Em um procedimento, chame o método <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> da classe <xref:System.Windows.Forms.ControlBindingsCollection> para associar a propriedade <xref:System.Windows.Forms.ListControl.SelectedValue%2A> do controle à tabela que está gravando a entrada do formulário. Você também pode fazer isso no designer, em vez de no código, acessando a propriedade <xref:System.Windows.Forms.Control.DataBindings%2A> do controle na janela **Propriedades** . No cenário anterior, isso é `OrderDetailsTable` e a coluna é `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Associação de dados e o Windows Forms](../data-binding-and-windows-forms.md)
- [Visão geral do controle ListBox](listbox-control-overview-windows-forms.md)
- [Visão geral do controle ComboBox](combobox-control-overview-windows-forms.md)
- [Visão geral do controle CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
