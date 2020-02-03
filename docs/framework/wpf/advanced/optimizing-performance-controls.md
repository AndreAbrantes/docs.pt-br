---
title: Otimizar o desempenho do controle
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: d02fde7076cd6a24fdfb171ed54161b20f3d465e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746733"
---
# <a name="optimizing-performance-controls"></a>Otimizando o desempenho: controles

O Windows Presentation Foundation (WPF) inclui muitos dos componentes comuns da interface do usuário que são usados na maioria dos aplicativos do Windows. Este tópico contém técnicas para melhorar o desempenho de sua interface do usuário.

## <a name="displaying-large-data-sets"></a>Exibindo grandes conjuntos de dados

Os controles do WPF, como o <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ComboBox>, são usados para exibir listas de itens em um aplicativo. Se a lista a ser exibida for grande, o desempenho do aplicativo poderá ser afetado. Isso ocorre porque o sistema de layout padrão cria um contêiner de layout para cada item associado ao controle de lista e computa a posição e tamanho do layout. Normalmente, você não precisa exibir todos os itens ao mesmo tempo. Em vez disso, você exibe um subconjunto e o usuário rola pela lista. Nesse caso, faz sentido usar a *virtualização* da interface do usuário, o que significa que a geração de contêiner do item e a computação do layout associado a um item são adiadas até que o item esteja visível.

A virtualização da interface do usuário é um aspecto importante dos controles de lista. A virtualização da interface do usuário não deve ser confundida com a virtualização de dados. A virtualização da interface do usuário armazena somente os itens visíveis na memória, mas em um cenário de associação de dados, armazena toda a estrutura de dados na memória. Em contraste, a virtualização de dados armazena somente os itens de dados visíveis na tela na memória.

Por padrão, a virtualização de interface do usuário está habilitada para os controles de <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ListBox> quando seus itens de lista estão associados aos dados. <xref:System.Windows.Controls.TreeView> virtualização pode ser habilitada definindo a propriedade <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> anexada como `true`. Se você quiser habilitar a virtualização de interface do usuário para controles personalizados que derivam de <xref:System.Windows.Controls.ItemsControl> ou controles de item existentes que usam a classe <xref:System.Windows.Controls.StackPanel>, como <xref:System.Windows.Controls.ComboBox>, você pode definir o <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> como <xref:System.Windows.Controls.VirtualizingStackPanel> e definir <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> como `true`. Infelizmente, você pode desabilitar a virtualização da interface do usuário para esses controles sem perceber. A seguir, temos uma lista de condições que desabilitam a virtualização da interface do usuário.

- Os contêineres de item são adicionados diretamente à <xref:System.Windows.Controls.ItemsControl>. Por exemplo, se um aplicativo adiciona explicitamente <xref:System.Windows.Controls.ListBoxItem> objetos a uma <xref:System.Windows.Controls.ListBox>, o <xref:System.Windows.Controls.ListBox> não virtualiza os objetos <xref:System.Windows.Controls.ListBoxItem>.

- Os contêineres de item no <xref:System.Windows.Controls.ItemsControl> são de tipos diferentes. Por exemplo, um <xref:System.Windows.Controls.Menu> que usa objetos <xref:System.Windows.Controls.Separator> não pode implementar a reciclagem de itens porque a <xref:System.Windows.Controls.Menu> contém objetos do tipo <xref:System.Windows.Controls.Separator> e <xref:System.Windows.Controls.MenuItem>.

- Definindo <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> como `false`.

- Definindo <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> como `false`.

Uma consideração importante quando você virtualiza contêineres de itens é se você tem informações de estado adicionais associadas a um contêiner de item que pertence ao item. Nesse caso, você precisa salvar o estado adicional. Por exemplo, você pode ter um item contido em um controle de <xref:System.Windows.Controls.Expander> e o estado de <xref:System.Windows.Controls.Expander.IsExpanded%2A> está associado ao contêiner do item, e não ao próprio item. Quando o contêiner é reutilizado para um novo item, o valor atual de <xref:System.Windows.Controls.Expander.IsExpanded%2A> é usado para o novo item. Além disso, o item antigo perde o valor de <xref:System.Windows.Controls.Expander.IsExpanded%2A> correto.

Atualmente, nenhum controle do WPF dá suporte interno para a virtualização de dados.

## <a name="container-recycling"></a>Reciclagem de contêineres

