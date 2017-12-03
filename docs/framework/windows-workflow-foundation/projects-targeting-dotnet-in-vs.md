---
title: Escrever projetos direcionar o.NET Framework 3.0 e os 3,5 no Visual Studio 2010
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="940cf-102">Escrever projetos direcionar o.NET Framework 3.0 e os 3,5 no Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="940cf-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="940cf-103">Você pode usar [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] para criar projetos que destinam-se a versão 3,0 ou 3,5 de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="940cf-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="940cf-104">Este tópico descreve como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="940cf-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="940cf-105">Ao adicionar atividades, certifique-se de que a versão desejada de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] está definida.</span><span class="sxs-lookup"><span data-stu-id="940cf-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="940cf-106">Alterar a versão de destino de fluxo de trabalho depois que as atividades são adicionadas fará com que o fluxo de trabalho para validação de falha.</span><span class="sxs-lookup"><span data-stu-id="940cf-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="940cf-107">Abrindo fluxos de trabalho existentes em [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] que possuem. .NET Framework 3,5 atividades causará um erro em `this.SetValue()`.</span><span class="sxs-lookup"><span data-stu-id="940cf-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="940cf-108">Para abrir projetos criados com as versões anteriores do. Framework .NET, primeiro abre um fluxo de trabalho em branco no designer e adicione a. Atividade líquida de Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="940cf-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="940cf-109">Para criar o .NET Framework 3.0 ou 3,5 com um projeto Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="940cf-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="940cf-110">Abra [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="940cf-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="940cf-111">Selecione **arquivo**, **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="940cf-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="940cf-112">Na lista suspensa na parte superior da caixa de diálogo, selecione a versão desejada de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="940cf-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="940cf-113">Para atualizar a versão de destino do.NET Framework</span><span class="sxs-lookup"><span data-stu-id="940cf-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="940cf-114">Clique com botão direito no projeto no Gerenciador de soluções e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="940cf-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="940cf-115">No **Framework de destino** lista suspensa, selecione a versão desejada.</span><span class="sxs-lookup"><span data-stu-id="940cf-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
