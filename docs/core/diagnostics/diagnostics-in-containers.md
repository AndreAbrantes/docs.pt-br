---
title: Coletar diagnósticos em contêineres
description: Neste artigo, você aprenderá como as ferramentas de diagnóstico do .NET Core podem ser usadas em contêineres do Docker.
ms.date: 09/01/2020
ms.openlocfilehash: e57f3696433bbf6f35b2e3e5d1e72ae8b1e3eeb3
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91451084"
---
# <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="bd8a8-103">Coletar diagnósticos em contêineres</span><span class="sxs-lookup"><span data-stu-id="bd8a8-103">Collect diagnostics in containers</span></span>

<span data-ttu-id="bd8a8-104">As mesmas ferramentas de diagnóstico que são úteis para diagnosticar problemas do .NET Core em outros cenários também funcionam em contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-104">The same diagnostics tools that are useful for diagnosing .NET Core issues in other scenarios also work in Docker containers.</span></span> <span data-ttu-id="bd8a8-105">No entanto, algumas das ferramentas exigem etapas especiais para trabalhar em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-105">However, some of the tools require special steps to work in a container.</span></span> <span data-ttu-id="bd8a8-106">Este artigo aborda como as ferramentas para reunir rastreamentos de desempenho e coletar despejos podem ser usadas em contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-106">This article covers how tools for gathering performance traces and collecting dumps can be used in Docker containers.</span></span>

## <a name="using-net-core-cli-tools-in-a-container"></a><span data-ttu-id="bd8a8-107">Usando ferramentas de CLI do .NET Core em um contêiner</span><span class="sxs-lookup"><span data-stu-id="bd8a8-107">Using .NET Core CLI tools in a container</span></span>

<span data-ttu-id="bd8a8-108">**Essas ferramentas se aplicam a: ✔️** SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bd8a8-108">**These tools apply to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="bd8a8-109">As ferramentas de diagnóstico da CLI global do .NET Core ( [`dotnet-counters`](dotnet-counters.md) , [`dotnet-dump`](dotnet-dump.md) , e [`dotnet-gcdump`](dotnet-gcdump.md) [`dotnet-trace`](dotnet-trace.md) ) foram projetadas para funcionar em uma ampla variedade de ambientes e devem funcionar diretamente em contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-109">The .NET Core global CLI diagnostic tools ([`dotnet-counters`](dotnet-counters.md), [`dotnet-dump`](dotnet-dump.md), [`dotnet-gcdump`](dotnet-gcdump.md), and [`dotnet-trace`](dotnet-trace.md)) are designed to work in a wide variety of environments and should all work directly in Docker containers.</span></span> <span data-ttu-id="bd8a8-110">Por isso, essas ferramentas são o método preferencial para coletar informações de diagnóstico para cenários do .NET Core visando o .NET Core 3,0 ou superior (ou 3,1 ou superior no caso do `dotnet-gcdump` ) em contêineres.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-110">Because of this, these tools are the preferred method of collecting diagnostic information for .NET Core scenarios targeting .NET Core 3.0 or above (or 3.1 or above in the case of `dotnet-gcdump`) in containers.</span></span>

<span data-ttu-id="bd8a8-111">O único fator de complicação de usar essas ferramentas em um contêiner é que elas são instaladas com o SDK do .NET Core e muitos contêineres do Docker são executados sem o SDK do .NET Core presente.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-111">The only complicating factor of using these tools in a container is that they are installed with the .NET Core SDK and many Docker containers run without the .NET Core SDK present.</span></span> <span data-ttu-id="bd8a8-112">Uma solução fácil para esse problema é instalar as ferramentas na imagem inicial do Docker.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-112">One easy solution to this problem is to install the tools in the initial Docker image.</span></span> <span data-ttu-id="bd8a8-113">As ferramentas não precisam do SDK do .NET Core para serem executadas, apenas para serem instaladas.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-113">The tools don't need the .NET Core SDK to run, only to be installed.</span></span> <span data-ttu-id="bd8a8-114">Portanto, é possível criar um Dockerfile com uma compilação de [vários estágios](https://docs.docker.com/develop/develop-images/multistage-build/) que instala as ferramentas em um estágio de compilação (em que o SDK do .NET Core está presente) e, em seguida, copia os binários na imagem final.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-114">Therefore, it's possible to create a Dockerfile with a [multi-stage build](https://docs.docker.com/develop/develop-images/multistage-build/) that installs the tools in a build stage (where the .NET Core SDK is present) and then copies the binaries into the final image.</span></span> <span data-ttu-id="bd8a8-115">A única desvantagem dessa abordagem é o tamanho maior da imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-115">The only downside to this approach is increased Docker image size.</span></span>

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