Uma otimização para a virtualização de interface do usuário adicionada no .NET Framework 3,5 SP1 para controles que herdam de <xref:System.Windows.Controls.ItemsControl> é a *reciclagem de contêiner,* que também pode melhorar o desempenho da rolagem. Quando um <xref:System.Windows.Controls.ItemsControl> que usa a virtualização de interface do usuário é populado, ele cria um contêiner de item para cada item que rola para a exibição e destrói o contêiner de item para cada item que rola para fora da exibição. A *reciclagem de contêiner* permite que o controle reutilize os contêineres de item existentes para itens de dados diferentes, de modo que os contêineres de item não sejam criados constantemente e destruídos quando o usuário rola a <xref:System.Windows.Controls.ItemsControl>. Você pode optar por habilitar a reciclagem de itens definindo a propriedade <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> anexada como <xref:System.Windows.Controls.VirtualizationMode.Recycling>.

Qualquer <xref:System.Windows.Controls.ItemsControl> que ofereça suporte à virtualização pode usar a reciclagem de contêiner. Para obter um exemplo de como habilitar a reciclagem de contêiner em um <xref:System.Windows.Controls.ListBox>, consulte [melhorar o desempenho de rolagem de uma caixa de listagem](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Suporte à virtualização bidirecional

o <xref:System.Windows.Controls.VirtualizingStackPanel> oferece suporte interno para a virtualização de interface do usuário em uma direção, tanto horizontal quanto verticalmente. Se você quiser usar a virtualização bidirecional para seus controles, deverá implementar um painel personalizado que estenda a classe <xref:System.Windows.Controls.VirtualizingStackPanel>. A classe <xref:System.Windows.Controls.VirtualizingStackPanel> expõe métodos virtuais, como <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>e <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Esses métodos virtuais permitem detectar uma alteração na parte visível de uma lista e tratá-la de acordo.

## <a name="optimizing-templates"></a>Otimizando modelos

A árvore visual contém todos os elementos visuais de um aplicativo. Além dos objetos criados diretamente, ela também contém objetos decorrentes da expansão do modelo. Por exemplo, ao criar um <xref:System.Windows.Controls.Button>, você também obtém <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> e <xref:System.Windows.Controls.ContentPresenter> objetos na árvore visual. Se ainda não tiver otimizado seus modelos de controle, você poderá estar criando muitos objetos extra desnecessários na árvore visual. Para obter mais informações sobre a árvore visual, consulte [Visão geral de renderização de gráficos do WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Rolagem adiada

Por padrão, quando o usuário arrasta o controle de posição em uma barra de rolagem, a exibição de conteúdo é atualizada continuamente. Se a rolagem estiver lenta em seu controle, considere usar a rolagem adiada. Com a rolagem adiada, o conteúdo é atualizado somente quando o usuário libera o controle de posição.

Para implementar a rolagem adiada, defina a propriedade <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> como `true`. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> é uma propriedade anexada e pode ser definida em <xref:System.Windows.Controls.ScrollViewer> e qualquer controle que tenha um <xref:System.Windows.Controls.ScrollViewer> em seu modelo de controle.

## <a name="controls-that-implement-performance-features"></a>Controles que implementam recursos de desempenho

A tabela a seguir lista os controles comuns para exibir dados e seu suporte a recursos de desempenho. Consulte as seções anteriores para obter informações sobre como habilitar esses recursos.

|Controle|Virtualização|Reciclagem de contêineres|Rolagem adiada|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|
|<xref:System.Windows.Controls.ContextMenu>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|
|<xref:System.Windows.Controls.DocumentViewer>|Não disponível|Não disponível|Pode ser habilitado|
|<xref:System.Windows.Controls.ListBox>|Padrão|Pode ser habilitado|Pode ser habilitado|
|<xref:System.Windows.Controls.ListView>|Padrão|Pode ser habilitado|Pode ser habilitado|
|<xref:System.Windows.Controls.TreeView>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|
|<xref:System.Windows.Controls.ToolBar>|Não disponível|Não disponível|Pode ser habilitado|

> [!NOTE]
> Para obter um exemplo de como habilitar a virtualização e a reciclagem de contêineres em um <xref:System.Windows.Controls.TreeView>, consulte [melhorar o desempenho de um TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Consulte também

- [Layout](layout.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Controles](../controls/index.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
