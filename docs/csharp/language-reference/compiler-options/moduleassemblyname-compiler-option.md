---
description: -moduleassemblyname (opção do compilador C#)
title: -moduleassemblyname (opção do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194083"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="89d58-103">-moduleassemblyname (opção do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="89d58-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="89d58-104">Especifica um assembly cujos tipos não públicos podem ser acessados por um .netmodule.</span><span class="sxs-lookup"><span data-stu-id="89d58-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d58-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89d58-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="89d58-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="89d58-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="89d58-107">O nome do assembly cujos tipos não públicos podem ser acessados por um .netmodule.</span><span class="sxs-lookup"><span data-stu-id="89d58-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89d58-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="89d58-108">Remarks</span></span>  

 <span data-ttu-id="89d58-109">O **-moduleassemblyname** deverá ser usado ao compilar um .netmodule e quando as condições a seguir forem true:</span><span class="sxs-lookup"><span data-stu-id="89d58-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="89d58-110">O .netmodule precisa acessar tipos não públicos em um assembly existente.</span><span class="sxs-lookup"><span data-stu-id="89d58-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="89d58-111">Você sabe o nome do assembly no qual o .netmodule será compilado.</span><span class="sxs-lookup"><span data-stu-id="89d58-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="89d58-112">O assembly existente concedeu acesso de assembly amigável ao assembly no qual o .netmodule será compilado.</span><span class="sxs-lookup"><span data-stu-id="89d58-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="89d58-113">Para obter mais informações sobre a compilação de um .netmodule, consulte [-target:module (Opções do compilador do C#)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="89d58-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="89d58-114">Para obter mais informações sobre assemblies amigos, consulte [Assemblies Amigáveis](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="89d58-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="89d58-115">Essa opção não está disponível de dentro do ambiente de desenvolvimento; ela só está disponível quando se compila na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="89d58-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="89d58-116">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="89d58-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89d58-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89d58-117">Example</span></span>  

 <span data-ttu-id="89d58-118">Este exemplo compila um assembly com um tipo privado que concede acesso de assembly amigável a um assembly denominado csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="89d58-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="89d58-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89d58-119">Example</span></span>  

 <span data-ttu-id="89d58-120">Este exemplo compila um .netmodule que acessa um tipo não público no assembly moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="89d58-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="89d58-121">Sabendo que esse. netmodule será criado em um assembly chamado csman_an_assembly, podemos especificar **-moduleassemblyname**, permitindo que o. netmodule acesse tipos não públicos em um assembly que tenha concedido acesso de assembly friend a csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="89d58-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="89d58-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89d58-122">Example</span></span>  

 <span data-ttu-id="89d58-123">Este exemplo de código compila o assembly csman_an_assembly, referenciando o assembly compilado anteriormente e o .netmodule.</span><span class="sxs-lookup"><span data-stu-id="89d58-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="89d58-124">**An_Internal_Class.Test foi chamado**</span><span class="sxs-lookup"><span data-stu-id="89d58-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="89d58-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="89d58-125">See also</span></span>

- [<span data-ttu-id="89d58-126">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="89d58-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="89d58-127">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="89d58-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
