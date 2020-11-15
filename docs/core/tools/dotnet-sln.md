---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 02/14/2020
ms.openlocfilehash: 898c53772a28b8cc3b65532dfc3d9bd6e73d467c
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634364"
---
# <a name="dotnet-sln"></a>dotnet sln

**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores

## <a name="name"></a>Name

`dotnet sln` -Lista ou modifica os projetos em um arquivo de solução .NET.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>Description

O `dotnet sln` comando fornece uma maneira conveniente de listar e modificar projetos em um arquivo de solução.

Para usar o comando `dotnet sln`, o arquivo de solução já deve existir. Se você precisar criar um, use o comando [dotnet New](dotnet-new.md) , como no exemplo a seguir:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se esse argumento for omitido, o comando pesquisará o diretório atual em busca de um. Se ele não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

## <a name="commands"></a>Comandos

### `list`

Lista todos os projetos em um arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se esse argumento for omitido, o comando pesquisará o diretório atual em busca de um. Se ele não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.
  
### `add`

Adiciona um ou mais projetos ao arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará o diretório atual em busca de um e falhará se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos a serem adicionados à solução. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo `dotnet sln` comando.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

- **`--in-root`**

  Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução. Disponível desde o SDK do .NET Core 3.0.

- **`-s|--solution-folder <PATH>`**

  O caminho da pasta da solução de destino para a qual adicionar os projetos. Disponível desde o SDK do .NET Core 3.0.

### `remove`

Remova um projeto ou vários projetos do arquivo da solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se for Left não especificado, o comando pesquisará o diretório atual em busca de um e falhará se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos a serem adicionados à solução. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo `dotnet sln` comando.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

## <a name="examples"></a>Exemplos

- Listar os projetos em uma solução:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Adicione um projeto C# a uma solução:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Remova um projeto C# de uma solução:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Adicione vários projetos C# à raiz de uma solução:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Adicione vários projetos C# a uma solução:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Remova vários projetos C# de uma solução:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Adicionar vários projetos C# a uma solução usando um padrão de mascaramento (somente UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Adicionar vários projetos C# a uma solução usando um padrão de mascaramento (somente Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- Remover vários projetos C# de uma solução usando um padrão de mascaramento (somente UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Remover vários projetos C# de uma solução usando um padrão de mascaramento (somente Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
