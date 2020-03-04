---
title: Dependências de SDK do .NET Core e tempo de execução-.NET Core
description: Detalha o sistema operacional e os pré-requisitos de arquitetura de CPU para instalar o SDK do .NET Core e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157798"
---
# <a name="net-core-dependencies-and-requirements"></a>Dependências e requisitos do .NET Core

Este artigo detalha quais sistemas operacionais e arquitetura de CPU têm suporte no .NET Core.

## <a name="supported-operating-systems"></a>Sistemas operacionais compatíveis

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

As seguintes versões do Windows têm suporte com o .NET Core 3,1:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Versão 1803 +                  | x64, ARM32      |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

As seguintes versões do Windows têm suporte com o .NET Core 3,0:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Versão 1803 +                  | x64, ARM32      |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

As seguintes versões do Windows têm suporte com o .NET Core 2,2:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Versão 1803 +                   | x64, ARM32      |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

As seguintes versões do Windows têm suporte com o .NET Core 2,1:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Versão 1803 +                  | x86            |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7/Vista/8,1/servidor 2008 R2

Dependências adicionais serão necessárias se você estiver instalando o SDK do .NET ou o tempo de execução nas seguintes versões do Windows:

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Instale o seguinte:

- [Atualização 3 C++ do Microsoft Visual 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Os requisitos acima também serão necessários se você vir entre um dos seguintes erros:

> O programa não pode ser iniciado porque *API-MS-Win-CRT-Runtime-L1-1-0. dll* está ausente do seu computador. Tente reinstalar o programa para corrigir esse problema.
>
> \- ou –
>
> A biblioteca *hostfxr. dll* foi encontrada, mas está sendo carregada de *C:\\\<path_to_app >\\hostfxr. dll* falhou.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

O .NET Core 3,1 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 3,1 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             | Versão               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | mais de 18 anos                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10 +                 | x64, ARM64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Para obter mais informações sobre como instalar o .NET Core 3,1 em ARM64 (kernel 4.14 +), consulte [instalando o .net core 3,0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> O suporte a ARM64 requer o kernel do Linux 4,14 ou superior. Algumas distribuições do Linux atendem a esse requisito, enquanto outras não. Por exemplo, o Ubuntu 18, 4 tem suporte, mas o Ubuntu 16, 4 não.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

O .NET Core 3,0 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             | Versão               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | mais de 18 anos                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

O .NET Core 2,2 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             |  Versão                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 18,10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

O .NET Core 2,1 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             |  Versão                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29 +                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 19, 4, 19,10    | x64, ARM32 |
| Linux Mint                     |  17+                    | x64 |
| openSUSE                       |  15 +                    | x64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

Com base em sua distribuição do Linux, talvez seja necessário instalar dependências adicionais.

> [!IMPORTANT]
> Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.

### <a name="ubuntu"></a>Ubuntu

As distribuições do Ubuntu exigem que as seguintes bibliotecas sejam instaladas:

- liblttng-ust0
- libcurl3 (para 14.x e 16.x)
- libcurl4 (para 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (para 14.x)
- libicu55 (para 16.x)
- libicu57 (para 17.x)
- libicu60 (para 18.x)

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS e Fedora

As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Usuários do Fedora: se a versão do OpenSSL > = 1,1, você precisará instalar o **compat-openssl10**.

Para o .NET Core 2,0, as seguintes dependências também são necessárias:

- libunwind
- libuuid

Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

O .NET Core tem suporte nas seguintes versões do macOS:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Versão do .NET Core | macOS                 | Arquiteturas |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Alta serra (10.13 +)  | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Alta serra (10.13 +)  | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

A partir do macOS Catalina (versão 10,15), todo software criado após 1º de junho de 2019 que é distribuído com a ID do desenvolvedor deve ser notarized. Esse requisito se aplica ao tempo de execução do .NET Core, SDK do .NET Core e software criado com o .NET Core.

Os instaladores do .NET Core (Runtime e SDK) versões 3,1, 3,0 e 2,1, foram notarizeddos desde 18 de fevereiro de 2020. Versões anteriores liberadas não são notarized. Se você executar um aplicativo não notarized, verá um erro semelhante à imagem a seguir:

![alerta de notarization Catalina do macOS](media/dependencies/macos-notarized-pkg-warning.png)

Para obter mais informações sobre como o imforced-notarization afeta o .NET Core (e seus aplicativos .NET Core), consulte [trabalhando com o MacOS Catalina notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.

Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS. Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Próximas etapas

- Para desenvolver e executar aplicativos, instale o [SDK do .NET Core](sdk.md) (inclui o tempo de execução).
- Para executar aplicativos que outras pessoas criaram, instale o [tempo de execução do .NET Core](runtime.md).