<span data-ttu-id="bd8a8-116">Como alternativa, o SDK do .NET Core pode ser instalado em um contêiner quando necessário para instalar as ferramentas da CLI.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-116">Alternatively, the .NET Core SDK can be installed in a container when needed in order to install the CLI tools.</span></span> <span data-ttu-id="bd8a8-117">Lembre-se de que a instalação do SDK do .NET Core terá o efeito colateral de reinstalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-117">Be aware that installing the .NET Core SDK will have the side-effect of reinstalling the .NET Core runtime.</span></span> <span data-ttu-id="bd8a8-118">Portanto, certifique-se de instalar a versão do SDK que corresponde ao tempo de execução presente no contêiner.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-118">So be sure to install the version of the SDK that matches the runtime present in the container.</span></span>

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a><span data-ttu-id="bd8a8-119">Usando as ferramentas da CLI global do .NET Core em um contêiner sidecar</span><span class="sxs-lookup"><span data-stu-id="bd8a8-119">Using .NET Core global CLI tools in a sidecar container</span></span>

<span data-ttu-id="bd8a8-120">Se você quiser usar as ferramentas de diagnóstico da CLI global do .NET Core para diagnosticar processos em um contêiner diferente, tenha em mente os seguintes requisitos adicionais:</span><span class="sxs-lookup"><span data-stu-id="bd8a8-120">If you would like to use .NET Core global CLI diagnostic tools to diagnose processes in a different container, bear the following additional requirements in mind:</span></span>

