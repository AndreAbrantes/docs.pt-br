---
title: Instalar o .NET Core no SLES 12-Gerenciador de pacotes-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no SLES 12.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a40180881ec0962d89f03c2c9d7aad9bbb052d2a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740656"
---
# <a name="sles-12-package-manager---install-net-core"></a>Gerenciador de pacotes SLES 12 – instalar o .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no SLES 12. Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.

## <a name="register-microsoft-key-and-feed"></a>Registrar a chave e o feed da Microsoft

Antes de instalar o .NET, você precisará:

- Registre a chave da Microsoft.
- Registre o repositório do produto.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute o comando a seguir.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalar o ASP.NET Core Runtime

Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
