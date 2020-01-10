---
title: Telemetria do SDK do .NET Core
description: Descubra os recursos de telemetria do SDK do .NET Core que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 8bde344ee393e113502a0895ee55c241cbf24c57
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714110"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="63057-103">Telemetria do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="63057-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="63057-104">O [SDK do .NET Core](index.md) inclui um recurso de telemetria que coleta dados de uso e informações de exceção em caso de falha da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63057-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="63057-105">A CLI do .NET Core é fornecida com o SDK do .NET Core e consiste no conjunto de verbos que permitem criar, testar e publicar os aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63057-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="63057-106">É importante que a equipe do .NET entenda como as ferramentas são usadas para poder melhorá-las.</span><span class="sxs-lookup"><span data-stu-id="63057-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="63057-107">As informações sobre falhas ajudam a equipe a resolver problemas e corrigir bugs.</span><span class="sxs-lookup"><span data-stu-id="63057-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="63057-108">Os dados coletados são anônimos e publicados em agregação sob a [Licença de Atribuição da Creative Commons](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="63057-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="63057-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="63057-109">Scope</span></span>

<span data-ttu-id="63057-110">`dotnet` tem duas funções: executar aplicativos e executar comandos da CLI.</span><span class="sxs-lookup"><span data-stu-id="63057-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="63057-111">A telemetria *não é coletada* durante o uso de `dotnet` para iniciar um aplicativo no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="63057-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="63057-112">A telemetria *é coletada* durante o uso de um dos [comandos da CLI do .NET Core](index.md), como:</span><span class="sxs-lookup"><span data-stu-id="63057-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="63057-113">Como recusar</span><span class="sxs-lookup"><span data-stu-id="63057-113">How to opt out</span></span>

<span data-ttu-id="63057-114">O recurso de telemetria do SDK do .NET Core é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="63057-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="63057-115">Para recusar o recurso de telemetria, defina a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.</span><span class="sxs-lookup"><span data-stu-id="63057-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> 

<span data-ttu-id="63057-116">Uma única entrada de telemetria também é enviada pelo instalador do SDK do .NET Core quando ocorre uma instalação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="63057-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="63057-117">Para recusá-la, defina a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` antes de instalar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63057-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="63057-118">Divulgação</span><span class="sxs-lookup"><span data-stu-id="63057-118">Disclosure</span></span>

<span data-ttu-id="63057-119">O SDK do .NET Core exibe um texto semelhante ao mostrado a seguir quando você executa um dos [comandos da CLI do .NET Core](index.md) pela primeira vez (por exemplo, `dotnet build`).</span><span class="sxs-lookup"><span data-stu-id="63057-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="63057-120">O texto pode variar um pouco dependendo da versão do SDK que você está executando.</span><span class="sxs-lookup"><span data-stu-id="63057-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="63057-121">Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados.</span><span class="sxs-lookup"><span data-stu-id="63057-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a><span data-ttu-id="63057-122">Pontos de dados</span><span class="sxs-lookup"><span data-stu-id="63057-122">Data points</span></span>

<span data-ttu-id="63057-123">O recurso de telemetria não coleta dados pessoais, como nomes de usuário ou endereços de email.</span><span class="sxs-lookup"><span data-stu-id="63057-123">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="63057-124">Ele não examina o código nem extrai dados no nível de projeto, como nome, repositório ou autor.</span><span class="sxs-lookup"><span data-stu-id="63057-124">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="63057-125">Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Azure Monitor](https://azure.microsoft.com/services/monitor/), mantidos em acesso restrito e publicados sob controles de segurança rigorosos por meio dos sistemas seguros do [Armazenamento do Azure](https://azure.microsoft.com/services/storage/).</span><span class="sxs-lookup"><span data-stu-id="63057-125">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="63057-126">A proteção de sua privacidade é importante para nós.</span><span class="sxs-lookup"><span data-stu-id="63057-126">Protecting your privacy is important to us.</span></span> <span data-ttu-id="63057-127">Se você suspeita que a telemetria está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [dotnet/cli](https://github.com/dotnet/cli/issues) ou envie um email para [dotnet@microsoft.com](mailto:dotnet@microsoft.com) para investigação.</span><span class="sxs-lookup"><span data-stu-id="63057-127">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="63057-128">O recurso de telemetria coleta os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="63057-128">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="63057-129">Versões do SDK</span><span class="sxs-lookup"><span data-stu-id="63057-129">SDK versions</span></span> | <span data-ttu-id="63057-130">Dados</span><span class="sxs-lookup"><span data-stu-id="63057-130">Data</span></span> |
|--------------|------|
| <span data-ttu-id="63057-131">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-131">All</span></span>          | <span data-ttu-id="63057-132">Carimbo de data/hora da invocação.</span><span class="sxs-lookup"><span data-stu-id="63057-132">Timestamp of invocation.</span></span> |
| <span data-ttu-id="63057-133">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-133">All</span></span>          | <span data-ttu-id="63057-134">Comando invocado (por exemplo, "build"), com hash no 2.1 em diante.</span><span class="sxs-lookup"><span data-stu-id="63057-134">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="63057-135">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-135">All</span></span>          | <span data-ttu-id="63057-136">Três endereços IP de octeto usados para determinar a localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="63057-136">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="63057-137">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-137">All</span></span>          | <span data-ttu-id="63057-138">Sistema operacional e versão.</span><span class="sxs-lookup"><span data-stu-id="63057-138">Operating system and version.</span></span> |
| <span data-ttu-id="63057-139">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-139">All</span></span>          | <span data-ttu-id="63057-140">RID (ID de runtime) em que o SDK está em execução.</span><span class="sxs-lookup"><span data-stu-id="63057-140">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="63057-141">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-141">All</span></span>          | <span data-ttu-id="63057-142">Versão do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63057-142">.NET Core SDK version.</span></span> |
| <span data-ttu-id="63057-143">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-143">All</span></span>          | <span data-ttu-id="63057-144">Perfil de telemetria: um valor opcional usado somente com o consentimento explícito do usuário e usado internamente na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="63057-144">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="63057-145">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-145">>=2.0</span></span>        | <span data-ttu-id="63057-146">Opções e argumentos de comando: várias opções e vários argumentos são coletados (não cadeias de caracteres arbitrárias).</span><span class="sxs-lookup"><span data-stu-id="63057-146">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="63057-147">Confira [Opções coletadas](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="63057-147">See [collected options](#collected-options).</span></span> <span data-ttu-id="63057-148">Com hash após 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="63057-148">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="63057-149">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-149">>=2.0</span></span>         | <span data-ttu-id="63057-150">Se o SDK está em execução em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="63057-150">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="63057-151">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-151">>=2.0</span></span>         | <span data-ttu-id="63057-152">Estruturas de destino (do evento `TargetFramework`), com hash começando em 2.1.</span><span class="sxs-lookup"><span data-stu-id="63057-152">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="63057-153">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-153">>=2.0</span></span>         | <span data-ttu-id="63057-154">Endereço MAC (controle de acesso à mídia) com hash: uma ID exclusiva e criptograficamente anônima (SHA256) para um computador.</span><span class="sxs-lookup"><span data-stu-id="63057-154">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="63057-155">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-155">>=2.0</span></span>         | <span data-ttu-id="63057-156">Diretório de trabalho atual com hash.</span><span class="sxs-lookup"><span data-stu-id="63057-156">Hashed current working directory.</span></span> |
| <span data-ttu-id="63057-157">>=2.0</span><span class="sxs-lookup"><span data-stu-id="63057-157">>=2.0</span></span>         | <span data-ttu-id="63057-158">Instale o relatório de êxito com o nome de arquivo exe do instalador com hash.</span><span class="sxs-lookup"><span data-stu-id="63057-158">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="63057-159">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="63057-159">>=2.1.300</span></span>     | <span data-ttu-id="63057-160">Versão do kernel.</span><span class="sxs-lookup"><span data-stu-id="63057-160">Kernel version.</span></span> |
| <span data-ttu-id="63057-161">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="63057-161">>=2.1.300</span></span>     | <span data-ttu-id="63057-162">Versão/liberação da Libc.</span><span class="sxs-lookup"><span data-stu-id="63057-162">Libc release/version.</span></span> |
| <span data-ttu-id="63057-163">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="63057-163">>=3.0.100</span></span>     | <span data-ttu-id="63057-164">Indica se a saída foi redirecionada (verdadeiro ou falso).</span><span class="sxs-lookup"><span data-stu-id="63057-164">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="63057-165">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="63057-165">>=3.0.100</span></span>     | <span data-ttu-id="63057-166">Em uma falha da CLI/do SDK, o tipo de exceção e seu rastreamento de pilha (somente o código da CLI/do SDK é incluído no rastreamento de pilha enviado).</span><span class="sxs-lookup"><span data-stu-id="63057-166">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="63057-167">Para obter mais informações, confira [Telemetria de exceção de falha da CLI/do SDK do .NET Core coletada](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="63057-167">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="63057-168">Opções coletadas</span><span class="sxs-lookup"><span data-stu-id="63057-168">Collected options</span></span>

<span data-ttu-id="63057-169">Alguns comandos enviam dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="63057-169">Certain commands send additional data.</span></span> <span data-ttu-id="63057-170">Um subconjunto de comandos envia o primeiro argumento:</span><span class="sxs-lookup"><span data-stu-id="63057-170">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="63057-171">{1&gt;Comando&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63057-171">Command</span></span>               | <span data-ttu-id="63057-172">Dados do primeiro argumento enviados</span><span class="sxs-lookup"><span data-stu-id="63057-172">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="63057-173">A ajuda do comando está sendo consultada.</span><span class="sxs-lookup"><span data-stu-id="63057-173">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="63057-174">O nome do modelo (com hash).</span><span class="sxs-lookup"><span data-stu-id="63057-174">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="63057-175">A palavra `package` ou `reference`.</span><span class="sxs-lookup"><span data-stu-id="63057-175">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="63057-176">A palavra `package` ou `reference`.</span><span class="sxs-lookup"><span data-stu-id="63057-176">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="63057-177">A palavra `package` ou `reference`.</span><span class="sxs-lookup"><span data-stu-id="63057-177">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="63057-178">A palavra `add`, `list` ou `remove`.</span><span class="sxs-lookup"><span data-stu-id="63057-178">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="63057-179">A palavra `delete`, `locals` ou `push`.</span><span class="sxs-lookup"><span data-stu-id="63057-179">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="63057-180">Um subconjunto de comandos envia as opções selecionadas se elas são usadas, juntamente com seus valores:</span><span class="sxs-lookup"><span data-stu-id="63057-180">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="63057-181">Opção</span><span class="sxs-lookup"><span data-stu-id="63057-181">Option</span></span>                  | <span data-ttu-id="63057-182">Comandos</span><span class="sxs-lookup"><span data-stu-id="63057-182">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="63057-183">Todos os comandos</span><span class="sxs-lookup"><span data-stu-id="63057-183">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="63057-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="63057-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="63057-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="63057-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="63057-186">`dotnet build`, `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="63057-186">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="63057-187">Exceto para `--verbosity` e `--sdk-package-version`, todos os outros valores são codificados no SDK 2.1.100 do .NET Core em diante.</span><span class="sxs-lookup"><span data-stu-id="63057-187">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="63057-188">Telemetria de exceção de falha do SDK/da CLI do .NET Core coletada</span><span class="sxs-lookup"><span data-stu-id="63057-188">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="63057-189">Se a CLI/o SDK do .NET Core falhar, o nome da exceção e o rastreamento de pilha do código da CLI/do SDK serão coletados.</span><span class="sxs-lookup"><span data-stu-id="63057-189">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="63057-190">Essas informações são coletadas para avaliar problemas e melhorar a qualidade do SDK e da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63057-190">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="63057-191">Este artigo fornece informações sobre os dados que coletamos.</span><span class="sxs-lookup"><span data-stu-id="63057-191">This article provides information about the data we collect.</span></span> <span data-ttu-id="63057-192">Ele também fornece dicas sobre como os usuários que criam sua própria versão do SDK do .NET Core podem evitar a divulgação não intencional de informações pessoais ou confidenciais.</span><span class="sxs-lookup"><span data-stu-id="63057-192">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="63057-193">Tipos de dados coletados</span><span class="sxs-lookup"><span data-stu-id="63057-193">Types of collected data</span></span>

<span data-ttu-id="63057-194">A CLI do .NET Core coleta informações apenas das exceções da CLI/do SDK, não das exceções no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63057-194">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="63057-195">Os dados coletados contêm o nome da exceção e o rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="63057-195">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="63057-196">Esse rastreamento de pilha é do código da CLI/do SDK.</span><span class="sxs-lookup"><span data-stu-id="63057-196">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="63057-197">O seguinte exemplo mostra os tipos de dados coletados:</span><span class="sxs-lookup"><span data-stu-id="63057-197">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-information"></a><span data-ttu-id="63057-198">Evitar a divulgação não intencional de informações</span><span class="sxs-lookup"><span data-stu-id="63057-198">Avoid inadvertent disclosure information</span></span>

<span data-ttu-id="63057-199">Os colaboradores do .NET Core e qualquer outra pessoa que estejam executando uma versão do SDK do .NET Core criada por conta própria devem considerar o caminho para o código-fonte do SDK.</span><span class="sxs-lookup"><span data-stu-id="63057-199">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="63057-200">Se ocorrer uma falha durante o uso de um SDK do .NET Core que seja um build de depuração personalizado ou configurado com arquivos de símbolo de build personalizado, o caminho do arquivo de origem do SDK do computador de build será coletado como parte do rastreamento de pilha e não terá hash.</span><span class="sxs-lookup"><span data-stu-id="63057-200">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="63057-201">Por isso, os builds personalizados do SDK do .NET Core não devem estar localizados em diretórios cujos nomes de caminho exponham informações pessoais ou confidenciais.</span><span class="sxs-lookup"><span data-stu-id="63057-201">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span> 

## <a name="see-also"></a><span data-ttu-id="63057-202">Veja também</span><span class="sxs-lookup"><span data-stu-id="63057-202">See also</span></span>

- [<span data-ttu-id="63057-203">Telemetria da CLI do .NET Core – dados do T2 de 2019</span><span class="sxs-lookup"><span data-stu-id="63057-203">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="63057-204">Fonte de referência de telemetria (repositório dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="63057-204">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
