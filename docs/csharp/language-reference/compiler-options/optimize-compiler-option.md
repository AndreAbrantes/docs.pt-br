---
description: -optimize (opções do compilador C#)
title: -optimize (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 1862794e4d823e38ce19780300a0b04f4e57dc44
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193979"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="a3158-103">-optimize (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="a3158-103">-optimize (C# Compiler Options)</span></span>

<span data-ttu-id="a3158-104">A opção **-optimize** habilita ou desabilita otimizações executadas pelo compilador para tornar o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="a3158-104">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3158-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3158-105">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3158-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3158-106">Remarks</span></span>  

 <span data-ttu-id="a3158-107">A **-optimize** também informa o Common Language Runtime para otimizar o código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3158-107">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="a3158-108">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="a3158-108">By default, optimizations are disabled.</span></span> <span data-ttu-id="a3158-109">Especifique **-optimize+** para habilitar otimizações.</span><span class="sxs-lookup"><span data-stu-id="a3158-109">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="a3158-110">Ao criar um módulo a ser usado por um assembly, use as mesmas configurações **-optimize** que as do assembly.</span><span class="sxs-lookup"><span data-stu-id="a3158-110">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="a3158-111">**-o** é a forma abreviada de **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="a3158-111">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="a3158-112">É possível combinar as opções **-optimize** e [-debug](./debug-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a3158-112">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a3158-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a3158-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a3158-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="a3158-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a3158-115">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a3158-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a3158-116">Modifique a propriedade **Otimizar código**.</span><span class="sxs-lookup"><span data-stu-id="a3158-116">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="a3158-117">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3158-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3158-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3158-118">Example</span></span>  

 <span data-ttu-id="a3158-119">Compile `t2.cs` e habilite as otimizações do compilador:</span><span class="sxs-lookup"><span data-stu-id="a3158-119">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3158-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3158-120">See also</span></span>

- [<span data-ttu-id="a3158-121">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="a3158-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a3158-122">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="a3158-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
