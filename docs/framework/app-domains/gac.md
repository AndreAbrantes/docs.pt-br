---
title: Cache de assemblies global
description: Entenda o cache de assembly global, que é um cache de código de todo o computador em que o Common Language Runtime para .NET está instalado.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 57d18c01bd6261e8207d8ad3849a3a7da9a24b6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264602"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="887d7-103">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="887d7-103">Global Assembly Cache</span></span>

<span data-ttu-id="887d7-104">Cada computador em que o Common Language Runtime está instalado tem um cache de código em todo o computador chamado Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="887d7-105">O Cache de Assembly Global armazena assemblies projetados especificamente para serem compartilhados por vários aplicativos no computador.</span><span class="sxs-lookup"><span data-stu-id="887d7-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="887d7-106">Você deverá compartilhar assemblies instalando-os no Cache de Assembly Global somente quando precisar.</span><span class="sxs-lookup"><span data-stu-id="887d7-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="887d7-107">Como diretriz geral, mantenha as dependências de um assembly privadas e localize os assemblies no diretório de aplicativo, a menos que o compartilhamento de um assembly seja explicitamente obrigatório.</span><span class="sxs-lookup"><span data-stu-id="887d7-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="887d7-108">Além disso, não é necessário instalar assemblies no Cache de Assembly Global a fim de torná-los acessíveis para interoperabilidade COM ou código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="887d7-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="887d7-109">Há cenários em que você explicitamente não deseja instalar um assembly no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="887d7-110">Se você colocar um dos assemblies que compõem um aplicativo no Cache de Assembly Global, não poderá mais replicar nem instalar o aplicativo usando o comando **xcopy** para copiar o diretório de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="887d7-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="887d7-111">Você também deve mover o assembly no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="887d7-112">Há duas maneiras de implantar um assembly no Cache de Assembly Global:</span><span class="sxs-lookup"><span data-stu-id="887d7-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="887d7-113">Usar um instalador projetado para funcionar com o Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="887d7-114">Essa é a opção preferencial para instalar assemblies no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="887d7-115">Use uma ferramenta de desenvolvedor chamada [Cache de Assembly Global (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), fornecida pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="887d7-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="887d7-116">Em cenários de implantação, use o Windows Installer para instalar assemblies no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="887d7-117">Só use a ferramenta Global Assembly Cache em cenários de desenvolvimento, porque ela não fornece contagem de referência de assembly e outros recursos fornecidos durante o uso do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="887d7-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="887d7-118">A partir do .NET Framework 4, a localização padrão do Cache de Assembly Global é **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="887d7-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="887d7-119">Em versões anteriores do .NET Framework, o local padrão era **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="887d7-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="887d7-120">Os administradores geralmente protegem o diretório systemroot usando uma ACL (lista de controle de acesso) para controlar acesso de escrita e execução.</span><span class="sxs-lookup"><span data-stu-id="887d7-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="887d7-121">Como o Cache de Assembly Global é instalado em um subdiretório do diretório systemroot, ele herda a ACL desse diretório.</span><span class="sxs-lookup"><span data-stu-id="887d7-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="887d7-122">É recomendável que apenas usuários com privilégios de Administrador tenham permissão para excluir arquivos do Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="887d7-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="887d7-123">Assemblies implantados no Cache de Assembly Global devem ter um nome forte.</span><span class="sxs-lookup"><span data-stu-id="887d7-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="887d7-124">Quando um assembly é adicionado ao Cache de Assembly Global, são executadas verificações de integridade em todos os arquivos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="887d7-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="887d7-125">O cache executa essas verificações de integridade para garantir que um assembly não tenha sido adulterado, por exemplo, quando um arquivo é alterado, mas o manifesto não reflete a alteração.</span><span class="sxs-lookup"><span data-stu-id="887d7-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887d7-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="887d7-126">See also</span></span>

- [<span data-ttu-id="887d7-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="887d7-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="887d7-128">Trabalhando com assemblies e o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="887d7-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="887d7-129">Assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="887d7-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
