---
title: -moduleassemblyname (opção do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173712"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (opção do compilador C#)
Especifica um assembly cujos tipos não públicos podem ser acessados por um .netmodule.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumentos  
 `assembly_name`  
 O nome do assembly cujos tipos não públicos podem ser acessados por um .netmodule.  
  
## <a name="remarks"></a>Comentários  
 O **-moduleassemblyname** deverá ser usado ao compilar um .netmodule e quando as condições a seguir forem true:  
  
- O .netmodule precisa acessar tipos não públicos em um assembly existente.  
  
- Você sabe o nome do assembly no qual o .netmodule será compilado.  
  
- O assembly existente concedeu acesso de assembly amigável ao assembly no qual o .netmodule será compilado.  
  
 Para obter mais informações sobre a compilação de um .netmodule, consulte [-target:module (Opções do compilador do C#)](./target-module-compiler-option.md).  
  
 Para obter mais informações sobre assemblies amigos, consulte [Assemblies Amigáveis](../../../standard/assembly/friend.md).  
  
 Essa opção não está disponível de dentro do ambiente de desenvolvimento; ela só está disponível quando se compila na linha de comando.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo compila um assembly com um tipo privado que concede acesso de assembly amigável a um assembly denominado csman_an_assembly.  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo compila um .netmodule que acessa um tipo não público no assembly moduleassemblyname_1.dll. Ao saber que este módulo .net será incorporado em um conjunto chamado csman_an_assembly, podemos especificar **-moduleassemblyname**, permitindo que o módulo .neta acesse tipos não públicos em um conjunto que concedeu acesso de reunião de amigos a csman_an_assembly.  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo de código compila o assembly csman_an_assembly, referenciando o assembly compilado anteriormente e o .netmodule.  
  
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
  
**An_Internal_Class.Test foi chamado**

## <a name="see-also"></a>Confira também

- [C# Opções de compilador](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
