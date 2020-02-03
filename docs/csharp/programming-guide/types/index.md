---
title: Tipos – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: be2af77f9680ab3285720525638bba8ef2041999
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745381"
---
# <a name="types-c-programming-guide"></a>Tipos (Guia de Programação em C#)

## <a name="types-variables-and-values"></a>Tipos, variáveis e valores

C# é uma linguagem fortemente tipada. Todas as variáveis e constantes têm um tipo, assim como cada expressão que é avaliada como um valor. Cada assinatura de método especifica um tipo para cada parâmetro de entrada e para o valor retornado. A biblioteca de classes do .NET define um conjunto de tipos numéricos internos, bem como tipos mais complexos que representam uma ampla variedade de constructos lógicos, como o sistema de arquivos, as conexões de rede, as coleções e as matrizes de objetos e as datas. Um programa em C# típico usa tipos da biblioteca de classes, bem como tipos definidos pelo usuário que modelam os conceitos que são específicos para o domínio do problema do programa.

As informações armazenadas em um tipo podem incluir o seguinte:

- O espaço de armazenamento que uma variável do tipo requer.

- Os valores mínimo e máximo que ele pode representar.

- Os membros (métodos, campos, eventos e etc.) que ele contém.

- O tipo base do qual ele herda.

- O local no qual a memória para as variáveis será alocada em tempo de execução.

- Os tipos de operações que são permitidos.

O compilador usa as informações de tipo para garantir que todas as operações que são realizadas em seu código sejam *fortemente tipadas*. Por exemplo, se você declarar uma variável do tipo [int](../../language-reference/builtin-types/integral-numeric-types.md), o compilador permitirá que você use a variável nas operações de adição e subtração. Se você tentar executar as mesmas operações em uma variável do tipo [bool](../../language-reference/builtin-types/bool.md), o compilador gerará um erro, como mostrado no exemplo a seguir:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> Desenvolvedores de C e C++, observem que, em C#, [bool](../../language-reference/builtin-types/bool.md) não é conversível em [int](../../language-reference/builtin-types/integral-numeric-types.md).

O compilador insere as informações de tipo no arquivo executável como metadados. O CLR (Common Language Runtime) usa metadados em tempo de execução para garantir mais segurança de tipos quando aloca e recupera a memória.

### <a name="specifying-types-in-variable-declarations"></a>Especificando tipos em declarações de variável

Quando declara uma variável ou constante em um programa, você deve especificar seu tipo ou usar a palavra-chave [var](../../language-reference/keywords/var.md) para permitir que o compilador infira o tipo. O exemplo a seguir mostra algumas declarações de variáveis que usam tipos numéricos internos e tipos complexos definidos pelo usuário:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Os tipos de parâmetros de método e valores de retorno são especificados na assinatura do método. A assinatura a seguir mostra um método que requer um [int](../../language-reference/builtin-types/integral-numeric-types.md) como um argumento de entrada e retorna uma cadeia de caracteres:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Depois que uma variável é declarada, ela não pode ser declarada novamente com um novo tipo e não pode ter um valor atribuído que não seja compatível com seu tipo declarado. Por exemplo, você não pode declarar um [int](../../language-reference/builtin-types/integral-numeric-types.md) e, em seguida, atribuir a ele um valor booliano de `true`. No entanto, os valores podem ser convertidos em outros tipos, por exemplo, quando são passados como argumentos de método ou atribuídos a novas variáveis. Uma *conversão de tipo* que não causa a perda de dados é executada automaticamente pelo compilador. Uma conversão que pode causar perda de dados requer um *cast* no código-fonte.

