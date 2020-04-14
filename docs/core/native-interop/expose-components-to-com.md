---
title: Expondo componentes do .NET Core ao COM
description: Este tutorial mostra como expor uma classe ao COM a partir do .NET Core. Você gera um servidor COM e um manifesto de servidor lado a lado para com.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242862"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="8eb90-104">Expondo componentes do .NET Core ao COM</span><span class="sxs-lookup"><span data-stu-id="8eb90-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="8eb90-105">No .NET Core, o processo de expor seus objetos .NET ao COM foi significativamente simplificado em comparação com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8eb90-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="8eb90-106">O processo a seguir explicará como expor uma classe ao COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="8eb90-107">Este tutorial mostra como:</span><span class="sxs-lookup"><span data-stu-id="8eb90-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="8eb90-108">Expor uma classe ao COM do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8eb90-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="8eb90-109">Gerar um servidor COM como parte de criar sua biblioteca do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8eb90-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="8eb90-110">Gerar automaticamente um manifesto de servidor lado a lado para COM Sem Registro.</span><span class="sxs-lookup"><span data-stu-id="8eb90-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8eb90-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8eb90-111">Prerequisites</span></span>

- <span data-ttu-id="8eb90-112">Instale [o .NET Core 3.0 SDK](https://dotnet.microsoft.com/download) ou uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="8eb90-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="8eb90-113">Criar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="8eb90-113">Create the library</span></span>

<span data-ttu-id="8eb90-114">A primeira etapa é criar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="8eb90-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="8eb90-115">Crie uma nova pasta e, nessa pasta, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="8eb90-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="8eb90-116">Abra o `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="8eb90-117">Adicione `using System.Runtime.InteropServices;` ao topo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8eb90-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="8eb90-118">Crie uma interface chamada `IServer`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="8eb90-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8eb90-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="8eb90-120">Adicione o atributo `[Guid("<IID>")]` à interface, com o GUID da interface COM que você está implementando.</span><span class="sxs-lookup"><span data-stu-id="8eb90-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="8eb90-121">Por exemplo, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="8eb90-122">Observe que esse GUID precisa ser exclusivo, pois é o único identificador dessa interface para COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="8eb90-123">No Visual Studio, você pode gerar um GUID acessando Ferramentas > Criar GUID para abrir a ferramenta Criar GUID.</span><span class="sxs-lookup"><span data-stu-id="8eb90-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="8eb90-124">Adicione o atributo `[InterfaceType]` à interface e especifique quais interfaces COM base sua interface deve implementar.</span><span class="sxs-lookup"><span data-stu-id="8eb90-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="8eb90-125">Crie uma classe chamada `Server` que implementa `IServer`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="8eb90-126">Adicione o atributo `[Guid("<CLSID>")]` à classe, com o GUID do identificador de classe da classe COM que você está implementando.</span><span class="sxs-lookup"><span data-stu-id="8eb90-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="8eb90-127">Por exemplo, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="8eb90-128">Como ocorre com o GUID da interface, esse GUID deve ser exclusivo pois é o único identificador dessa interface para COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="8eb90-129">Adicione o atributo `[ComVisible(true)]` à interface e à classe.</span><span class="sxs-lookup"><span data-stu-id="8eb90-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8eb90-130">Diferentemente do .NET Framework, o .NET Core exige que você especifique o CLSID de qualquer classe que você deseja que seja ativável por meio do COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="8eb90-131">Gerar o host COM</span><span class="sxs-lookup"><span data-stu-id="8eb90-131">Generate the COM host</span></span>

1. <span data-ttu-id="8eb90-132">Abra o arquivo de projeto `.csproj` e adicione `<EnableComHosting>true</EnableComHosting>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="8eb90-133">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="8eb90-133">Build the project.</span></span>

<span data-ttu-id="8eb90-134">A saída resultante terá um arquivo `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` e `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="8eb90-135">Registrar o host COM para COM</span><span class="sxs-lookup"><span data-stu-id="8eb90-135">Register the COM host for COM</span></span>

<span data-ttu-id="8eb90-136">Abra um prompt de comandos com privilégios elevados e execute `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="8eb90-137">Isso registrará todos os seus objetos .NET expostos com o COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="8eb90-138">Habilitar o COM RegFree</span><span class="sxs-lookup"><span data-stu-id="8eb90-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="8eb90-139">Abra o arquivo de projeto `.csproj` e adicione `<EnableRegFreeCom>true</EnableRegFreeCom>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="8eb90-140">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="8eb90-140">Build the project.</span></span>

<span data-ttu-id="8eb90-141">A saída resultante agora também terá um arquivo `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="8eb90-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="8eb90-142">Esse arquivo é o manifesto lado a lado para uso com o COM Sem Registro.</span><span class="sxs-lookup"><span data-stu-id="8eb90-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="8eb90-143">Amostra</span><span class="sxs-lookup"><span data-stu-id="8eb90-143">Sample</span></span>

<span data-ttu-id="8eb90-144">Há um [exemplo de servidor COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) totalmente funcional no repositório dotnet/de exemplos no GitHub.</span><span class="sxs-lookup"><span data-stu-id="8eb90-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="8eb90-145">Observações adicionais</span><span class="sxs-lookup"><span data-stu-id="8eb90-145">Additional notes</span></span>

<span data-ttu-id="8eb90-146">Ao contrário do .NET Framework, não há suporte no .NET Core para gerar um TLB (Biblioteca de Tipos) COM com base em um assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8eb90-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="8eb90-147">A orientação é escrever manualmente um arquivo IDL ou um cabeçalho C/C++ para as declarações nativas das interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="8eb90-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="8eb90-148">[As implantações independentes](../deploying/index.md#publish-self-contained) de componentes COM não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="8eb90-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="8eb90-149">Apenas [implantações dependentes de tempo](../deploying/index.md#publish-runtime-dependent) de execução de componentes COM são suportadas.</span><span class="sxs-lookup"><span data-stu-id="8eb90-149">Only [runtime-dependent deployments](../deploying/index.md#publish-runtime-dependent) of COM components are supported.</span></span>

<span data-ttu-id="8eb90-150">Além disso, carregar o .NET Framework e o .NET Core no mesmo processo tem limitações diagnósticas.</span><span class="sxs-lookup"><span data-stu-id="8eb90-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="8eb90-151">A principal limitação é a depuração de componentes gerenciados, pois não é possível depurar tanto o .NET Framework quanto o .NET Core ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8eb90-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="8eb90-152">Além disso, as duas instâncias de tempo de execução não compartilham assembléias gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="8eb90-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="8eb90-153">Isso significa que não é possível compartilhar tipos reais .NET nos dois tempos de execução e, em vez disso, todas as interações devem ser restritas aos contratos de interface COM expostos.</span><span class="sxs-lookup"><span data-stu-id="8eb90-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
