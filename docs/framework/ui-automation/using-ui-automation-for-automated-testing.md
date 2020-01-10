---
title: Usando automação de interface do usuário para testes automatizados
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 59c4076712823faa1602448653680a31b8cd8c69
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741073"
---
# <a name="using-ui-automation-for-automated-testing"></a>Usando automação de interface do usuário para testes automatizados
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral descreve como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pode ser útil como uma estrutura para acesso programático em cenários de teste automatizado.  
  
 o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece um modelo de objeto unificado que permite que todas as estruturas de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] exponham funcionalidades complexas e sofisticadas de uma maneira acessível e facilmente automatizada.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] foi desenvolvido como um sucessor para o Microsoft Acessibilidade Ativa. Acessibilidade Ativa é uma estrutura existente projetada para fornecer uma solução para tornar os controles e os aplicativos acessíveis. A Acessibilidade Ativa não foi projetada com a automação de teste em mente, embora tenha evoluído nessa função devido aos requisitos muito semelhantes de acessibilidade e automação. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], além de fornecer soluções mais refinadas para acessibilidade, também foi projetada especificamente para fornecer uma funcionalidade robusta para testes automatizados. Por exemplo, Acessibilidade Ativa se baseia em uma única interface para expor informações sobre a interface do usuário e coletar as informações necessárias para produtos AT; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] separa os dois modelos.  
  
 Um provedor e um cliente são necessários para implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para que ele seja útil como uma ferramenta de teste automatizada. Os provedores de automação de interface do usuário são aplicativos como o Microsoft Word, o Excel e outros aplicativos ou controles de terceiros baseados no sistema operacional Microsoft Windows. Os clientes de automação da interface do usuário incluem scripts de teste automatizados e aplicativos de tecnologia assistencial.  
  
> [!NOTE]
> A intenção desta visão geral é apresentar os novos e aprimorados recursos de teste automatizados do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Esta visão geral não se destina a fornecer informações sobre recursos de acessibilidade e não abordará acessibilidade além de onde for necessário.  
  
## <a name="ui-automation-in-a-provider"></a>Automação da interface do usuário em um provedor  
 Para que um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] seja automatizado, um desenvolvedor de um aplicativo ou controle deve examinar quais ações um usuário final pode executar no objeto [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] usando a interação padrão do teclado e do mouse.  
  
 Depois que essas ações-chave forem identificadas, os padrões de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] correspondentes (ou seja, os padrões de controle que espelham a funcionalidade e o comportamento do elemento [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]) devem ser implementados no controle. Por exemplo, a interação do usuário com um controle caixa de combinação (como o diálogo Executar) geralmente envolve expandir e recolher a caixa de combinação para ocultar ou exibir uma lista de itens, selecionar um item dessa lista ou adicionar um novo valor por meio de entrada do teclado.  
  
> [!NOTE]
> Com outros modelos de acessibilidade, os desenvolvedores devem reunir informações diretamente de botões, menus ou outros controles individuais. Infelizmente, cada tipo de controle vem em dezenas de pequenas variações. Em outras palavras, embora dez variações de um botão de pressão possam funcionar da mesma forma e executar a mesma função, todas elas devem ser tratadas como controles exclusivos. Não é possível saber que esses controles são funcionalmente equivalentes. Padrões de controle foram desenvolvidos para representar esses comportamentos de controle comuns. Para obter mais informações, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>Implementando a automação da interface do usuário  
 Conforme mencionado anteriormente, sem o modelo unificado fornecido pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], as ferramentas de teste e os desenvolvedores precisam conhecer informações específicas da estrutura para expor propriedades e comportamentos de controles nessa estrutura. Como pode haver várias estruturas de interface do usuário diferentes em um único momento dentro dos sistemas operacionais Windows, incluindo Win32, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]e Windows Presentation Foundation (WPF), pode ser uma tarefa assustadora para testar vários aplicativos com controles que parecem semelhantes. Por exemplo, a tabela a seguir descreve os nomes de propriedade específicos da estrutura necessários para recuperar o nome (ou texto) associado a um controle de botão e mostra a propriedade equivalente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] única.  
  
