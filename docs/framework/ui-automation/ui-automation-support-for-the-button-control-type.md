---
title: Suporte de Automação de Interface de Usuário para o Tipo de Controle Button
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
ms.openlocfilehash: 5087e02db3a5a44ab2e2b97523e793e397a0a914
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741299"
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Suporte de Automação de Interface de Usuário para o Tipo de Controle Button
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de botão. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a propriedade <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade, padrões de controle e eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Um botão é um objeto com o qual um usuário interage para executar uma ação como os botões **OK** e **Cancelar** em uma caixa de diálogo. O controle de botão é um controle simples para expor porque ele é mapeado para um único comando que o usuário deseja concluir.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, propriedades, padrões de controle e eventos necessários para o tipo de controle de botão. Os requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplicam a todos os controles de botão, sejam [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve a exibição de controle e a exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertence a controles de botão e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Botão<br /><br /> -Imagem (0 ou mais)<br />-Texto (0 ou mais)|Botão|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cujo valor ou definição é especialmente relevante para os controles que implementam o tipo de controle de botão (como controles de botão). Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Value|{1&gt;Observações&lt;1}|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|Consulte observações.|O controle de botão normalmente deve dar suporte a uma tecla aceleradora para permitir que um usuário final execute a ação que ele representa rapidamente do teclado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|Com suporte se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis e você executar um teste de clique especializado, substitua e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Botão|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte observações.|O texto de ajuda pode indicar qual será o resultado final da ativação do botão. Normalmente, esse é o mesmo tipo de informações apresentadas por meio de uma dica de ferramenta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de botão sempre deve ser conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de botão sempre deve ser um controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Os controles de botão são rotulados automaticamente por seu conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Button|Cadeia de caracteres localizada correspondente ao tipo de controle de botão.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O nome do controle de botão é o texto usado para rotulá-lo. Sempre que uma imagem é usada para rotular um botão, o texto alternativo deve ser fornecido para a propriedade Name do botão.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista os padrões de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de botão. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte do|{1&gt;Observações&lt;1}|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Consulte observações.|Todos os botões devem dar suporte ao padrão de controle Invoke ou ao padrão de controle toggle. Invoke tem suporte quando o botão executa um comando na solicitação do usuário. Esse comando é mapeado para uma única operação, como recortar, copiar, colar ou excluir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Consulte observações.|Todos os botões devem dar suporte ao padrão de controle Invoke ou ao padrão de controle toggle. A alternância terá suporte se o botão puder ser alternado por uma série de até três Estados. Normalmente, isso é visto como uma opção liga/desliga para recursos específicos.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Consulte observações.|Quando um botão é hospedado como um filho de um botão de divisão, o botão filho pode dar suporte ao padrão ExpandCollapse em vez do padrão Invoke ou toggle. O padrão ExpandCollapse pode ser usado para abrir ou fechar um menu ou outra subestrutura associada ao elemento Button.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista os eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de botão. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento|Suporte do|{1&gt;Observações&lt;1}|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de alteração de propriedade.|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessário|{1&gt;Nenhum&lt;1}|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Se o controle der suporte ao padrão de controle Invoke, ele deverá dar suporte a esse evento.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> evento de alteração de propriedade.|Depende|Se o controle der suporte ao padrão de controle Toggle, ele deverá dar suporte a esse evento.|  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Automation.ControlType.Button>
- [Visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
