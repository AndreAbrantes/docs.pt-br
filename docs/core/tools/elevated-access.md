---
title: Acesso elevado para os comandos dotnet
description: Conheça as melhores práticas para os comandos dotnet que exigem acesso elevado.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156758"
---
# <a name="elevated-access-for-dotnet-commands"></a>Acesso elevado para os comandos dotnet

As melhores práticas de desenvolvimento de software orientam os desenvolvedores a escrever um software que exija o mínimo de privilégios. No entanto, alguns softwares, como as ferramentas de monitoramento de desempenho, requerem permissão de administrador devido a regras do sistema operacional. As diretrizes a seguir descrevem os cenários compatíveis com a gravação desse software com o .NET Core.

Os seguintes comandos podem ser executados com privilégios elevados:

- comandos `dotnet tool`, como [instalação de ferramenta dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Não recomendamos executar outros comandos com privilégios elevados. Particularmente, não recomendamos privilégios elevados com comandos que usam o MSBuild, como [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md) e [dotnet run](dotnet-run.md). O principal problema é o gerenciamento de permissões quando um usuário faz a transição entre a raiz e uma conta restrita várias vezes após a emissão de comandos dotnet. Você pode achar, como um usuário restrito, que não tem acesso ao arquivo criado por um usuário raiz. Existem maneiras de resolver esta situação, mas não é necessário entrar nesse assunto agora.

Você pode executar comandos como raiz, desde que não faça a transição várias vezes entre raiz e uma conta restrita. Por exemplo, os contêineres do Docker são executados como raiz por padrão, então eles têm essa característica.

## <a name="global-tool-installation"></a>Instalação da ferramenta global

As instruções a seguir mostram a maneira recomendada para instalar, executar e desinstalar as ferramentas do .NET Core que exigem permissões com privilégios elevados para executar.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Instale a ferramenta

Se a pasta `%ProgramFiles%\dotnet-tools` já existir, faça o seguinte para verificar se o grupo “Usuários” tem permissão para gravar ou modificar esse diretório:

- Clique com `%ProgramFiles%\dotnet-tools` o botão direito do mouse na pasta e selecione **Propriedades**. A caixa de diálogo **Propriedades Comuns** é aberta.
- Selecione a guia **Segurança.** Em **Grupo ou nomes de usuários,** verifique se o grupo "Usuários" tem permissão para escrever ou modificar o diretório.
- Se o grupo “Usuários” puder gravar ou modificar o diretório, use um nome de diretório diferente ao instalar as ferramentas em vez de *dotnet-tools*.

Para instalar as ferramentas, execute o seguinte comando no prompt com privilégios elevados. Ele criará a pasta *dotnet-tools* durante a instalação.

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Executar a ferramenta global

**Opção 1** Usar o caminho completo com prompt com privilégios elevados:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Opção 2** Adicionar a pasta recém-criada ao `%Path%`. Você só precisa fazer essa operação uma vez.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

E execute com:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Desinstalar a ferramenta global

No prompt de privilégios elevados, digite o seguinte comando:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Ferramentas locais

As ferramentas locais têm escopo por árvore de subdiretório, por usuário. Quando executadas com privilégios elevados, as ferramentas locais compartilham um ambiente de usuário restrito com o ambiente com privilégios elevados. No Linux e no macOS, isso resulta em arquivos sendo definidos com acesso somente para o usuário raiz. Se o usuário voltar para uma conta restrita, ele não poderá acessar ou gravar arquivos. Então, não é recomendado instalar as ferramentas que exigem elevação como ferramentas locais. Em vez disso, use a opção `--tool-path` e as diretrizes anteriores de ferramentas globais.

## <a name="elevation-during-development"></a>Elevação durante o desenvolvimento

Durante o desenvolvimento, talvez você precise de acesso com privilégios elevados para testar seu aplicativo. Esse cenário é comum para aplicativos de IoT, por exemplo. É recomendável que você compile o aplicativo sem elevação e, em seguida, execute-o com elevação. Há alguns padrões, como abaixo:

- Usando o executável gerado (fornece o melhor desempenho de inicialização):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- O uso do comando [dotnet run](dotnet-run.md) com o `—no-build` sinalizador para evitar a geração de novos binários:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Confira também

- [Visão geral das Ferramentas Globais do .NET Core](global-tools.md)
