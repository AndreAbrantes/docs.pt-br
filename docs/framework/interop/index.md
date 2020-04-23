---
title: Interoperação com código não gerenciado
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457960"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="36333-102">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="36333-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="36333-103">O .NET Framework promove a interação com componentes COM, serviços COM+, bibliotecas de tipos externas e muitos serviços do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="36333-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="36333-104">Tipos de dados, assinaturas de método e mecanismos de tratamento de erros variam entre modelos de objetos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="36333-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="36333-105">Para simplificar a interoperação entre componentes do .NET Framework e o código não gerenciado e para facilitar o caminho de migração, o Common Language Runtime oculta de clientes e servidores as diferenças entre esses modelos de objeto.</span><span class="sxs-lookup"><span data-stu-id="36333-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="36333-106">O código que é executado sob o controle de runtime é chamado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="36333-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="36333-107">Em contraste, o código executado fora do runtime é chamado de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="36333-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="36333-108">Componentes COM, interfaces ActiveX e funções da API do Windows são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="36333-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="36333-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="36333-109">In this section</span></span>

[<span data-ttu-id="36333-110">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36333-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="36333-111">Descreve como usar componentes COM de aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36333-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="36333-112">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="36333-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="36333-113">Descreve como usar componentes do .NET Framework de aplicativos COM.</span><span class="sxs-lookup"><span data-stu-id="36333-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="36333-114">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="36333-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="36333-115">Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="36333-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="36333-116">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="36333-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="36333-117">Descreve o marshaling para invocação de plataforma e interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="36333-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="36333-118">Como mapear HRESULTs e exceções</span><span class="sxs-lookup"><span data-stu-id="36333-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="36333-119">Descreve o mapeamento entre exceções e HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="36333-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="36333-120">Equivalência de tipos e tipos de interoperabilidade inseridos</span><span class="sxs-lookup"><span data-stu-id="36333-120">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="36333-121">Descreve como as informações de tipo para tipos COM são inseridas em assemblies e como o Common Language Runtime determina a equivalência de tipos COM inseridos.</span><span class="sxs-lookup"><span data-stu-id="36333-121">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="36333-122">Como gerar assemblies de interoperabilidade primários usando Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="36333-122">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="36333-123">Descreve como gerar assemblies de interoperabilidade primários usando *Tlbimp.exe* (Importador da Biblioteca de Tipos).</span><span class="sxs-lookup"><span data-stu-id="36333-123">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="36333-124">Como registrar assemblies de interoperabilidade primários</span><span class="sxs-lookup"><span data-stu-id="36333-124">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="36333-125">Descreve como registrar os assemblies de interoperabilidade primários antes de referenciá-los em seus projetos.</span><span class="sxs-lookup"><span data-stu-id="36333-125">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="36333-126">Interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="36333-126">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="36333-127">Descreve como a interoperabilidade COM pode ativar componentes sem usar o Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="36333-127">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="36333-128">Como configurar componentes do COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="36333-128">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="36333-129">Descreve como criar um manifesto do aplicativo e como criar e inserir um manifesto do componente.</span><span class="sxs-lookup"><span data-stu-id="36333-129">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="36333-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="36333-130">Related sections</span></span>

[<span data-ttu-id="36333-131">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="36333-131">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="36333-132">Descreve os wrappers fornecidos pela interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="36333-132">Describes the wrappers provided by COM interop.</span></span>
