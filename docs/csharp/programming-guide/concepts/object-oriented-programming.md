---
title: Programação orientada a objeto (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627884"
---
# <a name="object-oriented-programming-c"></a>Programação orientada a objetos (C#)

O C# dá suporte completo à programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.

- *Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.
- *Herança* descreve a capacidade de criar novas classes com base em uma classe existente.
- *Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.

## <a name="classes-and-objects"></a>Classes e objetos

Os termos *classe* e *objeto* descrevem o *tipo* de objetos e as *instâncias* das classes, respectivamente. Sendo assim, o ato de criar um objeto é chamado de *instanciação*. Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.

Para definir uma classe:

```csharp
class SampleClass
{
}
```

C# também fornece tipos chamados *estruturas* que são úteis quando você não precisa de suporte para herança ou polimorfismo.

Para definir uma estrutura:

```csharp
struct SampleStruct
{
}
```

Para obter mais informações, consulte os artigos sobre a [classe](../../language-reference/keywords/class.md) e [struct](../../language-reference/builtin-types/struct.md) palavras-chave.

### <a name="class-members"></a>Membros de classe

Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.

#### <a name="properties-and-fields"></a>Propriedades e campos

Os campos e as propriedades representam as informações que um objeto contém. Os campos são como variáveis porque podem ser lidos ou definidos diretamente, sujeitos aos modificadores de acesso aplicáveis.

Para definir um campo que pode ser acessado a partir de instâncias da classe:

```csharp
public class SampleClass
{
    string sampleField;
}
```

As `get` propriedades `set` possuem e acessórios, que fornecem mais controle sobre como os valores são definidos ou devolvidos.

C# permite que você crie um campo privado para armazenar o valor da propriedade ou use propriedades auto-implementadas que criam esse campo automaticamente nos bastidores e forneçam a lógica básica para os procedimentos de propriedade.

Para definir uma propriedade autoimplementada:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade. No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas. No C#, é possível omitir o método de propriedade `get` ou `set`. No entanto, as propriedades implementadas automaticamente não podem ser somente gravação. As propriedades auto-implementadas somente leitura podem ser definidas em construtores da classe de contenção.

Para obter mais informações, consulte:

- [get](../../language-reference/keywords/get.md)

- [Definir](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Métodos

Um *método* é uma ação que um objeto pode executar.

Para definir um método de uma classe:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.

Para sobrecarregar um método:

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

Na maioria dos casos, você declara um método dentro de uma definição de classe. No entanto, o C# também dá suporte a *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.

Para obter mais informações, consulte:

- [Métodos](../classes-and-structs/methods.md)
- [Métodos de extensão](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Construtores

Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado. Os construtores normalmente inicializam os membros de dados do novo objeto. Um construtor pode ser executado apenas uma vez quando uma classe é criada. Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe. No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.

Para definir um construtor para uma classe:

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Para saber mais, veja [Construtores](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Finalizadores

Finalizadores são usados para destruir instâncias de classes. No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo. No entanto, talvez ainda seja necessário usar os finalizadores para limpar recursos não gerenciados que seu aplicativo criar. Pode haver apenas um finalizador para uma classe.

Para obter mais informações sobre os finalizadores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Eventos

Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer. A classe que envia (ou levanta) o evento é chamada *de editora* e as classes que recebem (ou lidam) com o evento são chamadas *de assinantes*. Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).

- Para declarar um evento em uma classe, use a palavra-chave [event](../../language-reference/keywords/event.md).

- Para acionar um evento, invoque o delegado do evento.

- Para assinar um evento, use o operador `+=`; para cancelar a assinatura de um evento, use o operador `-=`.

#### <a name="nested-classes"></a>Aulas aninhadas

Uma classe definida dentro de outra classe é chamada de *aninhada*. Por padrão, a classe aninhada é particular.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modificadores de acesso e níveis de acesso

Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.

Os modificadores de acesso a seguir estão disponíveis:

|Modificador de C#|Definição|
|------------------|----------------|
|[público](../../language-reference/keywords/public.md)|O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.|
|[Privada](../../language-reference/keywords/private.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe.|
|[Protegido](../../language-reference/keywords/protected.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.|
|[Interno](../../language-reference/keywords/internal.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.|
|[private protected](../../language-reference/keywords/private-protected.md)|O tipo ou membro pode ser acessado pelo código na mesma classe ou em uma classe derivada no assembly da classe base.|

Para obter mais informações, consulte [Modificadores de Acesso](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Aulas de instantiva

Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.

```csharp
SampleClass sampleObject = new SampleClass();
```

Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Para obter mais informações, consulte:

- [novo Operador](../../language-reference/operators/new-operator.md)
- [Inicializadores de objeto e coleção](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Classes e membros estáticos

Um membro estático da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.

Para definir um membro estático:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Para acessar o membro estático, use o nome da classe sem criar um objeto dessa classe:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Classes estáticas em C# têm apenas membros estáticos e não podem ser instanciadas. Membros estáticos também não podem acessar propriedades, métodos ou campos não estáticos

Para obter mais informações, consulte [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Tipos anônimos

Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.

Para criar uma instância de um tipo anônimo:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Para obter mais informações, consulte: [Tipos Anônimos](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Herança

A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes. A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*. No entanto, todas as classes em C# herdam implicitamente da classe <xref:System.Object> que dá suporte à hierarquia de classes do .NET e fornece serviços de nível baixo para todas as classes.

> [!NOTE]
> O C# não dá suporte a várias heranças. Ou seja, você pode especificar apenas uma classe base para uma classe derivada.

Para herdar de uma classe base:

```csharp
class DerivedClass:BaseClass {}
```

Por padrão, todas as classes podem ser herdadas. No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.

Para especificar que uma classe não pode ser usada como classe base:

```csharp
public sealed class A { }
```

Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:

```csharp
public abstract class B { }
```

Para obter mais informações, consulte:

- [sealed](../../language-reference/keywords/sealed.md)

- [Abstrata](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Substituindo membros

Por padrão, uma classe derivada herda todos os membros de sua classe base. Se quiser alterar o comportamento do membro herdado, você precisa substituí-la. Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.

Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:

|Modificador de C#|Definição|
|------------------|----------------|
|[Virtual](../../language-reference/keywords/virtual.md)|Permite que um membro de classe seja substituído em uma classe derivada.|
|[Substituir](../../language-reference/keywords/override.md)|Substitui um membro virtual (substituível) definido na classe base.|
|[Abstrata](../../language-reference/keywords/abstract.md)|Requer que um membro de classe seja substituído na classe derivada.|
|[Modificador new](../../language-reference/keywords/new-modifier.md)|Oculta um membro herdado de uma classe base|

## <a name="interfaces"></a>Interfaces

Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos. Mas, diferente das classes, as interfaces não fornecem implementação. Elas são implementadas por classes e definidas como entidades separadas das classes. Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.

Para definir uma interface:

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Para implementar uma interface em uma classe:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Para obter mais informações, consulte o artigo do guia de programação sobre [Interfaces](../interfaces/index.md) e o artigo de referência de idioma sobre a palavra-chave da [interface.](../../language-reference/keywords/interface.md)

## <a name="generics"></a>Genéricos

Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem tipos de objetos que podem armazenar ou usar. O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.

Para definir uma classe genérica:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Para criar uma instância de uma classe genérica:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Para obter mais informações, consulte:

- [Genéricos](../../../standard/generics/index.md)

- [Genéricos](../generics/index.md)

## <a name="delegates"></a>Delega

Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível. Você pode invocar (ou chamar) o método através do delegado. Delegados são usados para passar métodos como argumentos a outros métodos.

> [!NOTE]
> Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).

Para criar um delegado:

```csharp
public delegate void SampleDelegate(string str);
```

Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

Para obter mais informações, consulte o artigo do guia de programação sobre [Delegados](../delegates/index.md) e o artigo de referência da linguagem sobre a palavra-chave [delegado.](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
