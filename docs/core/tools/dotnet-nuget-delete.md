---
title: Comando dotnet nuget delete
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4fa4f24adba251d7872986de4a8b1a63203c36c3
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463578"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Este artigo se aplica a:** ✔️ .NET Core 1.x SDK e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nome

`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [--no-service-endpoint]
    [--non-interactive] [-s|--source <SOURCE>]

dotnet nuget delete -h|--help
```

## <a name="description"></a>Descrição

O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor. Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.

## <a name="arguments"></a>Argumentos

* **`PACKAGE_NAME`**

  Nome/ID do pacote a ser excluído.

* **`PACKAGE_VERSION`**

  Versão do pacote a ser excluído.

## <a name="options"></a>Opções

* **`--force-english-output`**

  Força a execução do aplicativo usando uma cultura invariável com base em inglês.

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

* **`--interactive`**

  Permite que o comando bloqueie e exija ação manual para operações como a autenticação. Opção disponível desde o SDK 2.2 do .NET Core.

* **`-k|--api-key <API_KEY>`**

  A chave da API para o servidor.

* **`--no-service-endpoint`**

  Não acrescenta "api/v2/package" à URL de origem. Opção disponível desde o SDK do .NET Core 2.1.

* **`--non-interactive`**

  Não solicita entrada do usuário ou confirmações.

* **`-s|--source <SOURCE>`**

  Especifica a URL do servidor. URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

## <a name="examples"></a>Exemplos

* Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
