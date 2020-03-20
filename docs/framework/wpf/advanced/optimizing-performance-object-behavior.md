---
title: 'Otimizando desempenho: comportamento do objeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187069"
---
# <a name="optimizing-performance-object-behavior"></a>Otimizando desempenho: comportamento do objeto
O entendimento do comportamento intrínseco de objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajudará você a fazer o balanceamento correto entre desempenho e funcionalidade.  

<a name="Not_Removing_Event_Handlers"></a>
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Não remover manipuladores de eventos em objetos poderá manter os objetos ativos  
 O delegado que um objeto passa para seu evento é, efetivamente, uma referência a esse objeto. Portanto, os manipuladores de eventos podem manter objetos ativos por mais tempo que o esperado. Ao realizar a limpeza de um objeto que tenha sido registrado para escutar um evento de objeto, é essencial remover esse delegado antes de liberar o objeto. Manter objetos desnecessários ativos aumenta o uso de memória do aplicativo. Isso é especialmente verdadeiro quando o objeto é a raiz de uma árvore lógica ou de uma árvore visual.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apresenta um padrão fraco de ouvinte de eventos para eventos que podem ser úteis em situações em que as relações de tempo de vida do objeto, entre a origem e o ouvinte, são difíceis de controlar. Alguns eventos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes usam esse padrão. Se estiver implementando objetos com eventos personalizados, esse padrão poderá ser útil para você. Para obter detalhes, consulte [Padrões de evento fracos](weak-event-patterns.md).  
  
 Há várias ferramentas, como o Criador de Perfil CLR e o Visualizador de Conjunto de Trabalho, que podem fornecer informações sobre o uso de memória de um processo especificado. O Criador de Perfil CLR inclui várias exibições muito úteis do perfil de alocação, incluindo um histograma de tipos alocados, grafos de alocação e de chamadas, uma linha do tempo mostrando coletas de lixo de várias gerações e o estado resultante do heap gerenciado após essas coletas, além de uma árvore de chamadas mostrando as cargas de assembly e alocações por método. Para obter mais informações, consulte [Desempenho](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>
## <a name="dependency-properties-and-objects"></a>Propriedades de dependência e objetos  
 Em geral, acessar uma propriedade <xref:System.Windows.DependencyObject> de dependência de a não é mais lento do que acessar uma propriedade CLR. Embora haja uma pequena sobrecarga de desempenho para definir um valor de propriedade, obter um valor é tão rápido quanto obter o valor de uma propriedade CLR. O fato de as propriedades de dependência darem suporte a recursos robustos, como vinculação de dados, animação, herança e estilos é a compensação pela pequena sobrecarga de desempenho. Para obter mais informações, consulte [Visão geral sobre propriedades de dependência](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Otimizações de DependencyProperty  
 Você deve definir as propriedades de dependência em seu aplicativo com muito cuidado. Se <xref:System.Windows.DependencyProperty> o seu afeto só renderizar opções de metadados de tipo, em vez de outras opções de metadados, como, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>você deve marcá-lo como tal, substituindo seus metadados. Para obter mais informações sobre como substituir ou obter metadados de propriedades, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).  
  
 Talvez seja mais eficiente fazer com que um manipulador de alterações de propriedade invalide as passagens de medida, organização e renderização manualmente se nem todas as alterações de propriedade afetarem, na verdade, a medida, a organização e a renderização. Por exemplo, você pode decidir renderizar novamente uma tela de fundo apenas quando um valor for maior que um limite definido. Nesse caso, seu manipulador de alteração de propriedade só invalidaria a renderização quando o valor excedesse o limite definido.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Há consequências em tornar uma DependencyProperty herdável  
 Por padrão, as propriedades de dependência registradas são não herdáveis. No entanto, você pode explicitamente tornar qualquer propriedade herdável. Embora esse seja um recurso útil, converter uma propriedade para se tornar herdável afeta o desempenho, aumentando o período de tempo para a invalidação da propriedade.  
  
### <a name="use-registerclasshandler-carefully"></a>Usar o RegisterClassHandler com cuidado  
 Embora <xref:System.Windows.EventManager.RegisterClassHandler%2A> a chamada permita que você salve seu estado de instância, é importante estar ciente de que o manipulador é chamado em todas as instâncias, o que pode causar problemas de desempenho. Use <xref:System.Windows.EventManager.RegisterClassHandler%2A> somente quando seu aplicativo exigir que você salve seu estado de instância.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Definir o valor padrão para uma DependencyProperty durante o registro  
 Ao criar <xref:System.Windows.DependencyProperty> um que exija um valor padrão, defina o valor <xref:System.Windows.DependencyProperty.Register%2A> usando os <xref:System.Windows.DependencyProperty>metadados padrão passados como parâmetro para o método do . Use esta técnica em vez de configurar o valor da propriedade em um construtor ou em cada instância de um elemento.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Definir o valor de PropertyMetadata usando o registro  
 Ao criar <xref:System.Windows.DependencyProperty>um , você tem <xref:System.Windows.PropertyMetadata> a <xref:System.Windows.DependencyProperty.Register%2A> opção <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> de definir o uso ou os métodos. Embora seu objeto possa ter um <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>construtor estático para chamar, esta não é a solução ideal e afetará o desempenho. Para obter o <xref:System.Windows.PropertyMetadata> melhor desempenho, <xref:System.Windows.DependencyProperty.Register%2A>defina o durante a chamada para .  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Objetos congeláveis  
 A <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois estados: descongelado e congelado. Congelar objetos sempre que possível melhora o desempenho do seu aplicativo e reduz seu conjunto de trabalho. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
 Cada <xref:System.Windows.Freezable> um <xref:System.Windows.Freezable.Changed> tem um evento que é levantado sempre que muda. No entanto, as notificações de alteração são dispendiosas em termos de desempenho do aplicativo.  
  
 Considere o seguinte exemplo <xref:System.Windows.Shapes.Rectangle> no <xref:System.Windows.Media.Brush> qual cada um usa o mesmo objeto:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão, fornece um <xref:System.Windows.Media.SolidColorBrush> manipulador de <xref:System.Windows.Freezable.Changed> eventos para o <xref:System.Windows.Shapes.Rectangle> evento do <xref:System.Windows.Shapes.Shape.Fill%2A> objeto, a fim de invalidar a propriedade do objeto. Neste caso, cada <xref:System.Windows.Media.SolidColorBrush> vez que <xref:System.Windows.Freezable.Changed> o evento tem que disparar é <xref:System.Windows.Shapes.Rectangle>necessário invocar a função de retorno de chamada para cada um — o acúmulo dessas invocações da função de retorno de chamada impõe uma penalidade de desempenho significativa. Além disso, adicionar e remover manipuladores neste ponto exigiria muito do desempenho, já que o aplicativo teria que percorrer toda a lista para fazer isso. Se o seu cenário <xref:System.Windows.Media.SolidColorBrush>de aplicação nunca mudar, <xref:System.Windows.Freezable.Changed> você estará pagando o custo de manter os manipuladores de eventos desnecessariamente.  
  
 Congelar um <xref:System.Windows.Freezable> pode melhorar seu desempenho, porque ele não precisa mais gastar recursos na manutenção de notificações de alterações. A tabela abaixo mostra o <xref:System.Windows.Media.SolidColorBrush> tamanho <xref:System.Windows.Freezable.IsFrozen%2A> de um `true`simples quando sua propriedade é definida para , em comparação com quando não é. Isso pressupõe a aplicação <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Rectangle> um pincel na propriedade de dez objetos.  
  
|**Estado**|**Tamanho**|  
|---------------|--------------|  
|Congelado<xref:System.Windows.Media.SolidColorBrush>|212 bytes|  
|Não congelado<xref:System.Windows.Media.SolidColorBrush>|972 bytes|  
  
 O exemplo de código a seguir demonstra esse conceito:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Manipuladores alterados em Congeláveis descongelados podem manter objetos ativos  
 O delegado de que <xref:System.Windows.Freezable> um objeto <xref:System.Windows.Freezable.Changed> passa para o evento de um objeto é efetivamente uma referência a esse objeto. Portanto, <xref:System.Windows.Freezable.Changed> os manipuladores de eventos podem manter os objetos vivos por mais tempo do que o esperado. Ao realizar a limpeza de um objeto que <xref:System.Windows.Freezable> se registrou <xref:System.Windows.Freezable.Changed> para ouvir o evento de um objeto, é essencial remover esse delegado antes de liberar o objeto.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também liga <xref:System.Windows.Freezable.Changed> eventos internamente. Por exemplo, todas as <xref:System.Windows.Freezable> propriedades de dependência <xref:System.Windows.Freezable.Changed> que tomam como valor ouvirão os eventos automaticamente. A <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade, que <xref:System.Windows.Media.Brush>leva um , ilustra esse conceito.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na atribuição `myBrush` `myRectangle.Fill`de , um delegado <xref:System.Windows.Shapes.Rectangle> apontando de volta <xref:System.Windows.Media.SolidColorBrush> para <xref:System.Windows.Freezable.Changed> o objeto será adicionado ao evento do objeto. Isso significa que o código a seguir, na verdade, não torna o `myRect` qualificado para a coleta de lixo:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Neste caso, `myBrush` ainda `myRectangle` está vivo e vai chamá-lo de volta quando ele dispara seu <xref:System.Windows.Freezable.Changed> evento. Observe que `myBrush` atribuir <xref:System.Windows.Shapes.Shape.Fill%2A> à propriedade <xref:System.Windows.Shapes.Rectangle> de um novo simplesmente `myBrush`adicionará outro manipulador de eventos a .  
  
 A maneira recomendada de limpar esses tipos de <xref:System.Windows.Media.Brush> objetos é remover o da propriedade, que <xref:System.Windows.Shapes.Shape.Fill%2A> por sua vez removerá o manipulador de <xref:System.Windows.Freezable.Changed> eventos.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>Virtualização da interface do usuário  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também fornece uma <xref:System.Windows.Controls.StackPanel> variação do elemento que automaticamente "virtualiza" o conteúdo infantil vinculado a dados. Nesse contexto, a palavra virtualizar refere-se a uma técnica pela qual um subconjunto dos objetos são gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. É intensivo, tanto em termos de memória quanto de processador, gerar um grande número de elementos de interface do usuário quando apenas alguns podem estar na tela em um determinado momento. <xref:System.Windows.Controls.VirtualizingStackPanel>(através da funcionalidade <xref:System.Windows.Controls.VirtualizingPanel>fornecida por ) calcula itens <xref:System.Windows.Controls.ItemContainerGenerator> visíveis <xref:System.Windows.Controls.ItemsControl> e <xref:System.Windows.Controls.ListBox> trabalha <xref:System.Windows.Controls.ListView>com o de um (como ou ) para criar apenas elementos para itens visíveis.  
  
 Como uma otimização de desempenho, os objetos visuais para esses itens serão gerados ou mantidos ativos somente se estiverem visíveis na tela. Quando não estão mais na área visível do controle, os objetos visuais podem ser removidos. Isso não deve ser confundido com virtualização de dados, em que os objetos de dados não estão todos presentes na coleção local mas, em vez disso, são transmitidos conforme necessário.  
  
 A tabela abaixo mostra o tempo decorrido adicionando e renderizando 5000 <xref:System.Windows.Controls.TextBlock> elementos a a <xref:System.Windows.Controls.StackPanel> e a <xref:System.Windows.Controls.VirtualizingStackPanel>. Neste cenário, as medidas representam o tempo entre anexar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> uma <xref:System.Windows.Controls.ItemsControl> seqüência de texto à propriedade de um objeto ao momento em que os elementos do painel exibem a seqüência de texto.  
  
|**Painel de host**|**Tempo de renderização (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Confira também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando o desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitar o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Recursos de aplicação](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