Para obter mais informações, consulte [Conversões e conversões de Tipo](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Tipos internos

O C# fornece um conjunto padrão de tipos numéricos internos para representar números inteiros, valores de ponto flutuante, expressões boolianas, caracteres de texto, valores decimais e outros tipos de dados. Também há tipos `string` e `object` internos. Eles estão disponíveis para uso em qualquer programa em C#. Para obter mais informações sobre os tipos internos, consulte [Tabelas de referência de tipos internos](../../language-reference/keywords/built-in-types-table.md).

## <a name="custom-types"></a>Tipos personalizados

Você usa os constructos [struct](../../language-reference/keywords/struct.md), [classe](../../language-reference/keywords/class.md), [interface](../../language-reference/keywords/interface.md) e [enum](../../language-reference/builtin-types/enum.md) para criar seus próprios tipos personalizados. A biblioteca de classes do .NET em si é uma coleção de tipos personalizados fornecida pela Microsoft, que você pode usar em seus próprios aplicativos. Por padrão, os tipos usados com mais frequência na biblioteca de classes estão disponíveis em qualquer programa em C#. Outros ficam disponíveis somente quando você adiciona explicitamente uma referência de projeto ao assembly no qual eles estão definidos. Após o compilador ter uma referência ao assembly, você pode declarar variáveis (e constantes) dos tipos declarados no assembly no código-fonte. Para saber mais, confira [Biblioteca de classes do .NET](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>O Common Type System

É importante entender os dois pontos fundamentais sobre o sistema de tipos do .NET:

- Ele dá suporte ao conceito de herança. Os tipos podem derivar de outros tipos, chamados *tipos base*. O tipo derivado herda (com algumas restrições) os métodos, as propriedades e outros membros do tipo base. O tipo base, por sua vez, pode derivar de algum outro tipo, nesse caso, o tipo derivado herda os membros de ambos os tipos base na sua hierarquia de herança. Todos os tipos, incluindo tipos numéricos internos, como <xref:System.Int32?displayProperty=nameWithType> (palavra-chave de C#: [int](../../language-reference/builtin-types/integral-numeric-types.md)), derivam, em última análise, de um único tipo base, que é o <xref:System.Object?displayProperty=nameWithType> (palavra-chave de C#: [object](../../language-reference/builtin-types/reference-types.md)). Essa hierarquia unificada de tipos é chamada de CTS [(Common Type System)](../../../standard/base-types/common-type-system.md). Para obter mais informações sobre herança em C#, consulte [Herança](../classes-and-structs/inheritance.md).

- Cada tipo no CTS é definido como um *tipo de valor* ou um *tipo de referência*. Isso inclui todos os tipos personalizados na biblioteca de classes do .NET, além de tipos personalizados definidos pelo usuário. Os tipos que você define usando a palavra-chave [struct](../../language-reference/keywords/struct.md) são tipos de valor. Todos os tipos numéricos internos são `structs`. Os tipos que você define usando a palavra-chave [classe](../../language-reference/keywords/class.md) são tipos de referência. Os tipos de referência e os tipos de valor têm diferentes regras de tempo de compilação e comportamento de tempo de execução diferente.

A ilustração a seguir mostra a relação entre tipos de referência e tipos de valor no CTS.

A imagem a seguir mostra os tipos de valor e tipos de referência no CTS:

![Captura de tela que mostra de tipos de valor CTS e tipos de referência.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Você pode ver que os tipos mais usados normalmente são todos organizados no namespace <xref:System>. No entanto, o namespace no qual um tipo está contido não tem relação com a possibilidade de ele ser um tipo de valor ou um tipo de referência.

### <a name="value-types"></a>Tipos de valor

Os tipos de valor derivam de <xref:System.ValueType?displayProperty=nameWithType>, que deriva de <xref:System.Object?displayProperty=nameWithType>. Os tipos que derivam de <xref:System.ValueType?displayProperty=nameWithType> apresentam um comportamento especial no CLR. As variáveis de tipo de valor contêm diretamente seus valores, o que significa que a memória é alocada embutida em qualquer contexto em que a variável é declarada. Não há nenhuma alocação de heap separada ou sobrecarga de coleta de lixo para variáveis do tipo de valor.

Há duas categorias de tipos de valor: [struct](../../language-reference/keywords/struct.md) e [enum](../../language-reference/builtin-types/enum.md).

Os tipos numéricos internos são structs e têm propriedades e métodos que você pode acessar:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Mas você declara e atribui valores a eles como se fossem tipos de não agregação simples:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Tipos de valor são *lacrados*, o que significa, por exemplo, que você não pode derivar um tipo de <xref:System.Int32?displayProperty=nameWithType> e não pode definir um struct para herdar de qualquer struct ou classe definida pelo usuário, porque um struct apenas pode herdar de <xref:System.ValueType?displayProperty=nameWithType>. No entanto, um struct pode implementar uma ou mais interfaces. É possível converter um tipo de struct em qualquer tipo de interface que ele implementa. Isso faz com que uma operação de *conversão boxing* envolva o struct dentro de um objeto de tipo de referência no heap gerenciado. As operações de conversão boxing ocorrem quando você passa um tipo de valor para um método que usa um <xref:System.Object?displayProperty=nameWithType> ou qualquer tipo de interface como parâmetro de entrada. Para obter mais informações, consulte [Boxing e unboxing](./boxing-and-unboxing.md).

Você usa a palavra-chave [struct](../../language-reference/keywords/struct.md) para criar seus próprios tipos de valor personalizados. Normalmente, um struct é usado como um contêiner para um pequeno conjunto de variáveis relacionadas, conforme mostrado no exemplo a seguir:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Para obter mais informações sobre structs, consulte [Structs](../classes-and-structs/structs.md). Para obter mais informações sobre tipos de valor, consulte [tipos de valor](../../language-reference/builtin-types/value-types.md).

A outra categoria de tipos de valor é [enum](../../language-reference/builtin-types/enum.md). Uma enum define um conjunto de constantes integrais nomeadas. Por exemplo, a enumeração <xref:System.IO.FileMode?displayProperty=nameWithType> na biblioteca de classes do .NET contém um conjunto de números inteiros constantes nomeados que especificam como um arquivo deve ser aberto. Ela é definida conforme mostrado no exemplo abaixo:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

A constante `System.IO.FileMode.Create` tem um valor de 2. No entanto, o nome é muito mais significativo para a leitura do código-fonte por humanos e, por esse motivo, é melhor usar enumerações em vez de números literais constantes. Para obter mais informações, consulte <xref:System.IO.FileMode?displayProperty=nameWithType>.

Todas as enumerações herdam de <xref:System.Enum?displayProperty=nameWithType>, que herda de <xref:System.ValueType?displayProperty=nameWithType>. Todas as regras que se aplicam a structs também se aplicam a enums. Para obter mais informações sobre enums, consulte [tipos de enumeração](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Tipos de referência

Um tipo que é definido como uma [classe](../../language-reference/keywords/class.md), [delegado](../../language-reference/builtin-types/reference-types.md), matriz ou [interface](../../language-reference/keywords/interface.md) é um *tipo de referência*. No tempo de execução, quando você declara uma variável de um tipo de referência, a variável contém o valor [null](../../language-reference/keywords/null.md) até você criar explicitamente um objeto usando o operador [new](../../language-reference/operators/new-operator.md) ou atribuir a ele um objeto que foi criado em outro lugar com o operador `new`, conforme mostrado no exemplo a seguir:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Uma interface deve ser inicializada com um objeto da classe que a implementa. Se `MyClass` implementa `IMyInterface`, você cria uma instância de `IMyInterface`, conforme mostrado no exemplo a seguir:

```csharp
IMyInterface iface = new MyClass();
```

Quando o objeto é criado, a memória é alocada no heap gerenciado e a variável contém apenas uma referência ao local do objeto. Os tipos no heap gerenciado requerem sobrecarga quando são alocados e quando são recuperados pela funcionalidade de gerenciamento automático de memória do CLR, que é conhecida como *coleta de lixo*. No entanto, a coleta de lixo também é altamente otimizada e na maioria dos cenários não cria um problema de desempenho. Para obter mais informações sobre a coleta de lixo, consulte [Gerenciamento automático de memória](../../../standard/automatic-memory-management.md).

Todas as matrizes são tipos de referência, mesmo se seus elementos forem tipos de valor. As matrizes derivam implicitamente da classe <xref:System.Array?displayProperty=nameWithType>, mas você declara e usa as matrizes com a sintaxe simplificada fornecida pelo C#, conforme mostrado no exemplo a seguir:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Os tipos de referência dão suporte completo à herança. Ao criar uma classe, você pode herdar de outra interface ou classe que não está definida como [lacrada](../../language-reference/keywords/sealed.md), e outras classes podem herdar de sua classe e substituir os métodos virtuais. Para obter mais informações sobre como criar suas próprias classes, consulte [Classes e structs](../classes-and-structs/index.md). Para obter mais informações sobre herança e métodos virtuais, consulte [Herança](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Tipos de valores literais

No C#, valores literais recebem um tipo do compilador. Você pode especificar como um literal numérico deve ser digitado anexando uma letra ao final do número. Por exemplo, para especificar que o valor 4,56 deve ser tratado como um float, acrescente um "f" ou "F" após o número: `4.56f`. Se nenhuma letra for anexada, o compilador inferirá um tipo para o literal. Para obter mais informações sobre quais tipos podem ser especificados com sufixos de letra, consulte [tipos numéricos inteiros](../../language-reference/builtin-types/integral-numeric-types.md) e [tipos numéricos de ponto flutuante](../../language-reference/builtin-types/floating-point-numeric-types.md).

Como os literais são tipados e todos os tipos derivam basicamente de <xref:System.Object?displayProperty=nameWithType>, você pode escrever e compilar o código como o seguinte:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Tipos genéricos

Um tipo pode ser declarado com um ou mais *parâmetros de tipo* que servem como um espaço reservado para o tipo real (o *tipo concreto*) que o código do cliente fornecerá ao criar uma instância do tipo. Esses tipos são chamados de *tipos genéricos*. Por exemplo, o tipo .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> tem um parâmetro de tipo que, por convenção, recebe o nome *t*. Ao criar uma instância do tipo, você especifica o tipo dos objetos que a lista conterá, por exemplo, Cadeia de caracteres:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

O uso do parâmetro de tipo possibilita a reutilização da mesma classe para conter qualquer tipo de elemento sem precisar converter cada elemento em [objeto](../../language-reference/builtin-types/reference-types.md). As classes de coleção genéricas são chamadas de *coleções fortemente tipadas* porque o compilador sabe o tipo específico dos elementos da coleção e pode gerar um erro em tempo de compilação se, por exemplo, você tentar adicionar um inteiro ao objeto `stringList` no exemplo anterior. Para obter mais informações, consulte [Genéricos](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Tipos implícitos, tipos anônimos e tipos de valor anulável

Conforme mencionado anteriormente, você pode digitar implicitamente uma variável local (mas não os membros de classe) usando a palavra-chave [var](../../language-reference/keywords/var.md). A variável ainda recebe um tipo em tempo de compilação, mas o tipo é fornecido pelo compilador. Para obter mais informações, consulte [Variáveis Locais de Tipo Implícito](../classes-and-structs/implicitly-typed-local-variables.md).

Em alguns casos, é inconveniente criar um tipo nomeado para conjuntos simples de valores relacionados que você não pretende armazenar ou transmitir fora dos limites de método. Você pode criar *tipos anônimos* para essa finalidade. Para obter mais informações, consulte [Tipos anônimos](../classes-and-structs/anonymous-types.md).

Os tipos comuns de valor não podem ter um valor [nulo](../../language-reference/keywords/null.md). No entanto, você pode criar tipos de valor anulável afixando uma `?` após o tipo. Por exemplo, `int?` é um tipo `int` que também pode ter o valor [nulo](../../language-reference/keywords/null.md). Os tipos de valores anuláveis são instâncias do tipo struct genérico <xref:System.Nullable%601?displayProperty=nameWithType>. Os tipos de valor anulável são especialmente úteis quando você está passando dados de e para bancos de dado nos quais valores numéricos podem ser nulos. Para obter mais informações, consulte [tipos de valor anulável](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="related-sections"></a>Seções relacionadas

Para mais informações, consulte os seguintes tópicos:

- [Transmissões e conversões de tipo](./casting-and-type-conversions.md)

- [Conversão boxing e unboxing](./boxing-and-unboxing.md)

- [Usando o tipo dynamic](./using-type-dynamic.md)

- [Tipos de valor](../../language-reference/builtin-types/value-types.md)

- [Tipos de referência](../../language-reference/keywords/reference-types.md)

- [Classes e Structs](../classes-and-structs/index.md)

- [Tipos Anônimos](../classes-and-structs/anonymous-types.md)

- [Genéricos](../generics/index.md)

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../index.md)
- [Conversão de tipos de dados XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Tipos integrais](../../language-reference/builtin-types/integral-numeric-types.md)
