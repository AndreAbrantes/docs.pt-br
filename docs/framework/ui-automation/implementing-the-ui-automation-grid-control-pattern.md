---
title: Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
description: Entenda as diretrizes e convenções para implementar o padrão de controle de grade GridPattern na automação da interface do usuário. Aprenda a implementar a interface IGridProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 2290fd91c8eee0ab969eef2827d3c7440ef21e20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274875"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="b9392-104">Implementando o Padrão de Controle Grid de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-104">Implementing the UI Automation Grid Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="b9392-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="b9392-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b9392-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="b9392-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b9392-107">Este tópico apresenta as diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IGridProvider> , incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="b9392-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b9392-108">Links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="b9392-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="b9392-109">O <xref:System.Windows.Automation.GridPattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="b9392-109">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="b9392-110">Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser atravessado por linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="b9392-110">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="b9392-111">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b9392-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b9392-112">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="b9392-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="b9392-113">Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="b9392-113">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b9392-114">As coordenadas de grade são baseadas em zero com o canto superior esquerdo (ou célula superior direita, dependendo da localidade) com coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="b9392-114">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="b9392-115">Se uma célula estiver vazia, um elemento de automação da interface do usuário ainda deverá ser retornado para dar suporte à <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> propriedade dessa célula.</span><span class="sxs-lookup"><span data-stu-id="b9392-115">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="b9392-116">Isso é possível quando o layout dos elementos filho na grade é semelhante a uma matriz irregular (Veja o exemplo abaixo).</span><span class="sxs-lookup"><span data-stu-id="b9392-116">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="b9392-117">![Exibição do Windows Explorer mostrando layout irregular.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="b9392-117">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="b9392-118">Exemplo de um controle de grade com coordenadas vazias</span><span class="sxs-lookup"><span data-stu-id="b9392-118">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="b9392-119">Uma grade com um único item ainda é necessária para implementar <xref:System.Windows.Automation.Provider.IGridProvider> se for considerada logicamente como uma grade.</span><span class="sxs-lookup"><span data-stu-id="b9392-119">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="b9392-120">O número de itens filho na grade é irrelevante.</span><span class="sxs-lookup"><span data-stu-id="b9392-120">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="b9392-121">Linhas e colunas ocultas, dependendo da implementação do provedor, podem ser carregadas na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore e, portanto, serão refletidas <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> nas <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="b9392-121">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="b9392-122">Se as linhas e colunas ocultas ainda não tiverem sido carregadas, elas não deverão ser contadas.</span><span class="sxs-lookup"><span data-stu-id="b9392-122">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="b9392-123"><xref:System.Windows.Automation.Provider.IGridProvider> não habilita a manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> deve ser implementado para habilitar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="b9392-123"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="b9392-124">Use um <xref:System.Windows.Automation.StructureChangedEventHandler> para escutar alterações estruturais ou de layout na grade, como células que foram adicionadas, removidas ou mescladas.</span><span class="sxs-lookup"><span data-stu-id="b9392-124">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="b9392-125">Use um <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para acompanhar a passagem pelos itens ou células de uma grade.</span><span class="sxs-lookup"><span data-stu-id="b9392-125">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>

## <a name="required-members-for-igridprovider"></a><span data-ttu-id="b9392-126">Membros necessários para IGridProvider</span><span class="sxs-lookup"><span data-stu-id="b9392-126">Required Members for IGridProvider</span></span>  

 <span data-ttu-id="b9392-127">As propriedades e os métodos a seguir são necessários para implementar a interface IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="b9392-127">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="b9392-128">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="b9392-128">Required members</span></span>|<span data-ttu-id="b9392-129">Type</span><span class="sxs-lookup"><span data-stu-id="b9392-129">Type</span></span>|<span data-ttu-id="b9392-130">Observações</span><span class="sxs-lookup"><span data-stu-id="b9392-130">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="b9392-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b9392-131">Property</span></span>|<span data-ttu-id="b9392-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9392-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="b9392-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b9392-133">Property</span></span>|<span data-ttu-id="b9392-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9392-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="b9392-135">Método</span><span class="sxs-lookup"><span data-stu-id="b9392-135">Method</span></span>|<span data-ttu-id="b9392-136">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9392-136">None</span></span>|  
  
 <span data-ttu-id="b9392-137">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="b9392-137">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="b9392-138">Exceções</span><span class="sxs-lookup"><span data-stu-id="b9392-138">Exceptions</span></span>  

 <span data-ttu-id="b9392-139">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="b9392-139">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b9392-140">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="b9392-140">Exception type</span></span>|<span data-ttu-id="b9392-141">Condição</span><span class="sxs-lookup"><span data-stu-id="b9392-141">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="b9392-142">-Se a coordenada de linha solicitada for maior do que a <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> ou a coordenada de coluna for maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="b9392-142">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="b9392-143">-Se uma das coordenadas de linha ou coluna solicitada for menor que zero.</span><span class="sxs-lookup"><span data-stu-id="b9392-143">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9392-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9392-144">See also</span></span>

- [<span data-ttu-id="b9392-145">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b9392-146">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b9392-147">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="b9392-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b9392-148">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-148">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="b9392-149">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-149">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b9392-150">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="b9392-150">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
