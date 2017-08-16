---
title: "Como criar assemblies amigáveis não assinados (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7d2924f0a619c234871232e155bb6f23e43aee4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Como criar assemblies amigáveis não assinados (C#)
Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Para criar um assembly e um assembly amigável  
  
1.  Abra um prompt de comando.  
  
2.  Crie um arquivo do C# chamado `friend_signed_A.` que contenha o seguinte código. O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar o friend_signed_B como um assembly amigável.  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3.  Compile e assine o friend_signed_A usando o seguinte comando.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Crie um arquivo do C# chamado `friend_unsigned_B` que contenha o seguinte código. Como friend_unsigned_A especifica friend_unsigned_B como um assembly amigável, o código em friend_unsigned_B pode acessar tipos `internal` e membros de friend_unsigned_A.  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5.  Compile friend_signed_B usando o comando a seguir.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você deve especificar explicitamente o nome do assembly de saída (.exe ou .dll) usando a opção do compilador `/out`. Para obter mais informações, consulte [/out (opções do compilador C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Execute o arquivo friend_signed_B.exe.  
  
     O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção do código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade de membros e tipos `internal`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblies amigáveis (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como criar assemblies amigáveis assinados (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)
