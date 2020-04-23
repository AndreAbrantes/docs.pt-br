---
title: Assemblies de vários arquivos
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 2a70e45d50763cf99c55cf08600c3c816b4043b7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644214"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="a044c-102">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="a044c-102">Multifile assemblies</span></span>

<span data-ttu-id="a044c-103">Você pode criar assemblies de multiarquivos direcionados ao .NET Framework usando compiladores de linha de comando ou o Visual Studio com Visual C++.</span><span class="sxs-lookup"><span data-stu-id="a044c-103">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="a044c-104">Um arquivo no assembly deve conter o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="a044c-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="a044c-105">Um assembly que inicia um aplicativo também deve conter um ponto de entrada, como um `Main` método `WinMain` ou.</span><span class="sxs-lookup"><span data-stu-id="a044c-105">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="a044c-106">Por exemplo, suponha que você tenha um aplicativo que contenha dois módulos de código, *Client.cs* e *Stringer.cs*.</span><span class="sxs-lookup"><span data-stu-id="a044c-106">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="a044c-107">*Stringer.cs* cria o `myStringer` namespace que é referenciado pelo código em *Client.cs*.</span><span class="sxs-lookup"><span data-stu-id="a044c-107">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="a044c-108">*Client.cs* contém o `Main` método, que é o ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a044c-108">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="a044c-109">Neste exemplo, você compila os dois módulos de código e cria um terceiro arquivo que contém o manifesto do assembly, que inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a044c-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="a044c-110">O manifesto do assembly faz referência aos módulos *cliente* e *Stringer* .</span><span class="sxs-lookup"><span data-stu-id="a044c-110">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="a044c-111">Os assemblies de vários arquivos podem ter apenas um ponto de entrada, mesmo que o assembly tenha vários módulos de código.</span><span class="sxs-lookup"><span data-stu-id="a044c-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="a044c-112">Existem vários motivos que levam você a querer criar um assembly de vários arquivos:</span><span class="sxs-lookup"><span data-stu-id="a044c-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="a044c-113">Para combinar módulos escritos em linguagens diferentes.</span><span class="sxs-lookup"><span data-stu-id="a044c-113">To combine modules written in different languages.</span></span> <span data-ttu-id="a044c-114">Essa é a razão mais comum para a criação de um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="a044c-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="a044c-115">Para otimizar o download de um aplicativo colocando tipos raramente usados em um módulo que é baixado apenas quando necessário.</span><span class="sxs-lookup"><span data-stu-id="a044c-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a044c-116">Se você estiver criando aplicativos que serão baixados usando a marca `<object>` com o Microsoft Internet Explorer, é importante criar assemblies de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="a044c-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="a044c-117">Nesse cenário, você cria um arquivo separado do seus módulos de código que contenha somente o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="a044c-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="a044c-118">O Internet Explorer baixa o manifesto do assembly primeiro e, em seguida, cria threads de trabalho para baixar quaisquer módulos adicionais ou assemblies necessários.</span><span class="sxs-lookup"><span data-stu-id="a044c-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="a044c-119">Enquanto o arquivo que contém o manifesto do assembly estiver sendo baixado, o Internet Explorer não responderá à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a044c-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="a044c-120">Quanto menor o arquivo que contém o manifesto do assembly, menos tempo o Internet Explorer ficará sem responder.</span><span class="sxs-lookup"><span data-stu-id="a044c-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="a044c-121">Para combinar módulos de código escritos por vários desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="a044c-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="a044c-122">Embora cada desenvolvedor possa compilar cada módulo de código em um assembly, isso pode forçar alguns tipos a serem expostos publicamente, que não o seriam se todos os módulos fossem colocados em um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="a044c-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="a044c-123">Depois de criar o assembly, você pode assinar o arquivo que contém o manifesto do assembly e, portanto, o assembly, ou pode dar ao arquivo e ao assembly um nome forte e colocá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="a044c-123">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="a044c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a044c-124">See also</span></span>

- [<span data-ttu-id="a044c-125">Como compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="a044c-125">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="a044c-126">Programar com assemblies</span><span class="sxs-lookup"><span data-stu-id="a044c-126">Program with assemblies</span></span>](../../standard/assembly/index.md)
