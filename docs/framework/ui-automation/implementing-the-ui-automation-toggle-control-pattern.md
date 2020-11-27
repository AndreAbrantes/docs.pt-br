---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
description: Examine as diretrizes e convenções para implementar o padrão de controle de alternância na automação da interface do usuário. Conheça os membros necessários para a interface IToggleProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 865f225d749c29fb1ec80507daeffda82ae8816e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265629"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="c4b3f-104">Implementando o padrão de controle Toggle de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-104">Implementing the UI Automation Toggle Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="c4b3f-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c4b3f-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="c4b3f-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c4b3f-107">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IToggleProvider> , incluindo informações sobre métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="c4b3f-108">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c4b3f-109">O <xref:System.Windows.Automation.TogglePattern> padrão de controle é usado para dar suporte a controles que podem percorrer um conjunto de Estados e manter um estado depois de definido.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-109">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="c4b3f-110">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c4b3f-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c4b3f-111">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="c4b3f-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="c4b3f-112">Ao implementar o padrão de controle de alternância, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="c4b3f-112">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="c4b3f-113">Os controles que não mantêm o estado quando ativados, como botões, botões da barra de ferramentas e hiperlinks, devem implementar <xref:System.Windows.Automation.Provider.IInvokeProvider> em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-113">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="c4b3f-114">Um controle deve percorrer seu <xref:System.Windows.Automation.ToggleState> na seguinte ordem: <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> e, se houver suporte, <xref:System.Windows.Automation.ToggleState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="c4b3f-114">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="c4b3f-115"><xref:System.Windows.Automation.TogglePattern> não fornece um método SetState (newState) devido a problemas em torno da configuração direta de uma caixa de seleção de três Estados sem percorrer a <xref:System.Windows.Automation.ToggleState> sequência apropriada.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-115"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="c4b3f-116">O controle RadioButton não implementa <xref:System.Windows.Automation.Provider.IToggleProvider> , pois não é capaz de percorrer seus Estados válidos.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-116">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>

## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="c4b3f-117">Membros necessários para IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="c4b3f-117">Required Members for IToggleProvider</span></span>  

 <span data-ttu-id="c4b3f-118">As propriedades e os métodos a seguir são necessários para implementar o <xref:System.Windows.Automation.Provider.IToggleProvider> .</span><span class="sxs-lookup"><span data-stu-id="c4b3f-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="c4b3f-119">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-119">Required member</span></span>|<span data-ttu-id="c4b3f-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="c4b3f-120">Member type</span></span>|<span data-ttu-id="c4b3f-121">Observações</span><span class="sxs-lookup"><span data-stu-id="c4b3f-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="c4b3f-122">Método</span><span class="sxs-lookup"><span data-stu-id="c4b3f-122">Method</span></span>|<span data-ttu-id="c4b3f-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c4b3f-123">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="c4b3f-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c4b3f-124">Property</span></span>|<span data-ttu-id="c4b3f-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c4b3f-125">None</span></span>|  
  
 <span data-ttu-id="c4b3f-126">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-126">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="c4b3f-127">Exceções</span><span class="sxs-lookup"><span data-stu-id="c4b3f-127">Exceptions</span></span>  

 <span data-ttu-id="c4b3f-128">Este padrão de controle não tem nenhuma exceção associada.</span><span class="sxs-lookup"><span data-stu-id="c4b3f-128">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b3f-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="c4b3f-129">See also</span></span>

- [<span data-ttu-id="c4b3f-130">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-130">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c4b3f-131">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-131">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c4b3f-132">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="c4b3f-132">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c4b3f-133">Obter o estado Toggle de uma caixa de seleção usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-133">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="c4b3f-134">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="c4b3f-135">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c4b3f-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
