---
title: Introdução ao C# e ao Visual Studio Code
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: fdf26d67ca06ffb5ae9f8c12aa29819280770d5c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715314"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Introdução ao C# e ao Visual Studio Code

O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS. Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

1. Instalar o [Visual Studio Code](https://code.visualstudio.com/).
2. Instalar o [SDK do .NET Core](https://dotnet.microsoft.com/download).
3. Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) para o Visual Studio Code. Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Vamos começar com um simples programa "Olá, Mundo" no .NET Core:

1. Abra um projeto:

    - Abra o Visual Studio Core.
    - Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**.
    - Selecione **Arquivo** > **Abrir Pasta** no menu principal para abrir a pasta na qual deseja colocar o projeto C# e clique em **Selecionar Pasta**. Para nosso exemplo, estamos criando uma pasta para nosso projeto chamado *HelloWorld*.

      ![Pasta aberta do Visual Studio Code](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicialize um projeto em C#:

    - Abra o Terminal Integrado do Visual Studio Code selecionando **Exibir** > **Terminal Integrado** no menu principal.
    - Na janela do terminal, digite `dotnet new console`.
    - Este comando cria um arquivo *Program.cs* em sua pasta com um programa simples de "Olá, mundo" já gravado, juntamente com C# um arquivo de projeto chamado *HelloWorld. csproj*.

      ![O novo comando dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Resolva os ativos do build:

    - Para o **.NET Core 1.x**, digite `dotnet restore`. Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.

      ![O comando de restauração dotnet](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Execute o programa "Olá, Mundo":

    - Digite `dotnet run`.

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Depuração

1. Abra *Program.cs* clicando nele. Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. O Visual Studio Code deverá solicitar que você adicione os ativos ausentes para compilar e depurar o aplicativo. Selecione **Sim**.

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.

    ![Abrir a guia Depurar no Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. Localize a seta verde na parte superior do painel. Certifique-se de que a lista suspensa ao lado dele tenha a **inicialização do .NET Core (console)** selecionada.

    ![Selecionando o .NET Core no Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Para iniciar a depuração, pressione <kbd>F5</kbd> ou selecione a seta verde. O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.
    - Durante a depuração, você pode exibir as variáveis locais no painel superior esquerdo ou usar o console de depuração.

7. Selecione a seta azul na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interromper o processamento.

    ![Execução e depuração no Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Adicionar uma classe

1. Para adicionar uma nova classe, clique com o botão direito do mouse no VSCode Explorer e selecione **novo arquivo**. Isso adiciona um novo arquivo à pasta que você abriu no VSCode.
2. Nomeie o arquivo *MyClass.cs*. Salve-o com uma extensão `.cs` no final para que ele seja reconhecido como um arquivo csharp.
3. Adicione o código a seguir para criar sua primeira classe. Certifique-se de incluir o namespace correto para que você possa referenciá-lo do arquivo *Program.cs* :

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. Chame sua nova classe de seu método principal no *Program.cs* adicionando o código abaixo:

    ```csharp
    using System;
    
    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Salve as alterações e execute o programa novamente. A nova mensagem deve aparecer com a cadeia de caracteres acrescentada.

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Perguntas frequentes

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code. Meu depurador diz: "Nenhuma configuração".

A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você. O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez. Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug". Selecionar isso gera os arquivos de configuração *. vscode*, *Launch. JSON*e *Tasks. JSON* necessários.

## <a name="see-also"></a>Veja também

- [Configurando o Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Depurando no Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
