---
title: Usar variação em interfaces para coleções genéricas
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: b762ce42215f9b24371313446637e95962677bfb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375635"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="2d41d-102">Usando variação em interfaces para coleções genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d41d-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>

<span data-ttu-id="2d41d-103">Uma interface de covariante permite que seus métodos retornem mais tipos derivados daquelas especificadas na interface.</span><span class="sxs-lookup"><span data-stu-id="2d41d-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="2d41d-104">Uma interface de contravariante permite que seus métodos aceitem parâmetros de tipos menos derivados do que os especificados na interface.</span><span class="sxs-lookup"><span data-stu-id="2d41d-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>

<span data-ttu-id="2d41d-105">No .NET Framework 4, várias interfaces existentes se tornaram covariantes e contravariantes.</span><span class="sxs-lookup"><span data-stu-id="2d41d-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="2d41d-106">Eles incluem <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="2d41d-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="2d41d-107">Isso permite que você reutilize métodos que operam com coleções genéricas de tipos base para coleções de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="2d41d-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>

<span data-ttu-id="2d41d-108">Para obter uma lista de interfaces variantes na .NET Framework, consulte [variação em interfaces genéricas (Visual Basic)](variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="2d41d-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="converting-generic-collections"></a><span data-ttu-id="2d41d-109">Convertendo coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="2d41d-109">Converting Generic Collections</span></span>

<span data-ttu-id="2d41d-110">O exemplo a seguir ilustra os benefícios do suporte à covariância na interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2d41d-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="2d41d-111">O método `PrintFullName` aceita uma coleção do tipo `IEnumerable(Of Person)` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2d41d-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="2d41d-112">No entanto, você pode reutilizá-lo para uma coleção do tipo `IEnumerable(Of Person)` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="2d41d-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class

' The method has a parameter of the IEnumerable(Of Person) type.
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))
    For Each person As Person In persons
        Console.WriteLine(
            "Name: " & person.FirstName & " " & person.LastName)
    Next
End Sub

Sub Main()
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)

    ' You can pass IEnumerable(Of Employee),
    ' although the method expects IEnumerable(Of Person).

    PrintFullName(employees)

End Sub
```

## <a name="comparing-generic-collections"></a><span data-ttu-id="2d41d-113">Comparando coleções genéricas</span><span class="sxs-lookup"><span data-stu-id="2d41d-113">Comparing Generic Collections</span></span>

<span data-ttu-id="2d41d-114">O exemplo a seguir ilustra os benefícios do suporte à contravariância na interface <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="2d41d-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="2d41d-115">A classe `PersonComparer` implementa a interface `IComparer(Of Person)`.</span><span class="sxs-lookup"><span data-stu-id="2d41d-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="2d41d-116">No entanto, você pode reutilizar essa classe para comparar uma sequência de objetos do tipo `Employee` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="2d41d-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class
' The custom comparer for the Person type
' with standard implementations of Equals()
' and GetHashCode() methods.
Class PersonComparer
    Implements IEqualityComparer(Of Person)

    Public Function Equals1(
        ByVal x As Person,
        ByVal y As Person) As Boolean _
        Implements IEqualityComparer(Of Person).Equals

        If x Is y Then Return True
        If x Is Nothing OrElse y Is Nothing Then Return False
        Return (x.FirstName = y.FirstName) AndAlso
            (x.LastName = y.LastName)
    End Function
    Public Function GetHashCode1(
        ByVal person As Person) As Integer _
        Implements IEqualityComparer(Of Person).GetHashCode

        If person Is Nothing Then Return 0
        Dim hashFirstName =
            If(person.FirstName Is Nothing,
            0, person.FirstName.GetHashCode())
        Dim hashLastName = person.LastName.GetHashCode()
        Return hashFirstName Xor hashLastName
    End Function
End Class

Sub Main()
    Dim employees = New List(Of Employee) From {
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}
    }

    ' You can pass PersonComparer,
    ' which implements IEqualityComparer(Of Person),
    ' although the method expects IEqualityComparer(Of Employee)

    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())

    For Each employee In noduplicates
        Console.WriteLine(employee.FirstName & " " & employee.LastName)
    Next
End Sub
```

## <a name="see-also"></a><span data-ttu-id="2d41d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2d41d-117">See also</span></span>

- [<span data-ttu-id="2d41d-118">Variação em interfaces genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d41d-118">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