|Tipo de controle de automação da interface do usuário|Estrutura de interface do usuário|Propriedade específica da estrutura|Propriedade de automação da interface do usuário|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Botão|Windows Presentation Foundation|Conteúdo|Nome da|  
|Botão|Win32|Legenda|Nome da|  
|Image|HTML|alt|Nome da|  
  
 Provedores de automação de interface do usuário são responsáveis por mapear as propriedades específicas da estrutura de seus controles para as propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] equivalentes.  
  
 Informações sobre como implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um provedor podem ser encontradas em [provedores de automação de interface do usuário para código gerenciado](ui-automation-providers-for-managed-code.md). Informações sobre como implementar padrões de controle estão disponíveis em [padrões de controle de automação de IU](ui-automation-control-patterns.md) e padrão de texto de automação de [interface do usuário](ui-automation-text-pattern.md).  
  
## <a name="ui-automation-in-a-client"></a>Automação da interface do usuário em um cliente  
 O objetivo de muitas ferramentas e cenários de teste automatizados é a manipulação consistente e reproduzível da interface do usuário. Isso pode envolver controles específicos de testes de unidade até a gravação e reprodução de scripts de teste que iteram por meio de uma série de ações genéricas em um grupo de controles.  
  
 Uma complicação que surge de aplicativos automatizados é a dificuldade de sincronizar um teste com um destino dinâmico. Por exemplo, um controle de caixa de listagem, como um contido no Gerenciador de tarefas do Windows, que exibe uma lista de aplicativos em execução no momento. Como os itens na caixa de listagem são dinamicamente atualizados fora do controle do aplicativo de teste, a tentativa de repetir a seleção de um item específico na caixa de listagem com qualquer consistência é impossível. Problemas semelhantes também podem surgir ao tentar repetir alterações de foco simples em um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que está fora do controle do aplicativo de teste.  
  
### <a name="programmatic-access"></a>Acesso Programático  
 O acesso programático fornece a capacidade de imitar, por meio de código, qualquer interação e experiência exposta por entrada tradicional de mouse e teclado. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] habilita o acesso programático por meio de cinco componentes:  
  
- A árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] facilita a navegação por meio da estrutura da [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. A árvore é criada a partir da coleção de hWnds. Para obter mais informações, consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md)  
  
- Os elementos de automação são componentes individuais no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Muitas vezes, eles podem ser mais granulares do que um hWnd. Para obter mais informações, consulte [visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md).  
  
- As propriedades de automação fornecem informações específicas sobre elementos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Para obter mais informações, consulte [visão geral das propriedades de automação da interface do usuário](ui-automation-properties-overview.md).  
  
