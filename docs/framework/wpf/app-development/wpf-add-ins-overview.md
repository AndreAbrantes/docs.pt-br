---
title: Visão geral dos suplementos
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 93904e308932ea41c736ca849ce0efb200502a7e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738946"
---
# <a name="wpf-add-ins-overview"></a>Visão geral dos suplementos do WPF

<a name="Introduction"></a>O .NET Framework inclui um modelo de suplemento que os desenvolvedores podem usar para criar aplicativos que dão suporte à extensibilidade de suplementos. Esse modelo permite a criação de suplementos que integram e estendem a funcionalidade do aplicativo. Em alguns cenários, os aplicativos também precisam Exibir interfaces do usuário que são fornecidas por suplementos. Este tópico mostra como o WPF aumenta o modelo de suplemento .NET Framework para habilitar esses cenários, a arquitetura por trás dele, seus benefícios e suas limitações.

<a name="Requirements"></a>

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

É necessário ter familiaridade com o modelo de suplemento de .NET Framework. Para obter mais informações, consulte [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>Visão geral dos suplementos

Para evitar as complexidades da recompilação do aplicativo e de sua reimplantação para incorporação de uma nova funcionalidade, os aplicativos implementam mecanismos de extensibilidade que permitem aos desenvolvedores (fornecedores principais e terceiros) criar outros aplicativos que se integrem a eles. A maneira mais comum para dar suporte a esse tipo de extensibilidade é através do uso de suplementos (também conhecidos como "complementos" e "plug-ins"). Exemplos de aplicativos reais que expõem extensibilidade com suplementos incluem:

- Complementos do Internet Explorer.

- Plug-ins do Windows Media Player.

- Suplementos do Visual Studio.

Por exemplo, o modelo de suplemento do Windows Media Player permite que desenvolvedores de terceiros implementem "plug-ins" que estendam o Windows Media Player de várias maneiras, incluindo a criação de decodificadores e codificadores para formatos de mídia que não têm suporte nativo pelo Windows Media Player (por exemplo, DVD, MP3), efeitos de áudio e capas. Cada modelo de suplemento é desenvolvido para expor a funcionalidade que é exclusiva de um aplicativo, embora haja várias entidades e comportamentos que são comuns a todos os modelos de suplemento.

As três principais entidades das soluções típicas de extensibilidade de suplementos são *contratos*, *suplementos* e *aplicativos host*. Contratos definem como os suplementos se integram a aplicativos host de duas maneiras:

- Suplementos se integram à funcionalidade que é implementada por aplicativos host.

- Aplicativos host expõem a funcionalidade que os suplementos se integrem a ela.

Para que suplementos possam ser usados, é necessário que eles sejam localizados e carregados em tempo de execução pelos aplicativos host. Consequentemente, os aplicativos que dão suporte a suplementos têm as seguintes responsabilidades adicionais:

- **Descoberta**: encontrar suplementos que aderem a contratos com suporte por aplicativos host.

- **Ativação**: carregar, executar e estabelecer comunicação com suplementos.

- **Isolamento**: usar domínios do aplicativo ou processos para estabelecer limites de isolamento que protegem aplicativos de possíveis problemas de execução e segurança com suplementos.

- **Comunicação**: permitir, por meio da chamada de métodos e transmissão de dados, que suplementos e aplicativos host se comuniquem uns com os outros através de limites de isolamento.

- **Gerenciamento de tempo de vida**: Carregando e descarregando domínios do aplicativo e processos de uma maneira limpa e previsível (consulte [Domínios do aplicativo](../../app-domains/application-domains.md)).

- **Controle de versão**: garantir que os aplicativos host e suplementos possam se comunicar quando novas versões de qualquer um deles forem criadas.

Por fim, desenvolver um modelo de suplemento robusto é uma tarefa não trivial. Por esse motivo, o .NET Framework fornece uma infraestrutura para a criação de modelos de suplementos.

> [!NOTE]
> Para obter informações mais detalhadas sobre suplementos, consulte [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>Visão geral de modelo de suplemento do .NET Framework

O modelo de suplemento .NET Framework, encontrado no namespace <xref:System.AddIn>, contém um conjunto de tipos que são projetados para simplificar o desenvolvimento da extensibilidade do suplemento. A unidade fundamental do modelo de suplemento de .NET Framework é o *contrato*, que define como um aplicativo host e um suplemento se comunicam entre si. Um contrato é exposto a um aplicativo host utilizando uma *exibição* do contrato específica do aplicativo host. Da mesma forma, uma *exibição* do contrato específica do suplemento é exposta ao suplemento. Um *adaptador* é usado para permitir que um aplicativo host e um suplemento se comuniquem entre suas respectivas exibições do contrato. Contratos, exibições e adaptadores são referidos como segmentos, enquanto um conjunto de segmentos relacionados constitui um *pipeline*. Pipelines são a base sobre a qual o modelo de suplemento .NET Framework dá suporte à descoberta, ativação, isolamento de segurança, isolamento de execução (usando processos e domínios de aplicativo), comunicação, gerenciamento de tempo de vida e controle de versão.

A soma desse suporte permite aos desenvolvedores compilar suplementos que se integram com a funcionalidade de um aplicativo host. No entanto, alguns cenários exigem que aplicativos host exibam interfaces do usuário fornecidas por suplementos. Como cada tecnologia de apresentação no .NET Framework tem seu próprio modelo para implementar interfaces de usuário, o modelo de suplemento de .NET Framework não oferece suporte a nenhuma tecnologia de apresentação específica. Em vez disso, o WPF estende o modelo de suplemento .NET Framework com suporte de interface do usuário para suplementos.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>Suplementos do WPF

O WPF, em conjunto com o modelo de suplemento .NET Framework, permite que você resolva uma ampla variedade de cenários que exigem que aplicativos host exibam interfaces do usuário de suplementos. Em particular, esses cenários são tratados pelo WPF com os dois modelos de programação a seguir:

1. **O suplemento retorna uma interface do usuário**. Um suplemento retorna uma interface do usuário para o aplicativo host por meio de uma chamada de método, conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:

    - A aparência de uma interface do usuário retornada por um suplemento depende de dados ou das condições que existem somente em tempo de execução, como relatórios gerados dinamicamente.

    - A interface do usuário para serviços fornecidos por um suplemento difere da interface do usuário dos aplicativos host que podem usar o suplemento.

    - O suplemento executa principalmente um serviço para o aplicativo host e relata o status para o aplicativo host com uma interface do usuário.

2. **O suplemento é uma interface do usuário**. Um suplemento é uma interface do usuário, conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:

    - Um suplemento não fornece nenhum serviço além de ser exibido, por exemplo, um anúncio.

    - A interface do usuário para serviços fornecidos por um suplemento é comum a todos os aplicativos host que podem usar esse suplemento, como uma calculadora ou um seletor de cores.

Esses cenários exigem que os objetos da interface do usuário possam ser passados entre o aplicativo host e os domínios do aplicativo de suplemento. Como o modelo de suplemento .NET Framework conta com a comunicação remota para se comunicar entre domínios de aplicativo, os objetos passados entre eles devem ser remotos.

Um objeto remoto é uma instância de uma classe que satisfaz uma ou mais das condições a seguir:

- Deriva da classe <xref:System.MarshalByRefObject>.

- Implementa a interface <xref:System.Runtime.Serialization.ISerializable>.

- Tem o atributo <xref:System.SerializableAttribute> aplicado.

> [!NOTE]
> Para obter mais informações sobre a criação de objetos de .NET Framework remotas, consulte [tornando objetos remotos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).

Os tipos de interface do usuário do WPF não são remotos. Para resolver o problema, o WPF estende o modelo de suplemento .NET Framework para habilitar a interface do usuário do WPF criada por suplementos a serem exibidos de aplicativos host. Esse suporte é fornecido pelo WPF por dois tipos: a interface <xref:System.AddIn.Contract.INativeHandleContract> e dois métodos estáticos implementados pela classe <xref:System.AddIn.Pipeline.FrameworkElementAdapters>: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Em um nível elevado, esses tipos e métodos são usados da seguinte maneira:

1. O WPF requer que as interfaces de usuário fornecidas por suplementos sejam classes que derivam direta ou indiretamente de <xref:System.Windows.FrameworkElement>, como formas, controles, controles de usuário, painéis de layout e páginas.

2. Sempre que o contrato declarar que uma interface do usuário será passada entre o suplemento e o aplicativo host, ele deve ser declarado como um <xref:System.AddIn.Contract.INativeHandleContract> (não um <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> é uma representação remota da interface do usuário do suplemento que pode ser passada entre limites de isolamento.

3. Antes de ser passado do domínio do aplicativo do suplemento, um <xref:System.Windows.FrameworkElement> é empacotado como um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

4. Depois de ser passado para o domínio de aplicativo do aplicativo host, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser reempacotado como um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.

Como <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> são usados depende do cenário específico. As seções a seguir fornecem detalhes para cada modelo de programação.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>O suplemento retorna uma interface do usuário

Para que um suplemento retorne uma interface do usuário para um aplicativo host, são necessários os seguintes:

1. O aplicativo host, o suplemento e o pipeline devem ser criados, conforme descrito pelos [suplementos .NET Framework e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentação de extensibilidade.

2. O contrato deve implementar <xref:System.AddIn.Contract.IContract> e, para retornar uma interface do usuário, o contrato deve declarar um método com um valor de retorno do tipo <xref:System.AddIn.Contract.INativeHandleContract>.

3. A interface do usuário que é transmitida entre o suplemento e o aplicativo host deve ser direta ou indiretamente derivada de <xref:System.Windows.FrameworkElement>.

4. A interface do usuário retornada pelo suplemento deve ser convertida de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.

5. A interface do usuário retornada deve ser convertida de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento.

6. O aplicativo host exibe o <xref:System.Windows.FrameworkElement>retornado.

Para obter um exemplo que demonstra como implementar um suplemento que retorna uma interface do usuário, consulte [criar um suplemento que retorna uma interface do usuário](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>O suplemento é uma interface do usuário

Quando um suplemento é uma interface do usuário, são necessários os seguintes:

1. O aplicativo host, o suplemento e o pipeline devem ser criados, conforme descrito pelos [suplementos .NET Framework e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentação de extensibilidade.

2. A interface do contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>.

3. O suplemento que é passado para o aplicativo host deve ser derivado direta ou indiretamente de <xref:System.Windows.FrameworkElement>.

4. O suplemento deve ser convertido de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.

5. O suplemento deve ser convertido de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento.

6. O aplicativo host exibe o <xref:System.Windows.FrameworkElement>retornado.

Para obter um exemplo que demonstra como implementar um suplemento que é uma interface do usuário, consulte [criar um suplemento que é uma interface do usuário](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Retornando múltiplas interfaces do usuário de um suplemento

Os suplementos geralmente fornecem várias interfaces de usuário para que os aplicativos host sejam exibidos. Por exemplo, considere um suplemento que é uma interface do usuário que também fornece informações de status para o aplicativo host, também como uma interface do usuário. Um suplemento como esse pode ser implementado pelo uso de uma combinação de técnicas de ambos os modelos [O suplemento retorna uma interface do usuário](#ReturnUIFromAddInContract) e [O suplemento é uma interface do usuário](#AddInIsAUI).

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Suplementos e aplicativos de navegação XAML

Nos exemplos até agora, o aplicativo host tem sido um aplicativo autônomo instalado. Mas os aplicativos de navegador XAML (XBAPs) também podem hospedar suplementos, embora com os seguintes requisitos adicionais de compilação e implementação:

- O manifesto do aplicativo XBAP deve ser configurado especialmente para baixar o pipeline (pastas e assemblies) e o assembly do suplemento para o cache de aplicativo do ClickOnce no computador cliente, na mesma pasta que o XBAP.

- O código XBAP para descobrir e carregar os suplementos deve usar o cache de aplicativo ClickOnce para o XBAP como o pipeline e o local do suplemento.

- O XBAP deve carregar o suplemento em um contexto de segurança especial se o suplemento referenciar arquivos soltos que estão localizados no site de origem; Quando hospedado por XBAPs, os suplementos só podem fazer referência a arquivos soltos que estão localizados no site de origem do aplicativo host.

Essas tarefas são descritas detalhadamente nas subseções a seguir.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configurar o pipeline e o suplemento para a implantação do ClickOnce

XBAPs são baixados e executados em uma pasta segura no cache de implantação do ClickOnce. Para que um XBAP hospede um suplemento, o pipeline e o assembly do suplemento também devem ser baixados para a pasta segura. Para fazer isso, você precisa configurar o manifesto do aplicativo para incluir ambos o assembly do suplemento e do pipeline para baixar. Isso é feito com mais facilidade no Visual Studio, embora o pipeline e o assembly do suplemento precisem estar na pasta raiz do projeto XBAP do host para que o Visual Studio detecte os assemblies de pipeline.

Consequentemente, a primeira etapa é criar o pipeline e o assembly do suplemento para a raiz do projeto XBAP definindo a saída de Build de cada assembly de pipeline e projetos de assembly de suplementos. A tabela a seguir mostra os caminhos de saída de compilação para projetos de assembly de pipeline e projeto de assembly de suplemento que estão na mesma solução e pasta raiz que o projeto XBAP de host.

Tabela 1: caminhos de saída de build para os assemblies do pipeline hospedados por um XBAP

|Projeto de assembly do pipeline|Caminho de saída de build|
|-------------------------------|-----------------------|
|Contrato|`..\HostXBAP\Contracts\`|
|Exibição do suplemento|`..\HostXBAP\AddInViews\`|
|Adaptador no lado do suplemento|`..\HostXBAP\AddInSideAdapters\`|
|Adaptador no lado do host|`..\HostXBAP\HostSideAdapters\`|
|Suplemento|`..\HostXBAP\AddIns\WPFAddIn1`|

A próxima etapa é especificar os assemblies de pipeline e o assembly de suplemento como os arquivos de conteúdo XBAPs no Visual Studio fazendo o seguinte:

1. Incluindo o assembly do pipeline e do suplemento no projeto clicando com o botão direito do mouse em cada pasta de pipeline no Gerenciador de Soluções e escolhendo **Incluir no Projeto**.

2. Definindo a **Ação de Build** de cada assembly do pipeline e assembly do suplemento para **Conteúdo** da janela **Propriedades**.

A etapa final é configurar o manifesto do aplicativo para incluir os arquivos do assembly do pipeline e o arquivo do assembly do suplemento para download. Os arquivos devem estar localizados em pastas na raiz da pasta no cache do ClickOnce que o aplicativo XBAP ocupa. A configuração pode ser obtida no Visual Studio fazendo o seguinte:

1. Clique com o botão direito do mouse no projeto XBAP, clique em **Propriedades**, clique em **publicar**e, em seguida, clique no botão **arquivos de aplicativo** .

2. Na caixa de diálogo **Arquivos de Aplicativo**, defina o **Status da Publicação** de cada DLL de suplemento e de pipeline a **Incluir (Auto)** e defina o **Grupo de Download** para cada DLL de pipeline e de suplemento para **(Obrigatório)** .

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Usando o pipeline e o suplemento da base de aplicativo

Quando o pipeline e o suplemento são configurados para implantação do ClickOnce, eles são baixados para a mesma pasta de cache do ClickOnce que o XBAP. Para usar o pipeline e o suplemento do XBAP, o código XBAP deve obtê-los na base do aplicativo. Os vários tipos e membros do modelo de suplemento .NET Framework para usar pipelines e suplementos fornecem suporte especial para esse cenário. Em primeiro lugar, o caminho é identificado pelo valor de enumeração <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>. Você pode usar esse valor com sobrecargas de membros de suplemento pertinentes para usar pipelines que incluem o seguinte:

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Acessar o site de origem do host

Para garantir que um suplemento possa referenciar arquivos do site de origem, o suplemento deve ser carregado com isolamento de segurança que é equivalente ao do aplicativo host. Esse nível de segurança é identificado pelo valor de enumeração <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> e passado para o método <xref:System.AddIn.Hosting.AddInToken.Activate%2A> quando um suplemento é ativado.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>Arquitetura de suplemento do WPF

No nível mais alto, como vimos, o WPF permite que .NET Framework suplementos implementem interfaces do usuário (que derivam direta ou indiretamente do <xref:System.Windows.FrameworkElement>) usando <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. O resultado é que o aplicativo host é retornado um <xref:System.Windows.FrameworkElement> que é exibido na interface do usuário no aplicativo host.

Para cenários simples de suplementos de interface do usuário, isso é tão detalhado quanto um desenvolvedor precisa. Para cenários mais complexos, especialmente aqueles que tentam utilizar serviços adicionais do WPF, como layout, recursos e vinculação de dados, um conhecimento mais detalhado de como o WPF estende o modelo de suplemento .NET Framework com suporte à interface do usuário é necessário para entender seus benefícios e limitações.

Fundamentalmente, o WPF não passa uma interface do usuário de um suplemento para um aplicativo host; em vez disso, o WPF passa o identificador de janela do Win32 para a interface do usuário usando a interoperabilidade do WPF. Assim, quando uma interface do usuário de um suplemento é passada para um aplicativo host, ocorre o seguinte:

- No lado do suplemento, o WPF adquire um identificador de janela para a interface do usuário que será exibida pelo aplicativo host. O identificador de janela é encapsulado por uma classe interna do WPF que deriva de <xref:System.Windows.Interop.HwndSource> e implementa <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e é empacotada do domínio do aplicativo do suplemento para o domínio do aplicativo do aplicativo host.

- No lado do aplicativo host, o WPF reempacota o <xref:System.Windows.Interop.HwndSource> como uma classe interna do WPF que deriva de <xref:System.Windows.Interop.HwndHost> e consome <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> ao aplicativo host.

<xref:System.Windows.Interop.HwndHost> existe para exibir as interfaces do usuário, identificadas por identificadores de janela, de interfaces de usuário do WPF. Para obter mais informações, consulte [Interoperação Win32 e WPF](../advanced/wpf-and-win32-interoperation.md).

Em resumo, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existem para permitir que o identificador de janela para uma interface do usuário do WPF seja passado de um suplemento para um aplicativo host, onde ele é encapsulado por um <xref:System.Windows.Interop.HwndHost> e exibido a interface do usuário do aplicativo host.

> [!NOTE]
> Como o aplicativo host obtém uma <xref:System.Windows.Interop.HwndHost>, o aplicativo host não pode converter o objeto retornado pelo <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> para o tipo que ele é implementado como pelo suplemento (por exemplo, um <xref:System.Windows.Controls.UserControl>).

Por sua natureza, <xref:System.Windows.Interop.HwndHost> tem determinadas limitações que afetam como os aplicativos host podem usá-las. No entanto, o WPF estende <xref:System.Windows.Interop.HwndHost> com vários recursos para cenários de suplemento. Essas limitações e benefícios são descritos abaixo.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>Benefícios de suplementos do WPF

Como as interfaces de usuário do suplemento WPF são exibidas de aplicativos host usando uma classe interna que deriva de <xref:System.Windows.Interop.HwndHost>, essas interfaces de usuário são restritas pelos recursos do <xref:System.Windows.Interop.HwndHost> em relação aos serviços de interface do usuário do WPF, como layout, renderização, vinculação de dados, estilos, modelos e recursos. No entanto, o WPF aumenta sua subclasse <xref:System.Windows.Interop.HwndHost> interna com recursos adicionais que incluem o seguinte:

- Tabulação entre a interface do usuário de um aplicativo host e a interface do usuário de um suplemento. Observe que o modelo de programação "suplemento é uma interface do usuário" requer que o adaptador do suplemento substitua <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> para habilitar a tabulação, se o suplemento é totalmente confiável ou parcialmente confiável.

- Respeitar os requisitos de acessibilidade para interfaces do usuário do suplemento que são exibidas de interfaces de usuário do aplicativo host.

- Permitir que aplicativos WPF sejam executados com segurança em vários cenários de domínio de aplicativo.

- Impedir o acesso ilegal aos identificadores da janela da interface do usuário do suplemento quando os suplementos são executados com isolamento de segurança (ou seja, uma área restrita de segurança de confiança parcial). Chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garante essa segurança:

  - Para o modelo de programação "suplemento retorna uma interface do usuário", a única maneira de passar o identificador de janela para uma interface do usuário do suplemento pelo limite de isolamento é chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

  - Para o modelo de programação "suplemento é uma interface do usuário", é necessário substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> no adaptador do suplemento e chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (conforme mostrado nos exemplos anteriores), como chama a implementação de `QueryContract` do adaptador do suplemento do adaptador do lado do host.

- Fornecer proteção contra múltiplas execuções de domínio do aplicativo. Devido a limitações com domínios do aplicativo, as exceções sem tratamento que forem lançadas em domínios do aplicativo do suplemento fazem com que todo o aplicativo falhe, mesmo com a existência do limite de isolamento. No entanto, o WPF e o modelo de suplemento .NET Framework fornecem uma maneira simples de contornar esse problema e melhorar a estabilidade do aplicativo. Um suplemento do WPF que exibe uma interface do usuário cria uma <xref:System.Windows.Threading.Dispatcher> para o thread em que o domínio do aplicativo é executado, se o aplicativo host for um aplicativo do WPF. Você pode detectar todas as exceções sem tratamento que ocorrem no domínio do aplicativo manipulando o <xref:System.Windows.Threading.Dispatcher.UnhandledException> evento da <xref:System.Windows.Threading.Dispatcher>do suplemento do WPF. Você pode obter a <xref:System.Windows.Threading.Dispatcher> da propriedade <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>.

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>Limitações de suplementos WPF

Além dos benefícios que o WPF adiciona aos comportamentos padrão fornecidos por <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>e identificadores de janela, também há limitações para interfaces do usuário de suplementos que são exibidas de aplicativos host:

- As interfaces de usuário de suplemento exibidas em um aplicativo host não respeitam o comportamento de recorte do aplicativo host.

- O conceito de *espaço aéreo* em cenários de interoperabilidade também se aplica a suplementos (consulte [Visão geral das regiões de tecnologia](../advanced/technology-regions-overview.md)).

- Os serviços de interface do usuário de um aplicativo host, como herança de recursos, vinculação de dados e comando, não estão automaticamente disponíveis para as interfaces de usuário do suplemento. Para fornecer esses serviços para o suplemento, você precisa atualizar o pipeline.

- Uma interface do usuário do suplemento não pode ser girada, dimensionada, distorcida ou afetada de outra forma por uma transformação (consulte [visão geral de transformações](../graphics-multimedia/transforms-overview.md)).

- O conteúdo dentro das interfaces do usuário do suplemento que é renderizado por operações de desenho do namespace <xref:System.Drawing> pode incluir a mistura alfa. No entanto, uma interface do usuário do suplemento e a interface do usuário do aplicativo host que a contém deve ser 100% opaca; em outras palavras, a propriedade `Opacity` em ambos deve ser definida como 1.

- Se a propriedade <xref:System.Windows.Window.AllowsTransparency%2A> de uma janela no aplicativo host que contém uma interface do usuário do suplemento for definida como `true`, o suplemento será invisível. Isso é verdadeiro mesmo que a interface do usuário do suplemento seja 100% opaca (ou seja, a propriedade `Opacity` tem um valor de 1).

- Uma interface do usuário do suplemento deve aparecer na parte superior de outros elementos do WPF na mesma janela de nível superior.

- Nenhuma parte da interface do usuário de um suplemento pode ser renderizada usando um <xref:System.Windows.Media.VisualBrush>. Em vez disso, o suplemento pode tirar um instantâneo da interface do usuário gerada para criar um bitmap que pode ser passado para o aplicativo host usando métodos definidos pelo contrato.

- Os arquivos de mídia não podem ser reproduzidos de um <xref:System.Windows.Controls.MediaElement> em uma interface do usuário do suplemento.

- Eventos de mouse gerados para a interface do usuário do suplemento não são recebidos nem gerados pelo aplicativo host, e a propriedade `IsMouseOver` para interface do usuário do aplicativo host tem um valor de `false`.

- Quando o foco muda entre os controles em uma interface do usuário do suplemento, os eventos `GotFocus` e `LostFocus` não são recebidos nem gerados pelo aplicativo host.

- A parte de um aplicativo host que contém uma interface do usuário do suplemento aparece em branco quando impressa.

- Todos os despachantes (consulte <xref:System.Windows.Threading.Dispatcher>) criados pela interface do usuário do suplemento devem ser desligados manualmente antes de o suplemento proprietário ser descarregado se o aplicativo host continuar a execução. O contrato pode implementar métodos que permitem que o aplicativo host sinalize o suplemento antes que o suplemento seja descarregado, permitindo, assim, que a interface do usuário do suplemento desligue seus distribuidores.

- Se uma interface do usuário do suplemento for uma <xref:System.Windows.Controls.InkCanvas> ou contiver uma <xref:System.Windows.Controls.InkCanvas>, você não poderá descarregar o suplemento.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Otimização do desempenho

Por padrão, quando vários domínios de aplicativo são usados, os vários assemblies de .NET Framework exigidos por cada aplicativo são carregados no domínio desse aplicativo. Como resultado, o tempo necessário para criar novos domínios de aplicativo e iniciar aplicativos neles pode afetar o desempenho. No entanto, a .NET Framework fornece uma maneira de reduzir os tempos de início ao instruir os aplicativos a compartilharem assemblies entre domínios de aplicativo se eles já estiverem carregados. Você pode fazer isso usando o atributo <xref:System.LoaderOptimizationAttribute>, que deve ser aplicado ao método de ponto de entrada (`Main`). Nesse caso, você deve usar apenas código para implementar sua definição de aplicativo (consulte [Visão geral de gerenciamento do aplicativo](application-management-overview.md)).

## <a name="see-also"></a>Veja também

- <xref:System.LoaderOptimizationAttribute>
- [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Domínios do aplicativo](../../app-domains/application-domains.md)
- [Visão geral de .NET Framework comunicação remota](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Tornando objetos remotos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Tópicos de instruções](how-to-topics.md)
