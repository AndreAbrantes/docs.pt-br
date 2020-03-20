---
title: Vincular o controle datagrid a uma fonte de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182249"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Como associar o controle DataGrid dos Windows Forms a uma fonte de dados
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 O controle <xref:System.Windows.Forms.DataGrid> do Windows Forms foi projetado especificamente para exibir informações de uma fonte de dados. Você vincula o controle no <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> tempo de execução chamando o método. Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Associar dados ao controle DataGrid por com programação  
  
1. Grave código para preencher o conjunto de dados.  
  
     Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.  
  
     O código exato usado depende do local em que o conjunto de dados está recebendo dados. Se o conjunto de dados estiver sendo preenchido diretamente `Fill` a partir de um banco de dados, você normalmente `DsCategories1`chamará o método de um adaptador de dados, como no exemplo a seguir, que preenche um conjunto de dados chamado :  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Se o conjunto de dados estiver sendo preenchido de um serviço Web XML, geralmente uma instância do serviço será criada no seu código e uma chamada será feita para um de seus métodos retornar um conjunto de dados. Em seguida, mescle o conjunto de dados do serviço Web XML ao seu conjunto de dados local. O exemplo a seguir mostra como você pode criar `CategoriesService`uma `GetCategories` instância de um serviço Web XML chamado `DsCategories1`, chamar seu método e mesclar o conjunto de dados resultante em um conjunto de dados local chamado :  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Ligue <xref:System.Windows.Forms.DataGrid> para o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método do controle, passando-o pela fonte de dados e um membro de dados. Se você não precisar passar explicitamente um membro de dados, passe uma cadeia de caracteres vazia.  
  
    > [!NOTE]
    > Se você estiver vinculando a grade pela primeira <xref:System.Windows.Forms.DataGrid.DataSource%2A> vez, você pode definir os controles e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades. No entanto, não será possível redefinir essas propriedades depois de serem definidas. Portanto, recomenda-se que você sempre <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> use o método.  
  
     O exemplo a seguir mostra como você pode se vincular `DsCustomers1`programáticamente à tabela Clientes em um conjunto de dados chamado :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Se a tabela Clientes for a única tabela no conjunto de dados, também seria possível associar a grade da seguinte forma:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Opcional) Adicione os estilos apropriados de tabela e coluna à grade. Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.  
  
## <a name="see-also"></a>Confira também

- [Visão geral do controle DataGrid](datagrid-control-overview-windows-forms.md)
- [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Vinculação de dados dos Windows Forms](../windows-forms-data-binding.md)
