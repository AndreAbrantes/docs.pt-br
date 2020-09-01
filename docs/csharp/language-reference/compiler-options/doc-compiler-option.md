---
description: -doc (opções do compilador C#)
title: -doc (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: 366bad1029904b3571be0a76d827ff0213d776bb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125742"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="3bd7d-103">-doc (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3bd7d-103">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="3bd7d-104">A opção **-doc** permite colocar comentários de documentação em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd7d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bd7d-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3bd7d-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3bd7d-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="3bd7d-107">O arquivo de saída para XML, que é populado com os comentários nos arquivos de código-fonte da compilação.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bd7d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bd7d-108">Remarks</span></span>  
 <span data-ttu-id="3bd7d-109">Nos arquivos de código-fonte, os comentários de documentação que precedem o seguinte podem ser processados e adicionados ao arquivo XML:</span><span class="sxs-lookup"><span data-stu-id="3bd7d-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="3bd7d-110">Tipos definidos pelo usuário, como [classe](../keywords/class.md), [delegado](../builtin-types/reference-types.md#the-delegate-type) ou [interface](../keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="3bd7d-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="3bd7d-111">Membros como um campo, [evento](../keywords/event.md), [propriedade](../../programming-guide/classes-and-structs/using-properties.md) ou método</span><span class="sxs-lookup"><span data-stu-id="3bd7d-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="3bd7d-112">O arquivo de código-fonte que contém Main é gerado primeiro no XML.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="3bd7d-113">Para usar o arquivo .xml gerado para uso com o recurso [IntelliSense](/visualstudio/ide/using-intellisense), deixe o nome do arquivo .xml igual ao do assembly a que você deseja dar suporte e, em seguida, verifique se o arquivo .xml está no mesmo diretório que o assembly.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="3bd7d-114">Sendo assim, quando o assembly for referenciado no projeto do Visual Studio, o arquivo .xml também será encontrado.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="3bd7d-115">Consulte [Fornecendo comentários de código](/visualstudio/ide/reference/generate-xml-documentation-comments) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="3bd7d-116">A menos que você compile com o [módulo-target:](./target-module-compiler-option.md), conterá `file` \<assembly> \</assembly> marcas especificando o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bd7d-117">A opção -doc se aplica a todos os arquivos de entrada ou, se definida nas Configurações do Projeto, todos os arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="3bd7d-118">Para desabilitar avisos relacionados aos comentários de documentação para um arquivo ou uma seção específica do código, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="3bd7d-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="3bd7d-119">Consulte [Marcas recomendadas para comentários de documentação](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) para ver maneiras de gerar a documentação dos comentários em seu código.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3bd7d-120">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3bd7d-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3bd7d-121">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3bd7d-122">Clique na guia **Build**.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="3bd7d-123">Modifique a propriedade **Arquivo de documentação XML**.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="3bd7d-124">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bd7d-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd7d-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="3bd7d-125">See also</span></span>

- [<span data-ttu-id="3bd7d-126">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="3bd7d-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3bd7d-127">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="3bd7d-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
