---
title: Suporte de automação de interface de usuário para o Tipo de Controle Calendário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 5d2fce49e44b70e56c289d3e377a207e75d0b831
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741274"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Calendário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de calendário. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a propriedade <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade, padrões de controle e eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Os controles de calendário permitem que um usuário determine facilmente a data e selecione outras datas.  
  
 As seções a seguir definem a estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], propriedades, padrões de controle e eventos necessários para o tipo de controle Calendar. Os requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplicam a todos os controles de calendário, sejam [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve a exibição de controle e a exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertence a controles de calendário e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Calendário<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Cabeçalho (0 ou 1)</li><li>HeaderItem (0 ou 7; a quantidade depende de quantos dias são exibidos em colunas)</li><li>ListItem (a quantidade depende de quantos dias são exibidos)</li><li>Botão (0 ou 2; para exibição de calendário de paginação)</li></ul></li></ul>|Calendário<br /><br /> -ListItem (a quantidade depende de quantos dias são exibidos)|  
  
 Os controles de calendário podem ser representados em vários formatos diferentes na interface do usuário. Os únicos controles garantidos estão no modo de exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] são os controles de grade de dados, cabeçalho, item de cabeçalho e item de lista.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cujo valor ou definição é especialmente relevante para os controles de calendário. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|{1&gt;Observações&lt;1}|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|Com suporte se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis e você executar um teste de clique especializado, substitua e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Calendário|Esse valor é o mesmo para todas as estruturas de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de calendário é sempre incluído na exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle Calendar sempre é incluído na exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte observações.|O rótulo do controle de documento. Normalmente, o título do documento é usado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|calendário|Cadeia de caracteres localizada correspondente ao tipo de controle de calendário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O controle Calendar normalmente obtém seu nome a partir da data atual do dia.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista os padrões de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de calendário. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
|Propriedade padrão de controle/padrão|Suporte do|{1&gt;Observações&lt;1}|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Sim|O controle Calendar sempre dá suporte ao padrão de grade porque os dias em um mês são itens que podem ser navegados espacialmente.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|A maioria dos controles de calendário dá suporte à inversão de exibição por página. O padrão de rolagem é recomendado para dar suporte à navegação de paginação.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Depende|A maioria dos controles de calendário mantém um dia, mês ou ano específico como uma seleção do subelemento. Alguns calendários são multiselecionáveis e outros apenas de seleção única.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Sim|O controle Calendar sempre tem um cabeçalho dentro de sua subárvore para os dias da semana, portanto, o padrão de tabela deve ter suporte.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Não|O padrão de controle de valor não é necessário para controles de calendário porque você não pode definir o valor diretamente no controle. Se uma data específica estiver associada ao controle, as informações deverão ser fornecidas pelo padrão de controle de seleção.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista os eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de calendário. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento|Suporte do|{1&gt;Observações&lt;1}|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> evento de alteração de propriedade.|Depende|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Scroll, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
