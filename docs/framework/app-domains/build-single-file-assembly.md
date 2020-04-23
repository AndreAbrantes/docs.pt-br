---
title: Como compilar um .NET Framework assembly de arquivo único
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644296"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Como compilar um .NET Framework assembly de arquivo único

Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../standard/assembly/manifest.md). Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único que tenha como destino o .NET Framework. Por padrão, o compilador cria um arquivo de assembly com uma extensão *. exe* .

> [!NOTE]
> O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único. Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.

Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.

## <a name="create-an-assembly-with-an-exe-extension"></a>Criar um assembly com uma extensão. exe

No prompt de comando, digite o comando a seguir:

\<*compiler command*> \<*nome do módulo* de comando do compilador>

Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.

O exemplo a seguir cria um assembly chamado *myCode. exe* a partir de um `myCode`módulo de código chamado.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Criar um assembly com uma extensão. exe e especificar o nome do arquivo de saída

No prompt de comando, digite o comando a seguir:

\<*comando*> do compilador **/out:**\<*nome*> \<do arquivo*nome do módulo*>

Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.

O exemplo a seguir cria um assembly chamado *myAssembly. exe* a partir de um `myCode`módulo de código chamado.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Criar assemblies de biblioteca
 Um assembly de biblioteca é semelhante a uma biblioteca de classes. Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.

Para criar um assembly de biblioteca, no prompt de comando, digite o seguinte comando:

\<*comando*> do compilador **–** \< *nome do módulo* t:library>

Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly. Você também pode usar outras opções de compilador, como a opção **-out:** .

O exemplo a seguir cria um assembly de biblioteca chamado *myCodeAssembly. dll* a partir de `myCode`um módulo de código chamado.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Confira também

- [Criar assemblies](../../standard/assembly/create.md)
- [Assemblies de vários arquivos](multifile-assemblies.md)
- [Como compilar um assembly de multiarquivos](build-multifile-assembly.md)
- [Programar com assemblies](../../standard/assembly/index.md)
