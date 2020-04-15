---
title: Escrever um código C# seguro e eficiente
description: Aprimoramentos recentes na linguagem C# permitem escrever código seguro verificável que o desempenho associou anteriormente ao código não seguro.
ms.date: 03/17/2020
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: dc697d822c4d471d2b67ce074ab9af8fc2724b23
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389675"
---
# <a name="write-safe-and-efficient-c-code"></a>Escrever um código C# seguro e eficiente

Novos recursos em C# permitem escrever código seguro verificável com melhor desempenho. Se você aplicar essas técnicas com cuidado, menos cenários exigirão código não seguro. Esses recursos tornam fácil usar referências a tipos de valor como argumentos e retornos de método. Quando realizadas com segurança, essas técnicas minimizam a cópia de tipos de valor. Usando tipos de valor, é possível minimizar a quantidade de alocações e passagens de coleta de lixo.

Grande parte do código de exemplo neste artigo usa recursos adicionados no C# 7.2. Para usar esses recursos, é necessário configurar seu projeto para usar o C# 7.2 ou posterior. Para obter mais informações sobre a definição da versão do idioma, consulte [configurar a versão do idioma](language-reference/configure-language-version.md).

Este artigo se concentra em técnicas para o gerenciamento eficiente de recursos. Uma vantagem de usar tipos de valor é que eles geralmente evitam alocações de heap. A desvantagem é que eles são copiados por valor. Essa troca torna mais difícil otimizar algoritmos que operam em grandes quantidades de dados. Os novos recursos de linguagem no C# 7.2 oferecem mecanismos que habilitam o código eficiente seguro que usa referências para tipos de valor. Use esses recursos criteriosamente para minimizar tanto as alocações quanto as operações de cópia. Este artigo explora esses novos recursos.

Este artigo se concentra nas seguintes técnicas de gerenciamento de recursos:

