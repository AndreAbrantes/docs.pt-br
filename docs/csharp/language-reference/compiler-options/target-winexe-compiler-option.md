---
title: -target:winexe (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606385"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target:winexe (opções do compilador C#)
A opção **-target:winexe** faz com que o compilador crie um programa do Windows executável (EXE).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Comentários  
 O arquivo executável será criado com a extensão .exe. Um programa do Windows é aquele que fornece uma interface do usuário da biblioteca do .NET Framework ou com as APIs do Windows.  
  
 Use [-target:exe](./target-exe-compiler-option.md) para criar um aplicativo do console.  
  
 A menos que seja especificado de outra forma com a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).  
  
 Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou [-target](./target-compiler-option.md) serão usados para criar o programa do Windows.  
  
 Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. A opção [-main](./main-compiler-option.md) permite especificar qual classe contém o método **Main**, nos casos em que o código tem mais de uma classe com um método **Main**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Clique na página de propriedades do **Aplicativo**.  
  
3. Modifique a propriedade **Tipo de saída**.  
  
 Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` em um programa do Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Confira também

- [-destino (C# Opções de compilador)](./target-compiler-option.md)
- [C# Opções de compilador](./index.md)
