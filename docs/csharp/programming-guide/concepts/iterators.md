---
title: Iteradores (C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 11a606ef18bc497630c0a417488e533a0880056f
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="iterators-c"></a>Iteradores (C#)
Um *iterador* pode ser usado para percorrer coleções, como listas e matrizes.  
  
 Um método iterador ou um acessador `get` realiza uma iteração personalizada em uma coleção. Um método iterador usa a instrução [yield return](../../../csharp/language-reference/keywords/yield.md) para retornar um elemento de cada vez. Quando uma instrução `yield return` for atingida, o local atual no código será lembrado. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Um iterador é consumido no código cliente, usando uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou usando uma consulta LINQ.  
  
 No exemplo a seguir, a primeira iteração do loop `foreach` faz a execução continue no método iterador `SomeNumbers` até que a primeira instrução `yield return` seja alcançada. Essa iteração retorna um valor de 3 e o local atual no método iterador é mantido. Na próxima iteração do loop, a execução no método iterador continuará de onde parou, parando novamente quando alcançar uma instrução `yield return`. Essa iteração retorna um valor de 5 e o local atual no método iterador é mantido novamente. O loop terminará quando o final do método iterador for alcançado.  
  
```csharp  
static void Main()  
{  
    foreach (int number in SomeNumbers())  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 3 5 8  
    Console.ReadKey();  
}  
  
public static System.Collections.IEnumerable SomeNumbers()  
{  
    yield return 3;  
    yield return 5;  
    yield return 8;  
}  
```  
  
 O tipo de retorno de um método iterador ou acessador `get` pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Você pode usar uma instrução `yield break` para encerrar a iteração.  
  
 Os iteradores foram introduzidos no C# no Visual Studio 2005.  
  
 **Neste tópico**  
  
-   [Iterador simples](#BKMK_SimpleIterator)  
  
-   [Criando uma classe de coleção](#BKMK_CollectionClass)  
  
-   [Usando iteradores com uma lista genérica](#BKMK_GenericList)  
  
-   [Informações de sintaxe](#BKMK_SyntaxInformation)  
  
-   [Implementação técnica](#BKMK_Technical)  
  
-   [Uso de iteradores](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Todos os exemplos neste tópico, exceto o exemplo Iterador Simples, incluem diretivas [using](../../../csharp/language-reference/keywords/using-directive.md) para os namespaces `System.Collections` e `System.Collections.Generic`.  
  
##  <a name="BKMK_SimpleIterator"></a> Iterador simples  
 O exemplo a seguir contém uma única instrução `yield return` que está dentro de um loop [for](../../../csharp/language-reference/keywords/for.md). Em `Main`, cada iteração do corpo da instrução `foreach` cria uma chamada à função iteradora, que avança para a próxima instrução `yield return`.  
  
```csharp  
static void Main()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 6 8 10 12 14 16 18  
    Console.ReadKey();  
}  
  
public static System.Collections.Generic.IEnumerable<int>  
    EvenSequence(int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (int number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
##  <a name="BKMK_CollectionClass"></a> Criando uma classe de coleção  
 No exemplo a seguir, a classe `DaysOfTheWeek` implementa a interface <xref:System.Collections.IEnumerable>, que requer um método <xref:System.Collections.IEnumerable.GetEnumerator%2A>. O compilador chama implicitamente o método `GetEnumerator`, que retorna um <xref:System.Collections.IEnumerator>.  
  
 O método `GetEnumerator` retorna cada cadeia de caracteres, uma de cada vez, usando a instrução `yield return`.  
  
```csharp  
static void Main()  
{  
    DaysOfTheWeek days = new DaysOfTheWeek();  
  
    foreach (string day in days)  
    {  
        Console.Write(day + " ");  
    }  
    // Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey();  
}  
  
public class DaysOfTheWeek : IEnumerable  
{  
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };  
  
    public IEnumerator GetEnumerator()  
    {  
        for (int index = 0; index < days.Length; index++)  
        {  
            // Yield each day of the week.  
            yield return days[index];  
        }  
    }  
}  
```  
  
 O exemplo a seguir cria uma classe `Zoo` que contém uma coleção de animais.  
  
 A instrução `foreach`, que faz referência à instância de classe (`theZoo`), chama implicitamente o método `GetEnumerator`. As instruções `foreach`, que fazem referência às propriedades `Birds` e `Mammals`, usam o método iterador nomeado `AnimalsForType`.  
  
```csharp  
static void Main()  
{  
    Zoo theZoo = new Zoo();  
  
    theZoo.AddMammal("Whale");  
    theZoo.AddMammal("Rhinoceros");  
    theZoo.AddBird("Penguin");  
    theZoo.AddBird("Warbler");  
  
    foreach (string name in theZoo)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros Penguin Warbler  
  
    foreach (string name in theZoo.Birds)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Penguin Warbler  
  
    foreach (string name in theZoo.Mammals)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros  
  
    Console.ReadKey();  
}  
  
public class Zoo : IEnumerable  
{  
    // Private members.  
    private List<Animal> animals = new List<Animal>();  
  
    // Public methods.  
    public void AddMammal(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });  
    }  
  
    public void AddBird(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });  
    }  
  
    public IEnumerator GetEnumerator()  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            yield return theAnimal.Name;  
        }  
    }  
  
    // Public members.  
    public IEnumerable Mammals  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }  
    }  
  
    public IEnumerable Birds  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Bird); }  
    }  
  
    // Private methods.  
    private IEnumerable AnimalsForType(Animal.TypeEnum type)  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            if (theAnimal.Type == type)  
            {  
                yield return theAnimal.Name;  
            }  
        }  
    }  
  
    // Private class.  
    private class Animal  
    {  
        public enum TypeEnum { Bird, Mammal }  
  
        public string Name { get; set; }  
        public TypeEnum Type { get; set; }  
    }  
}  
```  
  
##  <a name="BKMK_GenericList"></a> Usando iteradores com uma lista genérica  
 No exemplo a seguir, a classe `Stack(Of T)` genérica implementa a interface genérica <xref:System.Collections.Generic.IEnumerable%601>. O método `Push` atribui valores a uma matriz do tipo `T`. O método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retorna os valores da matriz usando a instrução `yield return`.  
  
 Além do método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genérico, o método <xref:System.Collections.IEnumerable.GetEnumerator%2A> não genérico também deve ser implementado. Isso ocorre porque <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable>. A implementação não genérica adia a implementação genérica.  
  
 O exemplo usa iteradores nomeados para dar suporte a várias maneiras de iterar na mesma coleção de dados. Esses iteradores nomeados são as propriedades `TopToBottom` e `BottomToTop` e o método `TopN`.  
  
 A propriedade `BottomToTop` usa um iterador em um acessador `get`.  
  
```csharp  
static void Main()  
{  
    Stack<int> theStack = new Stack<int>();  
  
    //  Add items to the stack.  
    for (int number = 0; number <= 9; number++)  
    {  
        theStack.Push(number);  
    }  
  
    // Retrieve items from the stack.  
    // foreach is allowed because theStack implements  
    // IEnumerable<int>.  
    foreach (int number in theStack)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    // foreach is allowed, because theStack.TopToBottom  
    // returns IEnumerable(Of Integer).  
    foreach (int number in theStack.TopToBottom)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    foreach (int number in theStack.BottomToTop)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 0 1 2 3 4 5 6 7 8 9  
  
    foreach (int number in theStack.TopN(7))  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey();  
}  
  
