---
title: "Documentando seu código com comentários em XML"
description: "Documentando seu código"
keywords: .NET, .NET Core
author: tsolarin
ms.author: wiwagn
ms.date: 02/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.translationtype: Human Translation
ms.sourcegitcommit: d91daf2005998d81609803982f5fc2c231fe7ad3
ms.openlocfilehash: 4e873d15ae2b2e7a475ea758678423f6ec3b14b3
ms.contentlocale: pt-br
ms.lasthandoff: 05/16/2017

---

# <a name="documenting-your-code-with-xml-comments"></a>Documentando seu código com comentários em XML

Comentários em documentação XML são um tipo especial de comentário, adicionados acima da definição de qualquer membro ou tipo definido pelo usuário. Eles são especiais porque podem ser processados pelo compilador para gerar um arquivo de documentação XML em tempo de compilação.
O arquivo XML gerado pelo compilador pode ser distribuído em conjunto com seu assembly .NET para que o Visual Studio e outros IDEs possam usar o IntelliSense para mostrar informações rápidas sobre os tipos ou membros. Além disso, o arquivo XML pode ser executado por ferramentas como [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://github.com/EWSoftware/SHFB) para gerar sites de referência de API.

Comentários de documentação XML, como todos os outros comentários, são ignorados pelo compilador.

É possível gerar o arquivo XML em tempo de compilação seguindo um destes procedimentos:

- Se estiver desenvolvendo um aplicativo com .NET Core da linha de comando, você poderá adicionar um [elemento DocumentationFile](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) à seção `<PropertyGroup>` do arquivo de projeto .csproj. O exemplo a seguir gera um arquivo XML no diretório do projeto com o mesmo nome de arquivo raiz do projeto:

   ```xml
   <DocumentationFile>$(MSBuildProjectName).xml</DocumentationFile>
   ```

   Você também pode especificar o caminho relativo ou absoluto exato e o nome do arquivo XML. O exemplo a seguir gera o arquivo XML no mesmo diretório que a versão de depuração de um aplicativo:

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- Se estiver desenvolvendo um aplicativo usando o Visual Studio, clique com botão direito do mouse no projeto e selecione **Propriedades**. Na caixa de diálogo Propriedades, selecione a guia **Build** e marque **Arquivo de documentação XML**. Também é possível alterar o local em que o compilador grava o arquivo. 

- Se você estiver compilando um aplicativo .NET Framework da linha de comando, adicione a [opção do compilador /doc](language-reference/compiler-options/doc-compiler-option.md) durante a compilação.  

Comentários de documentação XML usam três barras (`///`) e o corpo do comentário formatado em XML. Por exemplo:

[!code-csharp[Comentário da documentação XML](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Passo a passo

Vamos examinar a documentação de uma biblioteca de matemática bastante básica para facilitar a compreensão/contribuição por novos desenvolvedores e facilitar o uso por desenvolvedores de terceiros.

Este é o código para a biblioteca de matemática simples:

[!code-csharp[Biblioteca de exemplos](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

A biblioteca de exemplo dá suporte a quatro operações aritméticas principais, `add`, `subtract`, `multiply` e `divide`, nos tipos de dados `int` e `double`.

Agora, você quer poder criar um documento de referência de API do seu código para desenvolvedores de terceiros que usam sua biblioteca, mas não têm acesso ao código-fonte.
Conforme mencionado, marcas de documentação XML anteriores podem ser usadas para fazer isso. Agora, você conhecerá as marcas XML padrão a que o compilador C# dá suporte.

### <a name="ltsummarygt"></a>&lt;summary&gt;

A marca `<summary>` adiciona informações sucintas sobre um tipo ou membro.
Vou demonstrar seu uso adicionando-a à definição de classe `Math` e ao primeiro método `Add`. Fique à vontade para aplicá-la ao restante de seu código.

[!code-csharp[Marcação summary](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

A marca `<summary>` é muito importante e é recomendável inclui-la, porque seu conteúdo é a principal fonte de informações sobre o tipo ou membro no IntelliSense ou em um documento de referência de API.

### <a name="ltremarksgt"></a>&lt;remarks&gt;

A marca `<remarks>` complementa as informações sobre tipos ou membros que a marca `<summary>` fornece. Neste exemplo, você apenas a adiciona à classe.

[!code-csharp[Marcação remarks](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;returns&gt;

A marca `<returns>` descreve o valor retornado de uma declaração de método.
Assim como antes, o exemplo a seguir ilustra a marca `<returns>` no primeiro método `Add`. É possível fazer o mesmo em outros métodos.

[!code-csharp[Marcação returns](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

A marca `<value>` é semelhante à marca `<returns>`, exceto pelo fato de você usá-la para propriedades.
Supondo que sua biblioteca `Math` tivesse uma propriedade estática chamada `PI`, você usaria essa marca desta forma:

[!code-csharp[Marcação value](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;example&gt;

Você usa a marca `<example>` para incluir um exemplo em sua documentação XML.
Isso envolve o uso da marca `<code>` filho.

[!code-csharp[Marcação example](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

A marca `code` preserva quebras de linha e recuos para exemplos mais longos.

### <a name="ltparagt"></a>&lt;para&gt;

Você usa a marca `<para>` para formatar o conteúdo dentro de sua marca pai. Normalmente, `<para>` é usado dentro de uma marcação, como `<remarks>` ou `<returns>`, para dividir o texto em parágrafos.
Você pode formatar o conteúdo da marcação `<remarks>` para a definição de classe.

[!code-csharp[Marcação para](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Ainda com relação à formatação, use a marca `<c>` para marcar parte do texto como código.
Ela é semelhante à marca `<code>`, mas embutida. Ela é útil quando você deseja mostrar um exemplo de código rápido como parte do conteúdo da marca.
Vamos atualizar a documentação para a classe `Math`.

[!code-csharp[Marcação c](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;exception&gt;

Usando a marca `<exception>`, você informa os desenvolvedores de que um método pode lançar exceções específicas.
Observando sua biblioteca `Math`, você pode ver que ambos os métodos `Add` lançarão uma exceção se uma determinada condição for atendida. Algo menos óbvio, porém, é que o método inteiro `Divide` também será lançado se o parâmetro `b` for zero. Agora, adicione a documentação de exceção a esse método.

[!code-csharp[Marcação exception](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

O atributo `cref` representa uma referência a uma exceção que está disponível no ambiente de compilação atual.
Pode ser qualquer tipo definido no projeto ou um assembly referenciado. O compilador emitirá um aviso se o valor não puder ser resolvido.

### <a name="ltseegt"></a>&lt;see&gt;

A marca `<see>` permite criar um link clicável para uma página de documentação para outro elemento de código. Em nosso próximo exemplo, criaremos um link clicável entre os dois métodos `Add`.

[!code-csharp[Marcação see](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

O `cref` é um atributo **obrigatório** que representa uma referência para um tipo ou seu membro que está disponível no ambiente de compilação atual. Pode ser qualquer tipo definido no projeto ou um assembly referenciado.

### <a name="ltseealsogt"></a>&lt;seealso&gt;

Você usa a marca `<seealso>` da mesma forma que usaria a marca `<see>`. A única diferença é que seu conteúdo normalmente é colocado em uma seção "Consulte também". Aqui, adicionaremos uma marca `seealso` ao método inteiro `Add` para fazer referência a outros métodos na classe que aceitam parâmetros inteiros:

[!code-csharp[Marcação seealso](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

O atributo `cref` representa uma referência para um tipo ou seu membro que está disponível no ambiente de compilação atual.
Pode ser qualquer tipo definido no projeto ou um assembly referenciado.

### <a name="ltparamgt"></a>&lt;param&gt;

Você usa a marca `<param>` para descrever os parâmetros de um método. Este é um exemplo do método `Add` duplo: o parâmetro que a marca descreve é especificado no atributo `name` **obrigatório**.

[!code-csharp[Marcação param](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Use a marca `<typeparam>` exatamente como a marca `<param>`, mas para declarações de método ou de tipo genérico para descrever um parâmetro genérico.
Adicione um método genérico rápido à sua classe `Math` para verificar se uma quantidade é maior que outra.

[!code-csharp[Marcação typeparam](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

Às vezes, você pode estar descrevendo o que um método faz, no que poderia ser uma marcação `<summary>` e talvez queira fazer uma referência a um parâmetro. A marcação `<paramref>` é excelente para exatamente isso. Vamos atualizar o resumo de nosso método `Add` de base dupla. Assim como a marca `<param>`, o nome do parâmetro é especificado no atributo `name` **obrigatório**.

[!code-csharp[Marcação paramref](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Use a marca `<typeparamref>` exatamente como a marca `<paramref>`, mas para declarações de método ou de tipo genérico para descrever um parâmetro genérico.
É possível usar o mesmo método genérico criado anteriormente.

[!code-csharp[Marcação typeparamref](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Use a marca `<list>` para formatar informações de documentação como uma lista ordenada, uma lista não ordenada ou uma tabela.
Crie uma lista não ordenada de cada operação matemática a que sua biblioteca `Math` dá suporte.

[!code-csharp[Marcação list](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

É possível fazer uma lista ordenada ou tabela alterando o atributo `type` para `number` ou `table`, respectivamente.

### <a name="putting-it-all-together"></a>Juntando as peças

Se você seguiu o tutorial e aplicou as marcas ao seu código quando necessário, seu código deve ser semelhante ao seguinte:

[!code-csharp[Biblioteca marcada](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

No seu código, você pode gerar um site de documentação detalhada completo com referências cruzadas clicáveis. Mas você se depara com outro problema: o código tornou-se difícil de ler.
Há tanta informação para ser analisada que será um pesadelo para qualquer desenvolvedor que desejar contribuir para esse código. Felizmente, há uma marca XML que pode ajudá-lo a lidar com isso:

### <a name="ltincludegt"></a>&lt;include&gt;

A marcação `<include>` permite fazer referência a comentários em um arquivo XML separado que descrevem os tipos e membros em seu código-fonte, em vez de colocar comentários de documentação diretamente em seu arquivo de código-fonte.

Agora, você moverá todas as suas marcas XML para um arquivo XML separado chamado `docs.xml`. Fique à vontade para nomear o arquivo como desejar.

[!code-xml[XML de exemplo](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

No XML acima, os comentários de documentação de cada membro aparecem diretamente dentro de uma marca cujo nome corresponde ao que eles fazem. Você pode escolher sua própria estratégia. Agora que você tem seus comentários XML em um arquivo separado, vamos ver como seu código pode ficar mais legível usando a marca `<include>`:

[!code-csharp[Marcação include](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

E aqui está: nosso código voltou a ser legível e nenhuma informação de documentação foi perdida. 

O atributo `filename` representa o nome do arquivo XML que contém a documentação.

O atributo `path` representa uma consulta [XPath](https://msdn.microsoft.com/library/ms256115.aspx) para o `tag name` presente no `filename` especificado.

O atributo `name` representa o especificador de nome na marca que precede os comentários.

O atributo `id` que pode ser usado no lugar de `name` representa a ID da marca que precede os comentários.

### <a name="user-defined-tags"></a>Marcas definidas pelo usuário

Todas as marcas descritas acima representam as marcas que são reconhecidas pelo compilador C#. No entanto, o usuário é livre para definir suas próprias marcas.
Ferramentas como o Sandcastle dão suporte para marcas extras, como [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) e até mesmo à [documentação de namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Ferramentas de geração de documentação internas ou personalizadas também podem ser usadas com as marcas padrão e vários formatos de saída, de HTML a PDF, podem ter suporte.

## <a name="recommendations"></a>Recomendações

Documentar o código é recomendável por vários motivos. A seguir, temos algumas práticas recomendadas, cenários de caso de uso gerais e coisas que você precisa saber ao usar marcas de documentação XML em seu código C#.

* Para fins de consistência, todos os tipos visíveis publicamente e seus membros devem ser documentados. Se você precisar fazer isso, faça tudo.
* Membros particulares também podem ser documentados usando comentários XML. No entanto, isso expõe o funcionamento interno (potencialmente confidencial) de sua biblioteca.
* No mínimo, os tipos e seus membros devem ter uma marca `<summary>`, porque seu conteúdo é necessário para o IntelliSense.
* O texto da documentação deve ser escrito usando frases terminadas com ponto final.
* Classes parciais têm suporte total e informações da documentação serão concatenadas em uma única entrada para esse tipo.
* O compilador verifica a sintaxe das marcas `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` e `<typeparam>`.
- O compilador valida os parâmetros que contêm caminhos de arquivo e referências para outras partes do código.

## <a name="see-also"></a>Consulte também
[Comentários de documentação XML (Guia de Programação em C#)](programming-guide/xmldoc/xml-documentation-comments.md)

[Marcas recomendadas para comentários de documentação (Guia de Programação em C#)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

