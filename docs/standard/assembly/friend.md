---
title: Assemblies amigáveis
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348172"
---
# <a name="friend-assemblies"></a>Assemblies amigáveis

Uma *reunião de amigos* é uma montagem que pode acessar os tipos e membros [internos](../../csharp/language-reference/keywords/internal.md) (C#) ou [Amigos](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) de outra assembléia. Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nos seguintes cenários:

- Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.

- Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.

## <a name="remarks"></a>Comentários

Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly. O exemplo a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> seguir usa o atributo na *Assembléia A* e especifica *assembly AssemblyB* como uma reunião de amigos. Isso dá ao *Assembly AssemblyB* acesso a todos os `internal` tipos e `Friend` membros na *Assembléia A* que estão marcados como em C# ou no Visual Basic.

> [!NOTE]
> Quando você compila um conjunto como *o AssemblyB* que acessará tipos internos ou membros internos de outro conjunto como *o Assembly A,* você deve especificar explicitamente o nome do arquivo de saída *(.exe* ou *.dll)* usando a opção **-out** compilador. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas. Para obter mais informações, consulte [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Somente assembléias que você especifica explicitamente `internal` como amigos `Friend` podem acessar (C#) ou (Visual Basic) tipos e membros. Por exemplo, se *o AssemblyB* é amigo da *Montagem A* e da Montagem *C* faz referência *ao AssemblyB,* *a Montagem C* não tem acesso aos `internal` tipos (C#) ou `Friend` (Visual Basic) na Montagem *A*.

O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Se *a Assembléia A* declarar *AssemblyB* como uma assembléia de amigos, as regras de validação serão as seguintes:

- Se *a Assembléia A* for forte, o *AssemblyB* também deve ser forte. O nome de reunião do amigo que é passado para o atributo deve consistir no nome da montagem e na chave pública da tecla de nome forte que é usada para assinar *AssemblyB*.

     O nome de reunião do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> amigo que é passado para o atributo não pode ser o nome forte de *AssemblyB*. Não inclua a versão de montagem, cultura, arquitetura ou token de chave pública.

- Se *a Assembléia A* não for forte, o nome da assembléia do amigo deve consistir apenas no nome da montagem. Para obter mais informações, consulte [Como: Criar assembléias de amigos não assinadas](create-unsigned-friend.md).

- Se *o AssemblyB* for forte, você deve especificar a tecla de nome `/keyfile` forte para *AssemblyB* usando a configuração do projeto ou a opção compilador de linha de comando. Para obter mais informações, consulte [Como: Criar assembléias de amigos assinados.](create-signed-friend.md)

 A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.

- Se há centenas de tipos na *Assembléia A* que você deseja compartilhar com *o AssemblyB,* você tem que adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles. Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.

- Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos. Se você usar uma montagem de amigos, `internal` os tipos compartilhados serão declarados como (C#) ou `Friend` (Visual Basic).

Para obter informações sobre como `internal` acessar os tipos `Friend` e métodos de montagem (C#) ou (Visual Basic) de um arquivo de módulo (um arquivo com a extensão *.netmodule),* consulte [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Confira também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Como: Criar assembléias de amigos não assinados](create-unsigned-friend.md)
- [Como: Criar assembléias de amigos assinados](create-signed-friend.md)
- [Assemblies no .NET](index.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
