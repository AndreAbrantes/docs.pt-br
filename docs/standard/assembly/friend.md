---
title: Assemblies amigáveis
description: Um assembly Friend é um assembly .NET que pode acessar os tipos e membros internos (C#) ou Friend (Visual Basic) de outro assembly.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378927"
---
# <a name="friend-assemblies"></a><span data-ttu-id="b4e42-103">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="b4e42-103">Friend assemblies</span></span>

<span data-ttu-id="b4e42-104">Um *assembly Friend* é um assembly que pode acessar os tipos e membros [internos](../../csharp/language-reference/keywords/internal.md) (C#) ou [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="b4e42-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="b4e42-105">Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="b4e42-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="b4e42-106">Isso é especialmente conveniente nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="b4e42-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="b4e42-107">Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4e42-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="b4e42-108">Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4e42-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4e42-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4e42-109">Remarks</span></span>

<span data-ttu-id="b4e42-110">Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="b4e42-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="b4e42-111">O exemplo a seguir usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo no *assembly A* e especifica o assembly *AssemblyB* como um assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="b4e42-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="b4e42-112">Isso dá ao assembly *AssemblyB* acesso a todos os tipos e membros no *assembly A* que são marcados como `internal` em C# ou `Friend` em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4e42-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="b4e42-113">Quando você compila um assembly como *AssemblyB* que acessará tipos internos ou membros internos de outro assembly, como *assembly a*, você deve especificar explicitamente o nome do arquivo de saída (*. exe* ou *. dll*) usando a opção de compilador **-out** .</span><span class="sxs-lookup"><span data-stu-id="b4e42-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="b4e42-114">Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas.</span><span class="sxs-lookup"><span data-stu-id="b4e42-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="b4e42-115">Para obter mais informações, consulte [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="b4e42-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

<span data-ttu-id="b4e42-116">Somente os assemblies que você especifica explicitamente como amigos podem acessar `internal` os tipos e membros do (C#) ou `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b4e42-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="b4e42-117">Por exemplo, se *AssemblyB* for um amigo do *assembly a e o* *assembly c* fizer referência a *AssemblyB*, o *assembly c* não terá acesso aos `internal` tipos (C#) ou `Friend` (Visual Basic) no *assembly a*.</span><span class="sxs-lookup"><span data-stu-id="b4e42-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="b4e42-118">O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b4e42-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="b4e42-119">Se o *assembly A* declarar *AssemblyB* como um assembly Friend, as regras de validação serão as seguintes:</span><span class="sxs-lookup"><span data-stu-id="b4e42-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="b4e42-120">Se *o assembly A tiver um* nome forte, *AssemblyB* também deverá ter um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b4e42-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="b4e42-121">O nome do assembly Friend que é passado para o atributo deve consistir no nome do assembly e na chave pública da chave de nome forte que é usada para assinar *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="b4e42-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="b4e42-122">O nome do assembly Friend que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo não pode ser o nome forte de *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="b4e42-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="b4e42-123">Não inclua a versão do assembly, a cultura, a arquitetura ou o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="b4e42-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="b4e42-124">Se o *assembly A* não for de nome forte, o nome do assembly Friend deverá consistir apenas no nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="b4e42-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="b4e42-125">Para obter mais informações, consulte [como: criar assemblies Friend não assinados](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="b4e42-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="b4e42-126">Se *AssemblyB* for de nome forte, você deverá especificar a chave de nome forte para *AssemblyB* usando a configuração do projeto ou a opção do compilador de linha de comando `/keyfile` .</span><span class="sxs-lookup"><span data-stu-id="b4e42-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="b4e42-127">Para obter mais informações, consulte [como criar assemblies Friend assinados](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="b4e42-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="b4e42-128">A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="b4e42-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="b4e42-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="b4e42-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="b4e42-130">Se houver centenas de tipos no *assembly a* que você deseja compartilhar com *AssemblyB*, você precisará adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles.</span><span class="sxs-lookup"><span data-stu-id="b4e42-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="b4e42-131">Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.</span><span class="sxs-lookup"><span data-stu-id="b4e42-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="b4e42-132">Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos.</span><span class="sxs-lookup"><span data-stu-id="b4e42-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="b4e42-133">Se você usar um assembly Friend, os tipos compartilhados serão declarados como `internal` (C#) ou `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b4e42-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="b4e42-134">Para obter informações sobre como acessar `internal` os tipos e métodos de um assembly (C#) ou `Friend` (Visual Basic) de um arquivo de módulo (um arquivo com a extensão *. netmodule* ), consulte [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="b4e42-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4e42-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4e42-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="b4e42-136">Como: criar assemblies Friend não assinados</span><span class="sxs-lookup"><span data-stu-id="b4e42-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="b4e42-137">Como criar assemblies Friend assinados</span><span class="sxs-lookup"><span data-stu-id="b4e42-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="b4e42-138">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="b4e42-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="b4e42-139">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="b4e42-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b4e42-140">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e42-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
