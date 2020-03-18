---
title: -target:library (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606400"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="06947-102">-target:library (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="06947-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="06947-103">A opção **-target:library** faz com que o compilador crie uma DLL (biblioteca de vínculo dinâmico) em vez de um EXE (arquivo executável).</span><span class="sxs-lookup"><span data-stu-id="06947-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06947-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06947-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="06947-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="06947-105">Remarks</span></span>  
 <span data-ttu-id="06947-106">A DLL será criada com a extensão .dll.</span><span class="sxs-lookup"><span data-stu-id="06947-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="06947-107">A menos que seja especificado de outra forma com a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usa o nome do primeiro arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="06947-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="06947-108">Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou **-target:module** são usados para criar o arquivo .dll.</span><span class="sxs-lookup"><span data-stu-id="06947-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="06947-109">Ao criar um arquivo .dll, um método [Main](../../programming-guide/main-and-command-args/index.md) não é necessário.</span><span class="sxs-lookup"><span data-stu-id="06947-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="06947-110">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="06947-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="06947-111">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="06947-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="06947-112">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="06947-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="06947-113">Modifique a propriedade **Tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="06947-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="06947-114">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="06947-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06947-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06947-115">Example</span></span>  
 <span data-ttu-id="06947-116">Compile `in.cs`, criando `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="06947-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="06947-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="06947-117">See also</span></span>

- [<span data-ttu-id="06947-118">-destino (C# Opções de compilador)</span><span class="sxs-lookup"><span data-stu-id="06947-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="06947-119">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="06947-119">C# Compiler Options</span></span>](./index.md)
