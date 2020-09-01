---
description: -reference (opções do compilador do C#)
title: -reference (opções do compilador do C#)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 7b84953f85545c0400c7136c258849f259e8b48a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124793"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="e92b7-103">-reference (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="e92b7-103">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="e92b7-104">A opção **-reference** opção faz com que o compilador importe informações de tipo [public](../keywords/public.md) no arquivo especificado para o projeto atual, permitindo que você referencie metadados dos arquivos do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="e92b7-104">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92b7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e92b7-105">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e92b7-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e92b7-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e92b7-107">O nome de um arquivo que contém um manifesto de assembly.</span><span class="sxs-lookup"><span data-stu-id="e92b7-107">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="e92b7-108">Para importar mais de um arquivo, inclua uma opção **-reference** separada para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="e92b7-108">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="e92b7-109">Um identificador C# válido que representará um namespace raiz que conterá todos os namespaces no assembly.</span><span class="sxs-lookup"><span data-stu-id="e92b7-109">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e92b7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e92b7-110">Remarks</span></span>  
 <span data-ttu-id="e92b7-111">Para importar de mais de um arquivo, inclua uma opção **-reference** para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="e92b7-111">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="e92b7-112">Os arquivos que você importa devem conter um manifesto; o arquivo de saída deve ter sido compilado com uma das opções [-target](./target-compiler-option.md) diferentes de [-target:module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e92b7-112">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e92b7-113">**-r** é a forma abreviada de **-reference**.</span><span class="sxs-lookup"><span data-stu-id="e92b7-113">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="e92b7-114">Use [-addmodule](./addmodule-compiler-option.md) para importar metadados de um arquivo de saída que não contém um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="e92b7-114">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="e92b7-115">Se você referenciar um assembly (Assembly A) que referencia outro assembly (Assembly B), será necessário referenciar o Assembly B se:</span><span class="sxs-lookup"><span data-stu-id="e92b7-115">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="e92b7-116">o tipo A que você usar do Assembly A herdar de um tipo ou implementar uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="e92b7-116">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="e92b7-117">Você invoca um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="e92b7-117">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="e92b7-118">Use [-lib](./lib-compiler-option.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizadas.</span><span class="sxs-lookup"><span data-stu-id="e92b7-118">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="e92b7-119">O tópico **-lib** também aborda os diretórios nos quais o compilador pesquisa assemblies.</span><span class="sxs-lookup"><span data-stu-id="e92b7-119">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="e92b7-120">Para que o compilador reconheça um tipo em um assembly e não um módulo, ele precisa ser forçado a resolver o tipo, que você pode fazer definindo uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="e92b7-120">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="e92b7-121">Há outras maneiras de resolver nomes de tipo em um assembly para o compilador: por exemplo, se você herda de um tipo em um assembly, o nome do tipo será reconhecido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="e92b7-121">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="e92b7-122">Às vezes, é necessário referenciar duas versões diferentes do mesmo componente de dentro de um assembly.</span><span class="sxs-lookup"><span data-stu-id="e92b7-122">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="e92b7-123">Para fazer isso, use a subopção de alias na opção **-reference** para cada arquivo, a fim de diferenciar entre os dois arquivos.</span><span class="sxs-lookup"><span data-stu-id="e92b7-123">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="e92b7-124">Esse alias será usado como um qualificador do nome do componente e será resolvido para o componente em um dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="e92b7-124">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="e92b7-125">O arquivo de resposta csc (.rsp), que referencia assemblies .NET Framework usados com frequência, é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="e92b7-125">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="e92b7-126">Use [-noconfig](./noconfig-compiler-option.md) se você não quiser que o compilador use csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="e92b7-126">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e92b7-127">No Visual Studio, use a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e92b7-127">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="e92b7-128">Para obter mais informações, consulte [Como adicionar ou remover referências usando o Gerenciador de Referências](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="e92b7-128">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="e92b7-129">Para garantir o comportamento equivalente entre adicionar referências usando `-reference` e usando a caixa de diálogo **Adicionar Referência**, defina a propriedade **Inserir Tipos de Interoperabilidade** como **False** para o assembly que você está adicionando.</span><span class="sxs-lookup"><span data-stu-id="e92b7-129">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="e92b7-130">**True** é o valor padrão para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e92b7-130">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e92b7-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e92b7-131">Example</span></span>  
 <span data-ttu-id="e92b7-132">Este exemplo mostra como usar o recurso [alias externo](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="e92b7-132">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="e92b7-133">Compile o arquivo de origem e importe os metadados de `grid.dll` e de `grid20.dll`, que foram compilados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e92b7-133">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="e92b7-134">As duas DLLs contêm versões separadas do mesmo componente e você usa dois **-reference** com opções de alias para compilar o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="e92b7-134">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="e92b7-135">As opções têm esta aparência:</span><span class="sxs-lookup"><span data-stu-id="e92b7-135">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="e92b7-136">Isso configura os aliases externos `GridV1` e `GridV2`, que você usa em seu programa por meio de uma instrução `extern`:</span><span class="sxs-lookup"><span data-stu-id="e92b7-136">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="e92b7-137">Quando isso for feito, será possível consultar o controle de grade de `grid.dll`, prefixando o nome do controle com `GridV1`, assim:</span><span class="sxs-lookup"><span data-stu-id="e92b7-137">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="e92b7-138">Além disso, é possível consultar o controle de grade de `grid20.dll`, prefixando o nome do controle com `GridV2`, assim:</span><span class="sxs-lookup"><span data-stu-id="e92b7-138">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="e92b7-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="e92b7-139">See also</span></span>

- [<span data-ttu-id="e92b7-140">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e92b7-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e92b7-141">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="e92b7-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
