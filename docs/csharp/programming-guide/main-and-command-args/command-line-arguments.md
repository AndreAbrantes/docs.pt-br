---
title: Argumentos de linha de comando – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093504"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumentos de linha de comando (Guia de Programação em C#)

Você pode enviar argumentos para o método `Main` definindo o método de uma das seguintes maneiras:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Para habilitar argumentos de `Main` linha de comando no método em um `Main` aplicativo Do Windows Forms, você deve modificar manualmente a assinatura do *program.cs*. O código gerado pelo Designer de Formulários do Windows cria um `Main` sem um parâmetro de entrada. Você também pode usar <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> para acessar os argumentos de linha de comando de qualquer ponto em um console ou um aplicativo do Windows.

O parâmetro do método `Main` é uma matriz <xref:System.String> que representa os argumentos de linha de comando. Geralmente você determina se os argumentos existem testando a propriedade `Length`, por exemplo:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Você também pode converter os argumentos de cadeia de caracteres em tipos numéricos, usando a classe <xref:System.Convert> ou o método `Parse`. Por exemplo, a instrução a seguir converte o `string` em um número `long` usando o método <xref:System.Int64.Parse%2A>:

```csharp
long num = Int64.Parse(args[0]);
```

Também é possível usar o tipo `long` de C#, que funciona como alias de `Int64`:

```csharp
long num = long.Parse(args[0]);
```

Você também pode usar o método da classe `Convert`, o `ToInt64`, para fazer a mesma coisa:

```csharp
long num = Convert.ToInt64(s);
```

Para obter mais informações, consulte <xref:System.Int64.Parse%2A> e <xref:System.Convert>.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar argumentos de linha de comando em um aplicativo de console. O aplicativo recebe um argumento em tempo de execução, converte o argumento em um número inteiro e calcula o fatorial do número. Se nenhum argumento for fornecido, o aplicativo emitirá uma mensagem que explica o uso correto do programa.

Para compilar e executar o aplicativo em um prompt de comando, siga estas etapas:

1. Cole o seguinte código em qualquer editor de texto e, em seguida, salve o arquivo como um arquivo de texto com o nome *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Na tela **Inicial** ou no menu **Iniciar**, abra uma janela de **Prompt de Comando do Desenvolvedor** do Visual Studio e, em seguida, navegue até a pasta que contém o arquivo que você acabou de criar.

3. Digite o seguinte comando para compilar o aplicativo.
  
     `csc Factorial.cs`  
  
     Se o aplicativo não tiver erros de compilação, um arquivo executável chamado *Factorial.exe* será criado.
  
4. Digite o seguinte comando para calcular o fatorial de 3:
  
     `Factorial 3`  
  
5. O comando produz esta saída: `The factorial of 3 is 6.`

> [!NOTE]
> Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Confira também

- <xref:System.Environment?displayProperty=nameWithType>
- [C# Guia de Programação](../index.md)
- [Main() e argumentos de linha de comando](index.md)
- [Como exibir argumentos de linha de comando](how-to-display-command-line-arguments.md)
- [Valores retornados de Main()](main-return-values.md)
- [Classes](../classes-and-structs/classes.md)
