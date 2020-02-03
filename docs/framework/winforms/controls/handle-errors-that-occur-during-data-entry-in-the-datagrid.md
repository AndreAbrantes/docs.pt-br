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
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="44b3a-102">Como identificar erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b3a-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="44b3a-103">O exemplo de código a seguir demonstra como usar o controle <xref:System.Windows.Forms.DataGridView> para relatar erros de entrada de dados para o usuário.</span><span class="sxs-lookup"><span data-stu-id="44b3a-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="44b3a-104">Para obter uma explicação completa deste exemplo de código, consulte [Walkthrough: tratamento de erros que ocorrem durante a entrada de dados no controle Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="44b3a-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b3a-105">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="44b3a-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44b3a-106">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="44b3a-106">Compiling the Code</span></span>  
 <span data-ttu-id="44b3a-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="44b3a-107">This example requires:</span></span>  
  
- <span data-ttu-id="44b3a-108">Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.</span><span class="sxs-lookup"><span data-stu-id="44b3a-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="44b3a-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="44b3a-109">.NET Framework Security</span></span>  
 <span data-ttu-id="44b3a-110">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="44b3a-110">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="44b3a-111">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44b3a-111">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="44b3a-112">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="44b3a-112">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b3a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44b3a-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="44b3a-114">Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b3a-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="44b3a-115">Entrada de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b3a-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b3a-116">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b3a-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b3a-117">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="44b3a-117">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
