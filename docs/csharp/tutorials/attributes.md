---
title: "Atributos – C# | Microsoft Docs"
description: Saiba como os atributos funcionam em C#.
keywords: .NET, .NET Core, C#, atributos
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 512a222a727e3e6a032848b87463dda0ae8f7362
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

# Usando atributos no C#
<a id="using-attributes-in-c" class="xliff"></a> #

Os atributos fornecem uma maneira de associar informações ao código de forma declarativa. Eles também podem fornecer um elemento reutilizável que pode ser aplicado a uma variedade de destinos.

Considere o atributo `[Obsolete]`. Ele pode ser aplicado a classes, structs, métodos, construtores e muito mais. Ele _declara_ que o elemento é obsoleto. Em seguida, cabe ao compilador C# procurar esse atributo e realizar alguma ação em resposta.

Neste tutorial, você verá como adicionar atributos a seu código, como criar e usar seus próprios atributos e como usar alguns atributos que são criados no .NET Core.

## Pré-requisitos
<a id="prerequisites" class="xliff"></a>
Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).
Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker. Será necessário instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.

## Criar o aplicativo
<a id="create-the-application" class="xliff"></a>

Agora que você instalou todas as ferramentas, crie um novo aplicativo do .NET Core. Para usar o gerador de linha de comando, execute o seguinte comando no shell de sua preferência:

`dotnet new console`

Esse comando criará arquivos de projeto do .NET Core barebones. Você precisará executar `dotnet restore` para restaurar as dependências necessárias para compilar esse projeto.

Para executar o programa, use `dotnet run`. Você deve ver a saída do "Olá, Mundo" no console.

## Como adicionar atributos ao código
<a id="how-to-add-attributes-to-code" class="xliff"></a>

No C#, os atributos são classes que herdam da classe base `Attribute`. Qualquer classe que herda de `Attribute` pode ser usada como uma espécie de "marcação" em outras partes do código.
Por exemplo, há um atributo chamado `ObsoleteAttribute`. Ele é usado para sinalizar que o código está obsoleto e não deve mais ser usado. Você pode colocar este atributo em uma classe, por exemplo, usando colchetes.

