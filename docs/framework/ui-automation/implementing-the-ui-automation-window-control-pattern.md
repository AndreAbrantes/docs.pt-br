---
title: Implementando o Padrão Controle de Window de Automação de Interface de Usuário
description: Examine as diretrizes e convenções para implementar o padrão de controle de janela na automação da interface do usuário. Conheça os membros necessários para a interface IWindowProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: b43884393974e6f2863da6a4a5ca8f305e5a160c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286091"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="e108d-104">Implementando o Padrão Controle de Window de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="e108d-104">Implementing the UI Automation Window Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="e108d-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e108d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e108d-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="e108d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e108d-107">Este tópico apresenta as diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IWindowProvider> , incluindo informações sobre <xref:System.Windows.Automation.WindowPattern> Propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="e108d-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="e108d-108">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="e108d-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="e108d-109">O <xref:System.Windows.Automation.WindowPattern> padrão de controle é usado para dar suporte a controles que fornecem funcionalidade básica baseada em janela dentro de uma GUI (interface gráfica do usuário) tradicional.</span><span class="sxs-lookup"><span data-stu-id="e108d-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="e108d-110">Exemplos de controles que devem implementar esse padrão de controle incluem janelas de aplicativo de nível superior, janelas filhas de MDI (interface de vários documentos), controles de painel dividido redimensionável, caixas de diálogo modais e janelas de ajuda de balão.</span><span class="sxs-lookup"><span data-stu-id="e108d-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e108d-111">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="e108d-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="e108d-112">Ao implementar o padrão de controle Window, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="e108d-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e108d-113">Para dar suporte à capacidade de modificar o tamanho da janela e a posição da tela usando a automação da interface do usuário, um controle deve implementar além <xref:System.Windows.Automation.Provider.ITransformProvider> do <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="e108d-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e108d-114">Controles que contêm barras de título e elementos de barra de título que permitem que o controle seja movido, redimensionado, maximizado, minimizado ou fechado normalmente são necessários para implementar <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="e108d-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e108d-115">Controles como pop-ups de dica de ferramenta e caixas suspensas de caixa de combinação ou de menu normalmente não implementam <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="e108d-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e108d-116">As janelas de ajuda de balão são diferenciadas de pop-ups de dica de ferramenta básica pelo provisionamento de um botão de fechamento de janela.</span><span class="sxs-lookup"><span data-stu-id="e108d-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="e108d-117">O modo de tela inteira não tem suporte do IWindowProvider, pois ele é específico ao recurso para um aplicativo e não é um comportamento de janela típico.</span><span class="sxs-lookup"><span data-stu-id="e108d-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>

## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="e108d-118">Membros necessários para IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="e108d-118">Required Members for IWindowProvider</span></span>  

 <span data-ttu-id="e108d-119">As propriedades, os métodos e os eventos a seguir são necessários para a interface IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="e108d-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="e108d-120">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="e108d-120">Required member</span></span>|<span data-ttu-id="e108d-121">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="e108d-121">Member type</span></span>|<span data-ttu-id="e108d-122">Observações</span><span class="sxs-lookup"><span data-stu-id="e108d-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="e108d-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-123">Property</span></span>|<span data-ttu-id="e108d-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="e108d-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-125">Property</span></span>|<span data-ttu-id="e108d-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="e108d-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-127">Property</span></span>|<span data-ttu-id="e108d-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="e108d-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-129">Property</span></span>|<span data-ttu-id="e108d-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="e108d-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-131">Property</span></span>|<span data-ttu-id="e108d-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="e108d-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e108d-133">Property</span></span>|<span data-ttu-id="e108d-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="e108d-135">Método</span><span class="sxs-lookup"><span data-stu-id="e108d-135">Method</span></span>|<span data-ttu-id="e108d-136">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="e108d-137">Método</span><span class="sxs-lookup"><span data-stu-id="e108d-137">Method</span></span>|<span data-ttu-id="e108d-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="e108d-139">Método</span><span class="sxs-lookup"><span data-stu-id="e108d-139">Method</span></span>|<span data-ttu-id="e108d-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="e108d-141">Evento</span><span class="sxs-lookup"><span data-stu-id="e108d-141">Event</span></span>|<span data-ttu-id="e108d-142">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="e108d-143">Evento</span><span class="sxs-lookup"><span data-stu-id="e108d-143">Event</span></span>|<span data-ttu-id="e108d-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e108d-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="e108d-145">Evento</span><span class="sxs-lookup"><span data-stu-id="e108d-145">Event</span></span>|<span data-ttu-id="e108d-146">Não é garantido que seja <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="e108d-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="e108d-147">Exceções</span><span class="sxs-lookup"><span data-stu-id="e108d-147">Exceptions</span></span>  

 <span data-ttu-id="e108d-148">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="e108d-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e108d-149">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="e108d-149">Exception type</span></span>|<span data-ttu-id="e108d-150">Condição</span><span class="sxs-lookup"><span data-stu-id="e108d-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="e108d-151">-Quando um controle não dá suporte a um comportamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="e108d-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="e108d-152">-Quando o parâmetro não é um número válido.</span><span class="sxs-lookup"><span data-stu-id="e108d-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e108d-153">Veja também</span><span class="sxs-lookup"><span data-stu-id="e108d-153">See also</span></span>

- [<span data-ttu-id="e108d-154">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="e108d-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e108d-155">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e108d-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e108d-156">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="e108d-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e108d-157">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e108d-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e108d-158">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e108d-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
