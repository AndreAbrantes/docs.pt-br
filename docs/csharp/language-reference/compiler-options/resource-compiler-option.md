---
description: -resource (opções do compilador C#)
title: -resource (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 963004820f56272b4f1b1d92ccc4d0a60493a4a0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128693"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="c8a8a-103">-resource (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c8a8a-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="c8a8a-104">Insere o recurso especificado no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a8a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8a8a-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8a8a-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c8a8a-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c8a8a-107">O arquivo de recurso do .NET Framework que você deseja inserir no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-107">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="c8a8a-108">`identifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="c8a8a-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="c8a8a-109">O nome lógico do recurso; o nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="c8a8a-110">O padrão é o nome do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="c8a8a-111">`accessibility-modifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="c8a8a-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="c8a8a-112">A acessibilidade do recurso: público ou privado.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="c8a8a-113">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8a8a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8a8a-114">Remarks</span></span>  
 <span data-ttu-id="c8a8a-115">Use [-linkresource](./linkresource-compiler-option.md) para vincular um recurso a um assembly e não adicionar o arquivo de recurso ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="c8a8a-116">Por padrão, recursos são públicos no assembly quando são criados usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="c8a8a-117">Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="c8a8a-118">Não é permitida nenhuma outra acessibilidade diferente de `public` ou `private`.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="c8a8a-119">Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-119">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="c8a8a-120">Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8a8a-121">Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="c8a8a-122">**-res** é a forma abreviada de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="c8a8a-123">A ordem dos recursos no arquivo de saída é determinada com base na ordem especificada na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8a8a-124">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8a8a-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c8a8a-125">Adicionar um arquivo de recurso ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="c8a8a-126">Selecione o arquivo que você deseja inserir no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="c8a8a-127">Selecione **Ação de Build** para o arquivo na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="c8a8a-128">Defina **Ação de Build** como **Recurso inserido**.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="c8a8a-129">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8a8a-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8a8a-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8a8a-130">Example</span></span>  
 <span data-ttu-id="c8a8a-131">Compile `in.cs` e anexe ao arquivo de recurso `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="c8a8a-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8a8a-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8a8a-132">See also</span></span>

- [<span data-ttu-id="c8a8a-133">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="c8a8a-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c8a8a-134">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="c8a8a-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