[!code-csharp[Exemplo de atributo obsoleto](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Observe que, embora a classe seja chamada de `ObsoleteAttribute`, só é necessário usar `[Obsolete]` no código. Isso é uma convenção que a linguagem C# segue.
Você poderá usar o nome completo `[ObsoleteAttribute]` se escolher.

Ao marcar uma classe obsoleta, é uma boa ideia fornecer algumas informações como o *motivo* de estar obsoleto e/ou *o que* usar no lugar. Faça isso passando um parâmetro de cadeia de caracteres para o atributo obsoleto.

[!code-csharp[Exemplo de atributo obsoleto com parâmetros](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

A cadeia de caracteres está sendo passada como um argumento para um construtor `ObsoleteAttribute`, como se você estivesse escrevendo `var attr = new ObsoleteAttribute("some string")`.

Os parâmetros para um construtor de atributo são limitados a literais/tipos simples: `bool, int, double, string, Type, enums, etc` e matrizes desses tipos.
Você não pode usar uma expressão ou uma variável. Você pode usar parâmetros posicionais ou nomeados.

## Como criar seu próprio atributo
<a id="how-to-create-your-own-attribute" class="xliff"></a>

Criar um atributo é tão simples quanto herdar de uma classe base `Attribute`.

[!code-csharp[Criar seu próprio atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Com os itens acima, agora posso usar `[MySpecial]` (ou `[MySpecialAttribute]`) como um atributo em qualquer lugar na base do código.

[!code-csharp[Usando seu próprio atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Os atributos biblioteca de classes base do .NET, como `ObsoleteAttribute`, disparam determinados comportamentos no compilador. No entanto, qualquer atributo que você cria atua como metadados e não resulta em qualquer código dentro da classe de atributo que está sendo executada. Cabe a você agir nesses metadados no seu código (mais sobre isso posteriormente no tutorial).

Há uma “pegadinha” aqui. Conforme mencionado acima, somente determinados tipos podem ser passados como argumentos ao usar atributos. No entanto, ao criar um tipo de atributo, o compilador C# não impedirá você de criar esses parâmetros. No exemplo abaixo, criei um atributo com um construtor que compila bem.

[!code-csharp[Construtor válido usado em um atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

No entanto, não será possível usar esse construtor com a sintaxe de atributo.

[!code-csharp[Tentativa inválida de usar o construtor de atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

O descrito acima causará um erro do compilador como `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## Como restringir o uso do atributo
<a id="how-to-restrict-attribute-usage" class="xliff"></a>

Os atributos podem ser usados em um número de "destinos". Os exemplos acima mostram os atributos em classes, mas eles também podem ser usados em:

* Assembly
* Classe
* Construtor
* Representante
* Enum
* Evento
* Campo
* GenericParameter
* Interface
* Método
* Módulo
* Parâmetro
* Propriedade
* ReturnValue
* Estrutura

Quando você cria uma classe de atributo, por padrão, o C# permitirá que você use esse atributo em qualquer um dos destinos possíveis do atributo. Se quiser restringir seu atributo a determinados destinos, você poderá fazer isso usando o `AttributeUsageAttribute` em sua classe de atributo. É isso mesmo, um atributo em um atributo!

[!code-csharp[Usando seu próprio atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Se tentar colocar o atributo acima em algo que não é uma classe ou um struct, você obterá um erro do compilador como `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Usando seu próprio atributo](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## Como usar atributos anexados a um elemento de código
<a id="how-to-use-attributes-attached-to-a-code-element" class="xliff"></a>

Atributos agem como metadados. Sem nenhuma força, eles não farão nada.

Para localizar e agir sobre os atributos, geralmente é necessário [Reflexão](../programming-guide/concepts/reflection.md). Não abordarei Reflexão detalhadamente neste tutorial, mas a ideia básica é a Reflexão permite que você escreva um código em C# que examine outro código.

Por exemplo, você pode usar a Reflexão para obter informações sobre uma classe: 

[!code-csharp[Obtendo informações sobre o tipo com a Reflexão](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Isso imprimirá algo como: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Depois de ter um objeto `TypeInfo` (ou um `MemberInfo`, `FieldInfo`, etc.), você poderá usar o método `GetCustomAttributes`. Isso retornará uma coleção de objetos `Attribute`.
Você também poderá usar `GetCustomAttribute` e especificar um tipo de atributo.

Aqui está um exemplo do uso de `GetCustomAttributes` em uma instância `MemberInfo` para `MyClass` (que vimos, anteriormente, que tem um atributo `[Obsolete]` nele).

[!code-csharp[Obtendo informações sobre o tipo com a Reflexão](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Isso será impresso no console: `Attribute on MyClass: ObsoleteAttribute`. Tente adicionar outros atributos a `MyClass`.

É importante observar que esses objetos `Attribute` são instanciados lentamente. Ou seja, eles não serão instanciados até que você use `GetCustomAttribute` ou `GetCustomAttributes`.
Eles também são instanciados a cada vez. Chamar `GetCustomAttributes` duas vezes em uma linha retornará duas instâncias diferentes do `ObsoleteAttribute`.

## Atributos comuns na BCL (biblioteca de classes base)
<a id="common-attributes-in-the-base-class-library-bcl" class="xliff"></a>

Os atributos são usados por muitas ferramentas e estruturas. O NUnit usa atributos como `[Test]` e `[TestFixture]` que são usados pelo executor de teste NUnit. O ASP.NET MVC usa atributos como `[Authorize]` e fornece uma estrutura de filtro de ação para executar questões abrangentes sobre as ações do MVC. O [PostSharp](https://www.postsharp.net) usa a sintaxe de atributo para permitir a programação em C# orientada ao aspecto.

Aqui estão alguns atributos importantes incorporados às bibliotecas de classes base do .NET Core:

* `[Obsolete]`. Este foi usado nos exemplos acima, e reside no namespace `System`. Isso é útil para fornecer a documentação declarativa sobre uma base de código de alteração. Uma mensagem pode ser fornecida na forma de uma cadeia de caracteres e outro parâmetro booliano pode ser usado para encaminhamento de um aviso do compilador para um erro do compilador.

* `[Conditional]`. Esse atributo está no namespace `System.Diagnostics`. Esse atributo pode ser aplicado aos métodos (ou classes de atributo). Você deve passar uma cadeia de caracteres para o construtor.
Se essa cadeia de caracteres corresponder a uma diretiva `#define`, então todas as chamadas para o método (mas não o próprio método) serão removidas pelo compilador C#. Normalmente, isso é usado para depuração (diagnóstico).

* `[CallerMemberName]`. Esse atributo pode ser usado em parâmetros e reside no namespace `System.Runtime.CompilerServices`. Este é um atributo que é usado para injetar o nome do método que está chamando outro método. Isso normalmente é usado como uma forma de eliminar 'cadeias de caracteres mágicas' ao implementar INotifyPropertyChanged em diversas estruturas de interface do usuário. Um exemplo:

[!code-csharp[Usando CallerMemberName ao implementar INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

No código acima, você não precisa ter uma cadeia de caracteres `"Name"` literal. Isso pode ajudar a evitar erros relacionados à digitação e também possibilita a refatoração/renomeação mais suave.

## Resumo
<a id="summary" class="xliff"></a>

Os atributos fornecem poder declarativo ao C#. Mas eles são uma forma de código como metadados e não agem por si.

