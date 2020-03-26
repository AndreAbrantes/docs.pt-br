---
title: 'Instruções passo a passo: localizando um aplicativo híbrido'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111108"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Instruções passo a passo: localizando um aplicativo híbrido

Este passo a passo mostra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como localizar elementos em um aplicativo híbrido baseado no Windows Forms.

As tarefas ilustradas neste passo a passo incluem:

- Criando o projeto de host do Windows Forms.

- Atributo de conteúdo localizável.

- Habilitando a localização.

- Atribuindo identificadores de recursos.

- Usando a ferramenta LocBaml para produzir um assembly satélite.

Para obter uma lista completa de códigodas das tarefas ilustradas neste passo a passo, consulte [Localing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).

Quando tiver terminado, você terá um aplicativo híbrido localizado.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará dos seguintes componentes para concluir este passo a passo:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Criando o projeto de host do Windows Forms

O primeiro passo é criar o projeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de aplicativo Do Windows Forms e adicionar um elemento com conteúdo que você irá localizar.

### <a name="to-create-the-host-project"></a>Criar o projeto de host

1. Crie um projeto **wpf app** chamado `LocalizingWpfInWf`.  (**Arquivo** > **Novo** > **Projeto** > Visual**C#** ou Visual **Basic** > Classic**Desktop** > **WPF Application**).

2. Adicione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> um `SimpleControl` elemento chamado ao projeto.

3. Use <xref:System.Windows.Forms.Integration.ElementHost> o controle `SimpleControl` para colocar um elemento no formulário. Para obter mais informações, consulte [Passo a Passo: Hospedando um controle composto 3D WPF em formulários windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Adicionando conteúdo localizável

Em seguida, você adicionará um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de rótulo do Windows Forms e definirá o conteúdo do elemento como uma seqüência de string satisfaz.

### <a name="to-add-localizable-content"></a>Para adicionar um conteúdo localizável

1. No **Solution Explorer**, clique duas vezes em **SimpleControl.xaml** para abri-lo no WPF Designer.

2. Defina o <xref:System.Windows.Controls.Button> conteúdo do controle usando o seguinte código.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. No **Solution Explorer,** clique duas vezes em **Formulário1** para abri-lo no Windows Forms Designer.

4. Abra a **caixa de ferramentas** e clique duas vezes em **Etiqueta** para adicionar um controle de etiqueta ao formulário. Defina o <xref:System.Windows.Forms.Control.Text%2A> valor `"Hello"`de sua propriedade para .

5. Pressione **F5** para construir e executar o aplicativo.

     Tanto `SimpleControl` o elemento quanto o controle da etiqueta exibem o texto **"Olá".**

## <a name="enabling-localization"></a>Habilitando a localização

O Designer de Formulários do Windows fornece configurações para habilitar a localização em um assembly satélite.

### <a name="to-enable-localization"></a>Para permitir a localização

1. No **Solution Explorer,** clique duas vezes **em Form1.cs** para abri-lo no Windows Forms Designer.

2. Na janela **Propriedades,** defina o valor da propriedade `true` **Localizable** do formulário como .

3. Na janela **Propriedades,** defina o valor da propriedade **do idioma** para **espanhol (Espanha)**.

4. No Designer de Formulários do Windows, selecione o controle de rótulo.

5. Na janela **Propriedades,** defina <xref:System.Windows.Forms.Control.Text%2A> o `"Hola"`valor do imóvel como .

     Um novo arquivo de recursos chamado Form1.es-ES.resx é adicionado ao projeto.

6. No **Solution Explorer,** clique com o botão **direito do Form1.cs** e clique em Exibir **Código** para abri-lo no Editor de códigos.

7. Copie o seguinte `Form1` código no construtor, `InitializeComponent`precedendo a chamada para .

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. No **Solution Explorer,** clique com o botão direito do mouse **LocalizingWpfInWf** e clique **em Descarregar projeto**.

     O nome do projeto está rotulado **(indisponível)**.

9. Clique com o botão direito do mouse **LocalizingWpfInWf**e clique **em Editar LocalizingWpfInWf.csproj**.

     O arquivo de projeto é aberto no Editor de Códigos.

10. Copie a linha a `PropertyGroup` seguir na primeira no arquivo do projeto.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Salve o arquivo de projeto e feche-o.

12. No **Solution Explorer,** clique com o botão direito do mouse **LocalizingWpfInWf** e clique em **Recarregar projeto**.

## <a name="assigning-resource-identifiers"></a>Atribuindo identificadores de recursos

Você pode mapear o conteúdo localizável para assemblies de recursos usando identificadores de recurso. O aplicativo MsBuild.exe atribui automaticamente identificadores de `updateuid` recursos quando você especifica a opção.

### <a name="to-assign-resource-identifiers"></a>Para atribuir identificadores de recursos

1. A partir do menu Iniciar, abra o Prompt de comando do desenvolvedor para o Visual Studio.

2. Use o comando a seguir para atribuir identificadores de recurso ao seu conteúdo localizável.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. No **Solution Explorer**, clique duas vezes em **SimpleControl.xaml** para abri-lo no Editor de códigos. Você verá que `msbuild` o comando `Uid` adicionou o atributo a todos os elementos. Isso facilita a localização por meio da atribuição de identificadores de recurso.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Pressione **F6** para criar a solução.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Usando LocBaml para produzir um assembly satélite

Seu conteúdo localizado é armazenado em um conjunto de *satélite*somente com recursos . Use a ferramenta de linha de comando LocBaml.exe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para produzir um conjunto localizado para o seu conteúdo.

### <a name="to-produce-a-satellite-assembly"></a>Para produzir um assembly satélite

1. Copie LocBaml.exe para sua pasta do projeto obj\Debug. Para obter mais informações, consulte [Localize an Application](how-to-localize-an-application.md).

2. Na janela do Prompt de Comando, use o seguinte comando para extrair cadeias de caracteres de recurso em um arquivo temporário.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Abra o arquivo temporário.csv com o Visual Studio ou outro editor de texto. Substitua `"Hello"` a corda por `"Hola"`sua tradução em espanhol, .

4. Salve o arquivo temp.csv.

5. Use o seguinte comando para gerar o arquivo de recurso localizado.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     O arquivo LocalizingWpfInWf.g.es-ES.resources é criado na pasta obj\Debug.

6. Use o seguinte comando para compilar o assembly satélite localizado.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     O arquivo LocalizingWpfInWf.resources.dll é criado na pasta obj\Debug.

7. Copie o arquivo LocalizingWpfInWf.resources.dll para a pasta do projeto bin\Debug\es-ES. Substitua o arquivo existente.

8. Execute LocalizingWpfInWf.exe, que está localizado na pasta bin\Debug de seu projeto. Não recompilar o aplicativo ou o assembly satélite será substituído.

     O aplicativo mostra as cadeias de caracteres localizadas em vez de cadeias de caracteres em inglês.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Localize um aplicativo](how-to-localize-an-application.md)
- [Instruções passo a passo: localizando Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
