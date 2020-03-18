---
title: Usando variação em interfaces para Coleções Genéricas (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: b891ccde93e18baf5d5e814911666e9c6268e009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169734"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="b2ff2-102">Usando variação em interfaces para Coleções Genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="b2ff2-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="b2ff2-103">Uma interface de covariante permite que seus métodos retornem mais tipos derivados daquelas especificadas na interface.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="b2ff2-104">Uma interface de contravariante permite que seus métodos aceitem parâmetros de tipos menos derivados do que os especificados na interface.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="b2ff2-105">No .NET Framework 4, várias interfaces existentes se tornaram covariantes e contravariantes.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="b2ff2-106">Eles incluem <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="b2ff2-107">Isso permite que você reutilize métodos que operam com coleções genéricas de tipos base para coleções de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="b2ff2-108">Para obter uma lista de interfaces variantes no .NET Framework, consulte [Variação em interfaces genéricas (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b2ff2-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="b2ff2-109">Convertendo coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="b2ff2-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="b2ff2-110">O exemplo a seguir ilustra os benefícios do suporte à covariância na interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="b2ff2-111">O método `PrintFullName` aceita uma coleção do tipo `IEnumerable<Person>` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="b2ff2-112">No entanto, você pode reutilizá-lo para uma coleção do tipo `IEnumerable<Employee>` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="b2ff2-113">Comparando coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="b2ff2-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="b2ff2-114">O exemplo a seguir ilustra os benefícios do suporte à contravariância na interface <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="b2ff2-115">A classe `PersonComparer` implementa a interface `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="b2ff2-116">No entanto, você pode reutilizar essa classe para comparar uma sequência de objetos do tipo `Employee` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="b2ff2-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2ff2-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="b2ff2-117">See also</span></span>

- [<span data-ttu-id="b2ff2-118">Variância em interfaces genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="b2ff2-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