1. <span data-ttu-id="bd8a8-121">Os contêineres devem [compartilhar um namespace de processo](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (para que as ferramentas no contêiner sidecar possam acessar processos no contêiner de destino).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-121">The containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (so that tools in the sidecar container can access processes in the target container).</span></span>
2. <span data-ttu-id="bd8a8-122">As ferramentas de diagnóstico da CLI global do .NET Core precisam acessar os arquivos que o tempo de execução do .NET Core grava no diretório/tmp, de modo que o diretório/tmp deve ser compartilhado entre o contêiner de destino e o sidecar por meio de uma montagem de volume.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-122">The .NET Core global CLI diagnostic tools need access to files the .NET Core runtime writes to the /tmp directory, so the /tmp directory must be shared between the target and sidecar container via a volume mount.</span></span> <span data-ttu-id="bd8a8-123">Isso pode ser feito, por exemplo, fazendo com que os contêineres compartilhem um [volume comum ou um volume kubernetes](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) .</span><span class="sxs-lookup"><span data-stu-id="bd8a8-123">This could be done, for example, by having the containers share a common [volume](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) or a Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) volume.</span></span> <span data-ttu-id="bd8a8-124">Se você tentar usar as ferramentas de diagnóstico de um contêiner sidecar sem compartilhar o diretório/tmp, receberá um erro sobre o processo "não está executando o tempo de execução do .NET compatível".</span><span class="sxs-lookup"><span data-stu-id="bd8a8-124">If you attempt to use the diagnostic tools from a sidecar container without sharing the /tmp directory, you will get an error about the process "not running compatible .NET runtime."</span></span>

## <a name="using-perfcollect-in-a-container"></a><span data-ttu-id="bd8a8-125">Usando `PerfCollect` em um contêiner</span><span class="sxs-lookup"><span data-stu-id="bd8a8-125">Using `PerfCollect` in a container</span></span>

<span data-ttu-id="bd8a8-126">**Essa ferramenta se aplica a: ✔️** .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bd8a8-126">**This tool applies to: ✔️** .NET Core 2.1 and later versions</span></span>

<span data-ttu-id="bd8a8-127">O [`PerfCollect`](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/linux-performance-tracing.md) script é útil para coletar rastreamentos de desempenho e é a ferramenta recomendada para coletar rastreamentos antes do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-127">The [`PerfCollect`](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/linux-performance-tracing.md) script is useful for collecting performance traces and is the recommended tool for collecting traces prior to .NET Core 3.0.</span></span> <span data-ttu-id="bd8a8-128">Se estiver usando `PerfCollect` em um contêiner, tenha em mente os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="bd8a8-128">If using `PerfCollect` in a container, keep the following requirements in mind:</span></span>

1. <span data-ttu-id="bd8a8-129">`PerfCollect`requer o [ `SYS_ADMIN` recurso](https://man7.org/linux/man-pages/man7/capabilities.7.html) (para executar a `perf` ferramenta), portanto, verifique se o contêiner foi [iniciado com esse recurso](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-129">`PerfCollect` requires the [`SYS_ADMIN` capability](https://man7.org/linux/man-pages/man7/capabilities.7.html) (in order to run the `perf` tool), so be sure the container is [started with that capability](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span></span>
2. <span data-ttu-id="bd8a8-130">`PerfCollect` requer que algumas variáveis de ambiente sejam definidas antes do aplicativo que está iniciando a criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-130">`PerfCollect` requires some environment variables be set prior to the app it is profiling starting.</span></span> <span data-ttu-id="bd8a8-131">Eles podem ser definidos em um [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) ou ao [iniciar o contêiner](https://docs.docker.com/engine/reference/run/#env-environment-variables).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-131">These can be set either in a [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) or when [starting the container](https://docs.docker.com/engine/reference/run/#env-environment-variables).</span></span> <span data-ttu-id="bd8a8-132">Como essas variáveis não devem ser definidas em ambientes de produção normais, é comum apenas adicioná-las ao iniciar um contêiner cujo perfil será criado.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-132">Because these variables shouldn't be set in normal production environments, it's common to just add them when starting a container that will be profiled.</span></span> <span data-ttu-id="bd8a8-133">As duas variáveis que o PerfCollect requer são:</span><span class="sxs-lookup"><span data-stu-id="bd8a8-133">The two variables which PerfCollect requires are:</span></span>
    1. <span data-ttu-id="bd8a8-134">COMPlus_PerfMapEnabled = 1</span><span class="sxs-lookup"><span data-stu-id="bd8a8-134">COMPlus_PerfMapEnabled=1</span></span>
    1. <span data-ttu-id="bd8a8-135">COMPlus_EnableEventLog = 1</span><span class="sxs-lookup"><span data-stu-id="bd8a8-135">COMPlus_EnableEventLog=1</span></span>

### <a name="using-perfcollect-in-a-sidecar-container"></a><span data-ttu-id="bd8a8-136">Usando `PerfCollect` em um contêiner sidecar</span><span class="sxs-lookup"><span data-stu-id="bd8a8-136">Using `PerfCollect` in a sidecar container</span></span>

<span data-ttu-id="bd8a8-137">Se você quiser executar `PerfCollect` em um contêiner para criar o perfil de um processo do .NET Core em um contêiner diferente, a experiência será quase a mesma, exceto para essas diferenças:</span><span class="sxs-lookup"><span data-stu-id="bd8a8-137">If you would like to run `PerfCollect` in one container to profile a .NET Core process in a different container, the experience is almost the same except for these differences:</span></span>

1. <span data-ttu-id="bd8a8-138">As variáveis de ambiente mencionadas anteriormente (COMPlus_PerfMapEnabled e COMPlus_EnableEventLog) devem ser definidas para o contêiner de destino (não o que está em execução `PerfCollect` ).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-138">The environment variables mentioned previously (COMPlus_PerfMapEnabled and COMPlus_EnableEventLog) must be set for the target container (not the one running `PerfCollect`).</span></span>
2. <span data-ttu-id="bd8a8-139">O contêiner em execução `PerfCollect` deve ter a `SYS_ADMIN` capacidade (não o contêiner de destino).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-139">The container running `PerfCollect` must have the `SYS_ADMIN` capability (not the target container).</span></span>
3. <span data-ttu-id="bd8a8-140">Os dois contêineres devem [compartilhar um namespace de processo](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-140">The two containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span></span>

## <a name="using-createdump-in-a-container"></a><span data-ttu-id="bd8a8-141">Usando `createdump` em um contêiner</span><span class="sxs-lookup"><span data-stu-id="bd8a8-141">Using `createdump` in a container</span></span>

<span data-ttu-id="bd8a8-142">**Essa ferramenta se aplica a: ✔️** .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bd8a8-142">**This tool applies to: ✔️** .NET Core 2.1 and later versions</span></span>

<span data-ttu-id="bd8a8-143">Uma alternativa ao `dotnet-dump` , [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) pode ser usada para criar dumps de núcleo no Linux contendo informações nativas e gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="bd8a8-143">An alternative to `dotnet-dump`, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can be used for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="bd8a8-144">A `createdump` ferramenta é instalada com o tempo de execução do .NET Core e pode ser encontrada ao lado de libcoreclr.so (normalmente em "/usr/share/dotnet/Shared/Microsoft.NETCore.app/[Version]").</span><span class="sxs-lookup"><span data-stu-id="bd8a8-144">The `createdump` tool is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="bd8a8-145">A ferramenta funciona da mesma forma em um contêiner como acontece em ambientes Linux não-contêineres, com a única exceção de que a ferramenta requer o [ `SYS_PTRACE` recurso](https://man7.org/linux/man-pages/man7/capabilities.7.html), portanto, o contêiner do Docker deve ser [iniciado com esse recurso](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-145">The tool works the same in a container as it does in non-containerized Linux environments with the single exception that the tool requires the [`SYS_PTRACE` capability](https://man7.org/linux/man-pages/man7/capabilities.7.html), so the Docker container must be [started with that capability](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span></span>

### <a name="using-createdump-in-a-sidecar-container"></a><span data-ttu-id="bd8a8-146">Usando `createdump` em um contêiner sidecar</span><span class="sxs-lookup"><span data-stu-id="bd8a8-146">Using `createdump` in a sidecar container</span></span>

<span data-ttu-id="bd8a8-147">Se você quiser usar o `createdump` para criar um despejo de um processo em um contêiner diferente, a experiência será quase a mesma, exceto para essas diferenças:</span><span class="sxs-lookup"><span data-stu-id="bd8a8-147">If you would like to use `createdump` to create a dump from a process in a different container, the experience is almost the same except for these differences:</span></span>

1. <span data-ttu-id="bd8a8-148">O contêiner em execução `createdump` deve ter a `SYS_PTRACE` capacidade (não o contêiner de destino).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-148">The container running `createdump` must have the `SYS_PTRACE` capability (not the target container).</span></span>
2. <span data-ttu-id="bd8a8-149">Os dois contêineres devem [compartilhar um namespace de processo](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span><span class="sxs-lookup"><span data-stu-id="bd8a8-149">The two containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span></span>