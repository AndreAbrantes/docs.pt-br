---
title: Manipular erros que ocorrem durante a entrada de dados no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 03a13957c80b0ab62afb11efc57cf31e059e5942
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745607"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Como identificar erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms
O exemplo de código a seguir demonstra como usar o controle <xref:System.Windows.Forms.DataGridView> para relatar erros de entrada de dados para o usuário.  
  
 Para obter uma explicação completa deste exemplo de código, consulte [Walkthrough: tratamento de erros que ocorrem durante a entrada de dados no controle Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Entrada de dados no controle DataGridView do Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
