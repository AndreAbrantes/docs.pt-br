---
title: Para analisar o código-fonte LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e39b1686269442044beb73bb7e572738832bec27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164578"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="38710-102">Para analisar o código-fonte LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="38710-102">Analyzing LINQ to SQL Source Code</span></span>

<span data-ttu-id="38710-103">Usando as seguintes etapas, você pode produzir o código-fonte de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="38710-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="38710-104">Você pode comparar elementos modelo de objeto com os elementos de base de dados melhor para ver como os itens diferentes são mapeados.</span><span class="sxs-lookup"><span data-stu-id="38710-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38710-105">Os desenvolvedores que usam o Visual Studio podem usar o o/R Designer para produzir esse código.</span><span class="sxs-lookup"><span data-stu-id="38710-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="38710-106">Se você ainda não tiver o base de dados de exemplo Northwind no seu computador de desenvolvimento, você poderá baixá-lo gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="38710-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="38710-107">Para obter mais informações, consulte [baixar bancos de dados de exemplo](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="38710-107">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="38710-108">Use a ferramenta de linha de comando SqlMetal para gerar um arquivo de origem Visual Basic ou C#.</span><span class="sxs-lookup"><span data-stu-id="38710-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="38710-109">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="38710-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="38710-110">Digitando os seguintes comandos em um prompt de comando, você pode gerar os arquivos de origem Visual Basic e C# que incluem procedimentos armazenados e funções:</span><span class="sxs-lookup"><span data-stu-id="38710-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="38710-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="38710-111">See also</span></span>

- [<span data-ttu-id="38710-112">Referência</span><span class="sxs-lookup"><span data-stu-id="38710-112">Reference</span></span>](reference.md)
- [<span data-ttu-id="38710-113">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="38710-113">Background Information</span></span>](background-information.md)
