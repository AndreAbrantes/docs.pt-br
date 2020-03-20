---
title: Lc.exe (Compilador de Licença)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180406"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="470f2-102">Lc.exe (Compilador de Licença)</span><span class="sxs-lookup"><span data-stu-id="470f2-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="470f2-103">O Compilador de Licença lê arquivos de texto que contêm informações de licenciamento e produz um arquivo binário que pode ser inserido em um executável do Common Language Runtime como um recurso.</span><span class="sxs-lookup"><span data-stu-id="470f2-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="470f2-104">Um arquivo de texto .licx é gerado automaticamente ou atualizado pelo Designer de Formulários do Windows sempre que um controle licenciado é adicionado ao formulário.</span><span class="sxs-lookup"><span data-stu-id="470f2-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="470f2-105">Como parte da compilação, o sistema do projeto transformará o arquivo de texto .licx em um recurso binário .licenses que dá suporte ao licenciamento de controle do .NET.</span><span class="sxs-lookup"><span data-stu-id="470f2-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="470f2-106">Em seguida, o recurso binário será inserido na saída do projeto.</span><span class="sxs-lookup"><span data-stu-id="470f2-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="470f2-107">A compilação cruzada entre 32 e 64 bits não é compatível quando você usa o Compilador de Licença ao compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="470f2-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="470f2-108">Isso porque o Compilador de Licença precisa carregar assemblies, e o carregamento de assemblies 64 bits de um aplicativo 32 bits não é permitido, e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="470f2-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="470f2-109">Nesse caso, use o Compilador de Licença na linha de comando para compilar manualmente a licença e especificar a arquitetura correspondente.</span><span class="sxs-lookup"><span data-stu-id="470f2-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="470f2-110">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="470f2-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="470f2-111">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="470f2-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="470f2-112">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="470f2-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="470f2-113">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="470f2-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="470f2-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="470f2-114">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="470f2-115">Opção</span><span class="sxs-lookup"><span data-stu-id="470f2-115">Option</span></span>|<span data-ttu-id="470f2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="470f2-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="470f2-117">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="470f2-117">**/complist:** *filename*</span></span>|<span data-ttu-id="470f2-118">Especifica o nome de um arquivo que contém a lista de componentes licenciados que serão incluídos no arquivo .licenses.</span><span class="sxs-lookup"><span data-stu-id="470f2-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="470f2-119">Cada componente é referenciado usando-se seu nome completo com apenas um componente por linha.</span><span class="sxs-lookup"><span data-stu-id="470f2-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="470f2-120">Os usuários de linha de comando podem especificar um arquivo separado para cada formulário no projeto.</span><span class="sxs-lookup"><span data-stu-id="470f2-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="470f2-121">Lc.exe aceita vários arquivos de entrada e produz um único arquivo .licenses.</span><span class="sxs-lookup"><span data-stu-id="470f2-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="470f2-122">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="470f2-122">**/h**[**elp**]</span></span>|<span data-ttu-id="470f2-123">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="470f2-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="470f2-124">**/i:** *module*</span><span class="sxs-lookup"><span data-stu-id="470f2-124">**/i:** *module*</span></span>|<span data-ttu-id="470f2-125">Especifica os módulos que contêm os componentes listados no arquivo **/complist**.</span><span class="sxs-lookup"><span data-stu-id="470f2-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="470f2-126">Para especificar mais de um módulo, use vários sinalizadores **/i**.</span><span class="sxs-lookup"><span data-stu-id="470f2-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="470f2-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="470f2-127">**/nologo**</span></span>|<span data-ttu-id="470f2-128">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="470f2-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="470f2-129">**/outdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="470f2-129">**/outdir:** *path*</span></span>|<span data-ttu-id="470f2-130">Especifica o diretório no qual o arquivo .licenses de saída deve ser colocado.</span><span class="sxs-lookup"><span data-stu-id="470f2-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="470f2-131">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="470f2-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="470f2-132">Especifica o executável para o qual o arquivo .licenses está sendo gerado.</span><span class="sxs-lookup"><span data-stu-id="470f2-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="470f2-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="470f2-133">**/v**</span></span>|<span data-ttu-id="470f2-134">Especifica o modo detalhado; exibe informações de andamento da compilação.</span><span class="sxs-lookup"><span data-stu-id="470f2-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="470f2-135">\**@\*\*\*arquivo*</span><span class="sxs-lookup"><span data-stu-id="470f2-135">**@** *file*</span></span>|<span data-ttu-id="470f2-136">Especifica o arquivo de resposta (.rsp).</span><span class="sxs-lookup"><span data-stu-id="470f2-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="470f2-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="470f2-137">**/?**</span></span>|<span data-ttu-id="470f2-138">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="470f2-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="470f2-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="470f2-139">Example</span></span>  
  
1. <span data-ttu-id="470f2-140">Se estiver usando um controle licenciado `MyCompany.Samples.LicControl1` contido em `Samples.DLL` em um aplicativo chamado `HostApp.exe`*,* você poderá criar `HostAppLic.txt` que contém o seguinte.</span><span class="sxs-lookup"><span data-stu-id="470f2-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="470f2-141">Crie o arquivo .licenses chamado `HostApp.exe.licenses` usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="470f2-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="470f2-142">Compile `HostApp.exe` incluindo o arquivo .licenses como um recurso.</span><span class="sxs-lookup"><span data-stu-id="470f2-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="470f2-143">Se estivesse compilando um aplicativo do C#, você usaria o comando a seguir para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="470f2-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="470f2-144">O comando a seguir compila `myApp.licenses` com base nas listas de componentes licenciados especificados por `hostapplic.txt`, `hostapplic2.txt` e `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="470f2-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="470f2-145">O argumento `modulesList` especifica os módulos que contêm os componentes licenciados.</span><span class="sxs-lookup"><span data-stu-id="470f2-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="470f2-146">Exemplo de arquivo de resposta</span><span class="sxs-lookup"><span data-stu-id="470f2-146">Response File Example</span></span>  
 <span data-ttu-id="470f2-147">A listagem a seguir mostra um exemplo de um arquivo de resposta, `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="470f2-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="470f2-148">Para saber mais sobre arquivos de resposta, confira [Arquivos de resposta](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="470f2-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="470f2-149">A linha de comando a seguir usa o arquivo `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="470f2-149">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="470f2-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="470f2-150">See also</span></span>

- [<span data-ttu-id="470f2-151">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="470f2-151">Tools</span></span>](index.md)
- [<span data-ttu-id="470f2-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="470f2-152">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="470f2-153">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="470f2-153">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