- Padrões de controle definem um aspecto específico da funcionalidade de um controle; Eles podem consistir de informações de propriedade, método, evento e estrutura. Para obter mais informações, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
- Os eventos de automação fornecem notificações e informações de eventos. Para obter mais informações, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Propriedades de chave para automação de teste  
 A capacidade de identificar e subseqüentemente localizar qualquer controle dentro do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] fornece a base para que os aplicativos de teste automatizados operem nessa [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Há várias propriedades [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usadas por clientes e provedores que auxiliam nesse caso.  
  
#### <a name="automationid"></a>AutomationID  
 Identifica exclusivamente um elemento Automation de seus irmãos. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> não é localizado, ao contrário de uma propriedade como <xref:System.Windows.Automation.AutomationElement.NameProperty> que normalmente é localizada se um produto é enviado em vários idiomas. Consulte [usar a propriedade AutomationId](use-the-automationid-property.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> não garante uma identidade exclusiva em toda a árvore de automação. Por exemplo, um aplicativo pode conter um controle de menu com vários itens de menu de nível superior que, por sua vez, têm vários itens de menu filho. Esses itens de menu secundários podem ser identificados por um esquema genérico, como "Item1, item 2, Item3, etc.", permitindo identificadores duplicados para filhos em itens de menu de nível superior.  
  
#### <a name="controltype"></a>ControlType  
 Identifica o tipo de controle representado por um elemento de automação. Informações significativas podem ser inferidas do conhecimento do tipo de controle. Consulte [visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>Nome da  
 Essa é uma cadeia de caracteres de texto que identifica ou explica um controle. <xref:System.Windows.Automation.AutomationElement.NameProperty> deve ser usado com cautela, pois ele pode ser localizado. Consulte [visão geral das propriedades de automação da interface do usuário](ui-automation-properties-overview.md).  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementando a automação da interface do usuário em um aplicativo de teste  
  
|||  
|-|-|  
|Adicione as referências de automação da interface do usuário.|O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] DLL necessário para clientes de automação da interface do usuário estão listados aqui.<br /><br /> -UIAutomationClient. dll fornece acesso ao [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] APIs do lado do cliente.<br />-UIAutomationClientSideProvider. dll fornece a capacidade de automatizar controles do Win32. Consulte [suporte à automação da interface do usuário para controles padrão](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll fornece acesso aos tipos específicos definidos em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Adicione o namespace <xref:System.Windows.Automation>.|Esse namespace contém tudo que os clientes de automação da interface do usuário precisam para usar os recursos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], exceto a manipulação de texto.|  
|Adicione o namespace <xref:System.Windows.Automation.Text>.|Esse namespace contém tudo o que um cliente de automação da interface do usuário precisa para usar os recursos de manipulação de texto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Localizar controles de interesse|Scripts de teste automatizados localizam elementos de automação da interface do usuário que representam controles de interesse na árvore de automação.<br /><br /> Há várias maneiras de obter elementos de automação da interface do usuário com código.<br /><br /> -Consultar o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] usando uma instrução <xref:System.Windows.Automation.Condition>. Normalmente, esse é o local em que o <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> com neutralidade de idioma é usado. **Observação:**  Um <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> pode ser obtido usando uma ferramenta como inspecionar. exe que é capaz de discriminar as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de um controle. <br /><br /> -Use a classe <xref:System.Windows.Automation.TreeWalker> para atravessar toda a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ou um subconjunto dela.<br />-Controle o foco.<br />-Use o hWnd do controle.<br />-Use o local da tela, como o local do cursor do mouse.<br /><br /> Consulte [obtendo elementos de automação da interface do usuário](obtaining-ui-automation-elements.md)|  
|Obter padrões de controle|Padrões de controle expõem comportamentos comuns para controles funcionalmente semelhantes.<br /><br /> Depois de localizar os controles que exigem testes, os scripts de teste automatizados obtêm os padrões de controle de interesse desses elementos de automação da interface do usuário. Por exemplo, o padrão de controle de <xref:System.Windows.Automation.InvokePattern> para a funcionalidade típica de botão ou o padrão de controle de <xref:System.Windows.Automation.WindowPattern> para a funcionalidade de janela.<br /><br /> Consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).|  
|Automatizar a interface do usuário|Os scripts de teste automatizados agora podem controlar qualquer [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de interesse de uma estrutura de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] usando as informações e a funcionalidade expostas pelos padrões de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
  
## <a name="related-tools-and-technologies"></a>Ferramentas e tecnologias relacionadas  
 Há uma série de ferramentas e tecnologias relacionadas que dão suporte a testes automatizados com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
- O inspecionar. exe é um aplicativo de GUI (interface gráfica do usuário) que pode ser usado para coletar informações de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para desenvolvimento e depuração de provedor e cliente. O inspeciona. exe está incluído no SDK do Windows.  
  
- O MSAABridge expõe informações de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para Acessibilidade Ativa clientes. O objetivo principal da ponte de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para Acessibilidade Ativa é permitir que os clientes Acessibilidade Ativa existentes interajam com qualquer estrutura que tenha implementado [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
## <a name="security"></a>Segurança  
 Para obter informações de segurança, consulte [visão geral de segurança de automação da interface do usuário](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Veja também

- [UI Automation Fundamentals](index.md) (Fundamentos da Automação da Interface do Usuário)