public class Stack<T> : IEnumerable<T>  
{  
    private T[] values = new T[100];  
    private int top = 0;  
  
    public void Push(T t)  
    {  
        values[top] = t;  
        top++;  
    }  
    public T Pop()  
    {  
        top--;  
        return values[top];  
    }  
  
    // This method implements the GetEnumerator method. It allows  
    // an instance of the class to be used in a foreach statement.  
    public IEnumerator<T> GetEnumerator()  
    {  
        for (int index = top - 1; index >= 0; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        return GetEnumerator();  
    }  
  
    public IEnumerable<T> TopToBottom  
    {  
        get { return this; }  
    }  
  
    public IEnumerable<T> BottomToTop  
    {  
        get  
        {  
            for (int index = 0; index <= top - 1; index++)  
            {  
                yield return values[index];  
            }  
        }  
    }  
  
    public IEnumerable<T> TopN(int itemsFromTop)  
    {  
        // Return less than itemsFromTop if necessary.  
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;  
  
        for (int index = top - 1; index >= startIndex; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
}  
```  
  
##  <a name="BKMK_SyntaxInformation"></a> Informações de sintaxe  
 Um iterador pode ocorrer como um método ou como um acessador `get`. Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um finalizador estático.  
  
 Deve existir uma conversão implícita do tipo de expressão na instrução `yield return`, para o tipo de retorno do iterador.  
  
 No C#, um método iterador não pode ter nenhum parâmetro `ref` ou `out`.  
  
 No C#, a "yield" não é uma palavra reservada e, só terá um significado especial, quando for usada antes de uma palavra-chave `return` ou `break`.  
  
##  <a name="BKMK_Technical"></a> Implementação técnica  
 Embora você escreva um iterador como um método, o compilador o traduz em uma classe aninhada que é, na verdade, uma máquina de estado. Essa classe mantém o controle da posição do iterador enquanto o loop `foreach` no código cliente continuar.  
  
 Para ver o que o compilador faz, você pode usar a ferramenta Ildasm.exe para exibir o código Microsoft Intermediate Language que é gerado para um método iterador.  
  
 Quando você cria um iterador para uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), não é necessário implementar toda a interface <xref:System.Collections.IEnumerator>. Quando o compilador detecta o iterador, ele gera automaticamente os métodos `Current`, `MoveNext` e `Dispose` da interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 A cada iteração sucessiva do loop `foreach` (ou a chamada direta ao `IEnumerator.MoveNext`), o próximo corpo de código do iterador continua, depois da instrução `yield return` anterior. Em seguida, ele continuará até a próxima instrução `yield return`, até que o final do corpo do iterador seja alcançado ou até que uma instrução `yield break` seja encontrada.  
  
 Iteradores não dão suporte ao método <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>. Para iterar novamente desde o início, você deve obter um novo iterador.  
  
 Para obter informações adicionais, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Uso de iteradores  
 Os iteradores permitem que você mantenha a simplicidade de um loop `foreach` quando for necessário usar um código complexo para preencher uma sequência de lista. Isso pode ser útil quando você quiser fazer o seguinte:  
  
-   Modificar a sequência de lista após a primeira iteração de loop `foreach`.  
  
-   Evitar o carregamento completo de uma grande lista antes da primeira iteração de um loop `foreach`. Um exemplo é uma busca paginada para carregar um lote de linhas da tabela. Outro exemplo é o método <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, que implementa os iteradores dentro do .NET Framework.  
  
-   Encapsular a criação da lista no iterador. No método iterador, você pode criar a lista e, em seguida, gerar cada resultado em um loop.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [yield](../../../csharp/language-reference/keywords/yield.md)   
 [Usando foreach com matrizes](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)   
 [Genéricos](../../../csharp/programming-guide/generics/index.md)
