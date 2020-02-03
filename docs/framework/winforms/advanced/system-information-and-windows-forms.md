---
title: '{1&gt;Informações do sistema&lt;1}'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732583"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="a6e1e-102">Informações do sistema e o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6e1e-102">System Information and Windows Forms</span></span>
<span data-ttu-id="a6e1e-103">Às vezes, é necessário obter informações sobre o computador em que o aplicativo está sendo executado para tomar decisões em seu código.</span><span class="sxs-lookup"><span data-stu-id="a6e1e-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="a6e1e-104">Por exemplo, você pode ter uma função que só é aplicável quando conectada a um domínio de rede específico; Nesse caso, você precisaria de uma maneira de determinar o domínio e desabilitar a função se o domínio não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="a6e1e-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="a6e1e-105">Windows Forms aplicativos podem usar a classe <xref:System.Windows.Forms.SystemInformation> para determinar várias coisas sobre um computador em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6e1e-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="a6e1e-106">O exemplo a seguir demonstra como usar a classe <xref:System.Windows.Forms.SystemInformation> para recuperar o <xref:System.Windows.Forms.SystemInformation.UserName%2A> e <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="a6e1e-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 <span data-ttu-id="a6e1e-107">Todos os membros da classe <xref:System.Windows.Forms.SystemInformation> são somente leitura; Não é possível modificar as configurações de um usuário.</span><span class="sxs-lookup"><span data-stu-id="a6e1e-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="a6e1e-108">Há mais de 100 membros da classe, retornando informações sobre tudo, desde o número de monitores anexados ao computador (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) até o espaçamento de ícones no Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> e <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="a6e1e-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="a6e1e-109">Alguns dos membros mais úteis da classe <xref:System.Windows.Forms.SystemInformation> incluem <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>e <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6e1e-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e1e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6e1e-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="a6e1e-111">Gerenciamento de Energia nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6e1e-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
