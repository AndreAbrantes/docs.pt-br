---
title: "-target (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a>/target (opções do compilador C#)
A opção do compilador **/target** pode ser especificada e uma das quatro formas:  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Para criar um arquivo .exe para aplicativos [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Para criar um arquivo .exe.  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Para criar uma biblioteca de códigos.  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Para criar um módulo.  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Para criar um programa do Windows.  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Para criar um arquivo .winmdobj intermediário.  
  
 A menos que você especifique **/target:module**, o **/target** faz com que um manifesto do assembly do .NET Framework seja colocado em um arquivo de saída. Para obter mais informações, consulte [Assemblies no Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) e [Atributos comuns](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b).  
  
 O manifesto do assembly é colocado no primeiro arquivo de saída .exe na compilação ou na primeira DLL, se não houver nenhum arquivo de saída .exe. Por exemplo, na linha de comando a seguir, o manifesto será colocado em `1.exe`:  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 O compilador cria apenas um manifesto do assembly por compilação. As informações sobre todos os arquivos em uma compilação são colocados no manifesto do assembly. Todos os arquivos de saída, exceto os criados com **/target:module** podem conter um manifesto do assembly. Ao gerar vários arquivos de saída na linha de comando, apenas um manifesto do assembly pode ser criado e ele deve ir para o primeiro arquivo de saída especificado na linha de comando. Não importa qual é o primeiro arquivo de saída (**/target:exe**, **/target:winexe**, **/target:library** ou **/target:module**), todos os outros arquivos de saída produzidos na mesma compilação devem ser módulos (**/target:module**).  
  
 Se você criar um assembly, pode indicar que todo ou parte do seu código está em conformidade com CLS com o atributo <xref:System.CLSCompliantAttribute>.  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Para obter mais informações sobre configurar essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: Como Modificar as Propriedades do Projeto e as Definições de Configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [/subsystemversion (opções do compilador C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
