---
title: -target:winmdobj (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204486"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="a5161-102">-target:winmdobj (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="a5161-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="a5161-103">Se você usar a opção do compilador **-target:winmdobj**, o compilador criará um arquivo .winmdobj intermediário que pode ser convertido em um arquivo binário do Windows Runtime (.winmd).</span><span class="sxs-lookup"><span data-stu-id="a5161-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="a5161-104">O arquivo .winmd pode, então, ser consumido por programas JavaScript e C++, bem como programas de linguagem gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a5161-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5161-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5161-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="a5161-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5161-106">Remarks</span></span>  
 <span data-ttu-id="a5161-107">A configuração **winmdobj** indica para o compilador que um módulo intermediário é necessário.</span><span class="sxs-lookup"><span data-stu-id="a5161-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="a5161-108">Em resposta, o Visual Studio compila a biblioteca de classes do C# como um arquivo .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="a5161-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="a5161-109">O arquivo .winmdobj pode, então, ser alimentado por meio da ferramenta de exportação <xref:Microsoft.Build.Tasks.WinMDExp> para produzir um arquivo de metadados do Windows (.winmd).</span><span class="sxs-lookup"><span data-stu-id="a5161-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="a5161-110">O arquivo .winmd contém o código da biblioteca original e os metadados do WinMD que são usados pelo JavaScript ou C++ e pelo Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="a5161-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="a5161-111">A saída de um arquivo que é compilado usando a opção do compilador **-target:winmdobj** foi criada para ser usada apenas como entrada para a ferramenta de exportação WimMDExp. O arquivo .winmdobj em si não é referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="a5161-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="a5161-112">A menos que você use a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do primeiro arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5161-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="a5161-113">Um método [Main](../../programming-guide/main-and-command-args/index.md) não é necessário.</span><span class="sxs-lookup"><span data-stu-id="a5161-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="a5161-114">Se você especificar a opção -target:winmdobj em um prompt de comando, todos os arquivos até a próxima opção **-out** ou [-target:module](./target-module-compiler-option.md) serão usados para criar o programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5161-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="a5161-115">Para definir esta opção de compilador no IDE do Visual Studio para um aplicativo da Windows Store</span><span class="sxs-lookup"><span data-stu-id="a5161-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="a5161-116">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a5161-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="a5161-117">Escolha a guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a5161-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="a5161-118">Na lista **Tipo de saída**, escolha **Arquivo WinMD**.</span><span class="sxs-lookup"><span data-stu-id="a5161-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="a5161-119">A opção **Arquivo WinMD** está disponível apenas para modelos de aplicativos do Windows 8.x Store.</span><span class="sxs-lookup"><span data-stu-id="a5161-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="a5161-120">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5161-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5161-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5161-121">Example</span></span>  
 <span data-ttu-id="a5161-122">O comando a seguir compila `filename.cs` em um arquivo .winmdobj intermediário.</span><span class="sxs-lookup"><span data-stu-id="a5161-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5161-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5161-123">See also</span></span>

- [<span data-ttu-id="a5161-124">-destino (C# Opções de compilador)</span><span class="sxs-lookup"><span data-stu-id="a5161-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="a5161-125">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="a5161-125">C# Compiler Options</span></span>](./index.md)