- Declare [`readonly struct`](language-reference/builtin-types/struct.md#readonly-struct) a para expressar que um tipo é **imutável**. Isso permite que o compilador salve [`in`](language-reference/keywords/in-parameter-modifier.md) cópias defensivas ao usar parâmetros.
- Se um tipo não puder ser imutável, declare `struct` os membros [`readonly`](language-reference/builtin-types/struct.md#readonly-instance-members) para indicar que o membro não modifica o estado.
- Use [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) um retorno quando o `struct` valor <xref:System.IntPtr.Size?displayProperty=nameWithType> de retorno for maior do que e a vida útil do armazenamento for maior do que o método que devolve o valor.
- Quando o tamanho de um `readonly struct` é maior que <xref:System.IntPtr.Size?displayProperty=nameWithType>, você deve passá-lo como um parâmetro `in` por motivos de desempenho.
- Nunca passe `struct` um `in` como parâmetro a menos que `readonly` seja declarado com `readonly` o modificador ou o método chama apenas os membros da estrutura. Violar essa orientação pode afetar negativamente o desempenho e pode levar a um comportamento obscuro.
- Use [`ref struct`](language-reference/keywords/ref.md#ref-struct-types)um , `readonly ref struct` ou <xref:System.Span%601> <xref:System.ReadOnlySpan%601> um tal como ou para trabalhar com a memória como uma seqüência de bytes.

Essas técnicas forçam você a equilibrar duas metras concorrentes em relação às **referências** e aos **valores**. As variáveis que são [tipos de referência](programming-guide/types/index.md#reference-types) mantêm uma referência ao local na memória. As variáveis que são [tipos de valor](programming-guide/types/index.md#value-types) contêm diretamente seu valor. Essas diferenças realçam as principais diferenças que são importantes para gerenciar recursos de memória. Normalmente, os **tipos de valor** são copiados quando passados para um método ou retornados de um método. Esse comportamento inclui copiar o valor do `this` ao chamar membros de um tipo de valor. O custo da cópia está relacionado ao tamanho do tipo. Os **tipos de referência** são alocados no heap gerenciado. Cada novo objeto requer uma nova alocação e, subsequentemente, deve ser recuperado. Ambas as operações levam tempo. A referência é copiada quando um tipo de referência é passado como um argumento para um método ou retornado de um método.

Este artigo usa o seguinte exemplo de conceito da estrutura de ponto 3D para explicar estas recomendações:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

diferentes exemplos usam diferentes implementações deste conceito.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Declarar structs somente leitura para tipos de valor imutáveis

Declarar um `struct` usando o modificador `readonly` informa ao compilador que sua intenção é criar um tipo imutável. O compilador impõe essa decisão de design com as seguintes regras:

- Todos os membros do campo devem ser `readonly`
- Todas as propriedades devem ser somente leitura, incluindo propriedades autoimplementadas.

Essas duas regras são suficientes para garantir que nenhum membro de um `readonly struct` modifica o estado desse struct. O `struct` é imutável. A estrutura `Point3D` pode ser definida como um struct imutável, conforme mostrado no exemplo a seguir:

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

Siga esta recomendação sempre que sua intenção de design for criar um tipo de valor imutável. Quaisquer melhorias no desempenho são um benefício adicional. O `readonly struct` expressa claramente a intenção do design.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Declare membros somente leitura quando uma estrutura não pode ser imutável

Em C# 8.0 e posteriormente, quando um tipo de estrutura é mutável, `readonly`você deve declarar membros que não causam mutação para ser . Considere uma aplicação diferente que precise de uma estrutura de ponto 3D, mas que deve suportar mutabilidade. A versão a seguir da estrutura `readonly` de ponto 3D adiciona o modificador apenas aos membros que não modificam a estrutura. Siga este exemplo quando seu design deve suportar modificações na estrutura por alguns membros, mas você ainda quer os benefícios de aplicar a leitura apenas em alguns membros:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

A amostra anterior mostra muitos dos locais `readonly` onde você pode aplicar o modificador: métodos, propriedades e acessórios de propriedade. Se você usar propriedades implementadas automaticamente, `readonly` o compilador `get` adicionará o modificador ao acessório para propriedades de leitura e gravação. O compilador adiciona `readonly` o modificador às declarações de propriedade `get` implementadas automaticamente para propriedades com apenas um acessório.

Adicionar `readonly` o modificador a membros que não sofrem mutação de estado fornece dois benefícios relacionados. Primeiro, o compilador reforça sua intenção. Esse membro não pode alterar o estado da estrutura. Em segundo lugar, o compilador não `in` criará cópias defensivas de parâmetros ao acessar um `readonly` membro. O compilador pode fazer essa otimização com `struct` segurança porque garante `readonly` que o não é modificado por um membro.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Use instruções `ref readonly return` para grandes estruturas, quando possível

É possível retornar valores por referência quando o valor que está sendo retornado não é local para o método de retorno. Retornar por referência significa que somente a referência é copiada, não a estrutura. No exemplo a seguir, a propriedade `Origin` não pode usar um retorno `ref`, porque o valor que está sendo retornado é uma variável local:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

No entanto, a seguinte definição de propriedade pode ser retornada por referência, porque o valor retornado é um membro estático:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Você não deseja chamadores que modificam a origem, então deve retornar o valor por `ref readonly`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Retornar `ref readonly` permite que você salvar a cópia de estruturas maiores e preserve a imutabilidade de seus membros de dados internos.

No site de chamada, os chamadores fazem a opção de usar a propriedade `Origin` como um `ref readonly` ou como um valor:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

A primeira atribuição no código anterior faz uma cópia da constante `Origin` e atribui essa cópia. A segunda atribui uma referência. Observe que o modificador `readonly` deve ser parte da declaração da variável. A referência à qual ele se relaciona não pode ser modificada. As tentativas de modificá-la resultam em um erro em tempo de compilação.

O modificador `readonly` é necessário na declaração de `originReference`.

O compilador impõe que o autor da chamada não pode modificar a referência. As tentativas de atribuir o valor diretamente geram um erro em tempo de compilação. No entanto, o compilador não pode saber se algum método de membro modifica o estado do struct.
Para garantir que o objeto não será modificado, o compilador cria uma cópia e chama as referências de membro usando essa cópia. Todas as modificações são para essa cópia de defesa.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Aplique o modificador `in` a parâmetros `readonly struct` maiores que `System.IntPtr.Size`

A palavra-chave `in` complementa as palavras-chave `ref` e `out` existentes para passar argumentos por referência. A palavra-chave `in` especifica a passagem do argumento por referência, mas o método chamado não modifica o valor.

Essa adição fornece um vocabulário completo para expressar sua intenção de design.
Os tipos de valor são copiados no momento em que são passados para um método chamado quando você não especifica nenhum dos modificadores a seguir na assinatura do método. Cada um desses modificadores especifica que uma variável é passada por referência, evitando a cópia. Cada modificador expressa uma intenção diferente:

- `out`: esse método define o valor do argumento usado como este parâmetro.
- `ref`: esse método pode definir o valor do argumento usado como este parâmetro.
- `in`: Este método não modifica o valor do argumento usado como parâmetro.

Adicione o modificador `in` para passar um argumento por referência e declare que sua intenção de design é passar argumentos por referência para evitar cópias desnecessárias. Você não pretende modificar o objeto usado como esse argumento.

Essa prática geralmente melhora o desempenho para tipos de valor somente leitura que são maiores que <xref:System.IntPtr.Size?displayProperty=nameWithType>. Para tipos simples (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` e `bool`, e tipos `enum`), eventuais ganhos no desempenho são mínimos. Na verdade, o desempenho pode ser degradado usando a passagem por referência para tipos menores que <xref:System.IntPtr.Size?displayProperty=nameWithType>.

O código a seguir mostra um exemplo de um método que calcula a distância entre dois pontos no espaço 3D.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Os argumentos são duas estruturas que contêm três duplas. Uma dupla tem 8 bytes. Então, cada argumento tem 24 bytes. Ao especificar o modificador `in`, você passa uma referência de 4 ou 8 bytes para esses argumentos, dependendo da arquitetura do computador. A diferença no tamanho é pequena, mas ela aumenta rapidamente quando o aplicativo chama esse método em um loop estreito, usando muitos valores diferentes.

O modificador `in` complementa `out` e `ref` de outras formas também. Não é possível criar sobrecargas de um método que diferem somente na presença de `in`, `out` ou `ref`. Essas novas regras apresentam o mesmo comportamento que sempre foi definido para os parâmetros `out` e `ref`. Como os modificadores `out` e `ref`, os tipos de valor não estão demarcados, porque o modificador `in` é aplicado.

O modificador `in` pode ser aplicado a qualquer membro que usa os seguintes parâmetros: métodos, delegados, lambdas, funções locais, indexadores e operadores.

Outro recurso dos parâmetros `in` é que você pode usar valores literais ou constantes para o argumento para um parâmetro `in`. Além disso, ao contrário de um parâmetro `ref` ou `out`, você não precisa aplicar o modificador `in` no local da chamada. O código a seguir mostra dois exemplos para chamar o método `CalculateDistance`. O primeiro usa duas variáveis locais transmitidas por referência. O segundo inclui uma variável temporária criada como parte da chamada de método.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Há várias maneiras pelas quais um compilador impõe a natureza somente leitura de um argumento `in`.  Em primeiro lugar, o método chamado não pode ser atribuído diretamente a um parâmetro `in`. Não é possível atribuí-lo diretamente a nenhum campo de um parâmetro `in` quando esse valor é um tipo `struct`. Além disso, não é possível passar um parâmetro `in` para nenhum método usando o modificador `ref` ou `out`.
Essas regras se aplicam a qualquer campo de um parâmetro `in`, considerando que o campo seja um tipo `struct` e o parâmetro também seja um tipo `struct`. Na verdade, essas regras são aplicadas a várias camadas de acesso de membro, considerando que os tipos, em todos os níveis de acesso de membro, sejam `structs`.
O compilador impõe que os tipos `struct` passados como argumentos `in` e seus membros `struct` sejam variáveis somente leitura quando usados como argumentos para outros métodos.

O uso de parâmetros `in` pode evitar os possíveis custos de desempenho com a realização de cópias. Isso não altera a semântica de nenhuma chamada de método. Portanto, não é necessário especificar o modificador `in` no site de chamada. A omissão do modificador `in` no site de chamada informa ao compilador que ele tem permissão para fazer uma cópia do argumento pelos seguintes motivos:

- Existe uma conversão implícita, mas não uma conversão de identidade do tipo de argumento no tipo de parâmetro.
- O argumento é uma expressão, mas não tem uma variável de armazenamento conhecida.
- Há uma sobrecarga que é distinguível pela presença ou ausência de `in`. Nesse caso, a sobrecarga pelo valor é uma correspondência melhor.

Essas regras são úteis conforme você atualiza o código existente para usar argumentos de referência somente leitura. Dentro do método chamado, você pode chamar qualquer método de instância que use parâmetros por valor. Nessas instâncias, uma cópia do parâmetro `in` é criada. Uma vez que o compilador pode criar uma variável temporária para qualquer parâmetro `in`, você também pode especificar valores padrão para qualquer parâmetro `in`. O código a seguir especifica a origem (ponto 0,0) como o valor padrão para o segundo ponto:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Para forçar o compilador a passar argumentos somente leitura por referência, especifique o modificador `in` nos argumentos no site de chamada, conforme mostrado no código a seguir:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Esse comportamento facilita a adoção de parâmetros `in` ao longo do tempo nas grandes bases de código em que os ganhos de desempenho são possíveis. Primeiro você adiciona o modificador `in` às assinaturas de método. Em seguida, você adiciona o modificador `in` em sites de chamada e cria tipos `readonly struct` para que o compilador evite criar cópias de defesa de parâmetros `in` em mais locais.

A designação do parâmetro `in` também pode ser usada com tipos de referência ou valores numéricos. No entanto, os benefícios em ambos os casos serão mínimos, se houver.

## <a name="avoid-mutable-structs-as-an-in-argument"></a>Evite estruturas mutáveis como `in` argumento

As técnicas descritas acima explicam como evitar cópias retornando referências e passando valores por referência. Essas técnicas funcionam melhor quando os tipos de argumento são declarados como tipos `readonly struct`. Caso contrário, o compilador deve criar **cópias de defesa** em muitas situações, para impor a qualidade de somente leitura de quaisquer argumentos. Considere o exemplo a seguir que calcula a distância de um ponto 3D da origem:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

A estrutura `Point3D`*não* é um struct somente leitura. Há seis chamadas de acesso de propriedade diferentes no corpo deste método. No primeiro exame, você pode ter achado que esses acessos estavam seguros. No fim das contas, um acessador `get` não deve modificar o estado do objeto. Mas não há nenhuma regra de linguagem que impõe isso. É apenas uma convenção comum. Qualquer tipo pode implementar um acessador `get` que modificou o estado interno. Sem alguma garantia de idioma, o compilador deve criar uma cópia `readonly` temporária do argumento antes de chamar qualquer membro não marcado com o modificador. O armazenamento temporário é criado na pilha, os valores do argumento são copiados para o armazenamento temporário e o valor é copiado para a pilha para cada acesso de membro como o argumento `this`. Em muitas situações, essas cópias prejudicam o desempenho suficiente para que o pass-by-value `readonly struct` seja mais rápido do que `readonly`a referência de leitura de passagem por leitura quando o tipo de argumento não é um e o método chama membros que não são marcados . Se você marcar todos os métodos que não `readonly`modificam o estado de estrutura como , o compilador pode determinar com segurança que o estado de estrutura não é modificado, e uma cópia defensiva não é necessária.

Em vez disso, se o cálculo da distância `ReadonlyPoint3D`usar a estrutura imutável, objetos temporários não são necessários:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

O compilador gera um código mais eficiente `readonly struct`quando `this` você chama membros de a : `in` A referência, em vez de uma cópia do receptor, é sempre um parâmetro passado por referência ao método do membro. Essa otimização economiza cópias quando você usa um `readonly struct` como um argumento `in`.

Você não deve passar um tipo `in` de valor nulo como argumento. O <xref:System.Nullable%601> tipo não é declarado como uma estrutura somente leitura. Isso significa que o compilador deve gerar cópias defensivas para qualquer argumento de tipo de valor anulável passado para um método usando o modificador `in` na declaração de parâmetro.

Você pode ver um programa de exemplo que demonstra as diferenças de desempenho usando [benchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) em nosso [repositório de amostras](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) no GitHub. Ele compara a passagem de um struct mutável por valor e por referência com a passagem de um struct imutável por valor e por referência. O uso do struct imutável e da passagem por referência é mais rápido.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Use tipos `ref struct` para trabalhar com blocos ou memória em um único registro de ativação

Um recurso de linguagem relacionado é a capacidade de declarar um tipo de valor que deve ser restrito para um único registro de ativação. Essa restrição permite que o compilador faça várias otimizações. A principal motivação para esse recurso foi <xref:System.Span%601> e as estruturas relacionadas. Você obterá melhorias de desempenho com esses aprimoramentos usando APIs do .NET novas e atualizadas que fazem uso do tipo <xref:System.Span%601>.

Você pode ter requisitos semelhantes [`stackalloc`](language-reference/operators/stackalloc.md) trabalhando com memória criada usando ou ao usar memória de APIs interop. Você pode definir seus próprios tipos `ref struct` para essas necessidades.

## <a name="readonly-ref-struct-type"></a>Tipo`readonly ref struct`

A declaração de um struct como `readonly ref` combina os benefícios e as restrições das declarações `ref struct` e `readonly struct`. A memória usada pelo alcance somente leitura está restrita a um único registro de ativação, e a memória usada pelo alcance de somente leitura não pode ser modificada.

## <a name="conclusions"></a>Conclusões

Usar tipos de valor minimiza o número de operações de alocação:

- o armazenamento para tipos de valor é alocado em pilhas para variáveis locais e argumentos de método.
- o armazenamento para tipos de valor que são membros de outros objetos é alocado como parte desse objeto, não como uma alocação separada.
- o armazenamento para valores retornados de tipo de valor é alocado em pilhas.

Compare isso com tipos de referência nestas mesmas situações:

- o armazenamento para tipos de referência é alocado em heap para variáveis locais e argumentos de método. A referência é armazenada na pilha.
- O armazenamento para tipos de referência que são membros de outros objetos são alocados separadamente no heap. O objeto recipiente armazena a referência.
- O armazenamento para valores retornados de tipo de referência é alocado em heap. A referência a esse armazenamento é armazenada na pilha.

Minimizar alocações implica compensações. Você copia mais memória quando o tamanho do `struct` é maior que o tamanho de uma referência. Normalmente, uma referência é 64 ou 32 bits e depende da CPU do computador de destino.

Essas compensações geralmente têm o mínimo de impacto no desempenho. No entanto, para estruturas grandes ou coleções maiores, o impacto no desempenho aumenta. O impacto pode ser grande em loops estreitos e em afunilamentos para programas.

Esses aprimoramentos na linguagem C# são criados para algoritmos de desempenho críticos, nos quais as alocações de memória são um importante fator para alcançar o desempenho necessário. Você pode achar que geralmente não usa esses recursos no código que grava. No entanto, esses aprimoramentos foram adotados por meio do .NET. À medida que cada vez mais APIs utilizam esses recursos, você verá o desempenho dos seus aplicativos melhorar.

## <a name="see-also"></a>Confira também

- [ref keyword](language-reference/keywords/ref.md)
- [Ref returns e ref locals](programming-guide/classes-and-structs/ref-returns.md)
