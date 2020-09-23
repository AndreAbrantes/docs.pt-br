---
title: Declaração de variável do objeto
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 74b1401df3dbb2d744de74734d10cbcd92e9689e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077040"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="772a0-102">Declaração de variável do objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="772a0-102">Object Variable Declaration (Visual Basic)</span></span>

<span data-ttu-id="772a0-103">Você usa uma instrução de declaração normal para declarar uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="772a0-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="772a0-104">Para o tipo de dados, você especifica `Object` (ou seja, o [tipo de dados Object](../../../language-reference/data-types/object-data-type.md)) ou uma classe mais específica da qual o objeto deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="772a0-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="772a0-105">Declarar uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="772a0-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="772a0-106">Quando você declara uma variável com uma classe de objeto específica, ela pode acessar todos os métodos e propriedades expostos por essa classe e as classes das quais ela é herdada.</span><span class="sxs-lookup"><span data-stu-id="772a0-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="772a0-107">Se você declarar a variável com <xref:System.Object> , ela poderá acessar somente os membros da <xref:System.Object> classe, a menos que você mude `Option Strict Off` para permitir associação tardia.</span><span class="sxs-lookup"><span data-stu-id="772a0-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="772a0-108">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="772a0-108">Declaration Syntax</span></span>  

 <span data-ttu-id="772a0-109">Use a sintaxe a seguir para declarar uma variável de objeto:</span><span class="sxs-lookup"><span data-stu-id="772a0-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="772a0-110">Você também pode especificar [público](../../../language-reference/modifiers/public.md), [protegido](../../../language-reference/modifiers/protected.md), [amigo](../../../language-reference/modifiers/friend.md), `Protected Friend` [privado](../../../language-reference/modifiers/private.md), [compartilhado](../../../language-reference/modifiers/shared.md)ou [estático](../../../language-reference/modifiers/static.md) na declaração.</span><span class="sxs-lookup"><span data-stu-id="772a0-110">You can also specify [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md), or [Static](../../../language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="772a0-111">As seguintes declarações de exemplo são válidas:</span><span class="sxs-lookup"><span data-stu-id="772a0-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="772a0-112">Associação tardia e Associação antecipada</span><span class="sxs-lookup"><span data-stu-id="772a0-112">Late Binding and Early Binding</span></span>  

 <span data-ttu-id="772a0-113">Às vezes, a classe específica é desconhecida até que seu código seja executado.</span><span class="sxs-lookup"><span data-stu-id="772a0-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="772a0-114">Nesse caso, você deve declarar a variável de objeto com o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="772a0-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="772a0-115">Isso cria uma referência geral para qualquer tipo de objeto e a classe específica é atribuída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="772a0-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="772a0-116">Isso é chamado de *associação tardia*.</span><span class="sxs-lookup"><span data-stu-id="772a0-116">This is called *late binding*.</span></span> <span data-ttu-id="772a0-117">A associação tardia requer tempo de execução adicional.</span><span class="sxs-lookup"><span data-stu-id="772a0-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="772a0-118">Ele também limita seu código aos métodos e às propriedades da classe que você atribuiu mais recentemente a ele.</span><span class="sxs-lookup"><span data-stu-id="772a0-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="772a0-119">Isso pode causar erros de tempo de execução se o seu código tentar acessar membros de uma classe diferente.</span><span class="sxs-lookup"><span data-stu-id="772a0-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="772a0-120">Quando você conhece a classe específica em tempo de compilação, deve declarar a variável de objeto para ser dessa classe.</span><span class="sxs-lookup"><span data-stu-id="772a0-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="772a0-121">Isso é chamado de *associação inicial*.</span><span class="sxs-lookup"><span data-stu-id="772a0-121">This is called *early binding*.</span></span> <span data-ttu-id="772a0-122">A ligação antecipada melhora o desempenho e garante o acesso do código a todos os métodos e propriedades da classe específica.</span><span class="sxs-lookup"><span data-stu-id="772a0-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="772a0-123">Nas declarações de exemplo anteriores, se Variable `objA` usar somente objetos da classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , você deverá especificar `As System.Windows.Forms.Label` em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="772a0-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="772a0-124">Vantagens da associação inicial</span><span class="sxs-lookup"><span data-stu-id="772a0-124">Advantages of Early Binding</span></span>  

 <span data-ttu-id="772a0-125">Declarar uma variável de objeto como uma classe específica oferece várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="772a0-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="772a0-126">Verificação automática de tipo</span><span class="sxs-lookup"><span data-stu-id="772a0-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="772a0-127">Acesso garantido a todos os membros da classe específica</span><span class="sxs-lookup"><span data-stu-id="772a0-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="772a0-128">Suporte do Microsoft IntelliSense no editor de códigos</span><span class="sxs-lookup"><span data-stu-id="772a0-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="772a0-129">Melhor legibilidade do seu código</span><span class="sxs-lookup"><span data-stu-id="772a0-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="772a0-130">Menos erros em seu código</span><span class="sxs-lookup"><span data-stu-id="772a0-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="772a0-131">Erros capturados em tempo de compilação em vez de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="772a0-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="772a0-132">Execução de código mais rápida</span><span class="sxs-lookup"><span data-stu-id="772a0-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="772a0-133">Acesso a membros de variável de objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-133">Access to Object Variable Members</span></span>  

 <span data-ttu-id="772a0-134">Quando `Option Strict` é ativado `On` , uma variável de objeto pode acessar somente os métodos e as propriedades da classe com a qual você o declara.</span><span class="sxs-lookup"><span data-stu-id="772a0-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="772a0-135">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="772a0-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="772a0-136">Neste exemplo, `p` o pode usar somente os membros da <xref:System.Object> própria classe, que não incluem a `Left` propriedade.</span><span class="sxs-lookup"><span data-stu-id="772a0-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="772a0-137">Por outro lado, `q` foi declarado como de tipo <xref:System.Windows.Forms.Label> , portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label> classe no <xref:System.Windows.Forms> namespace.</span><span class="sxs-lookup"><span data-stu-id="772a0-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="772a0-138">Flexibilidade de variáveis de objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-138">Flexibility of Object Variables</span></span>  

 <span data-ttu-id="772a0-139">Ao trabalhar com objetos em uma hierarquia de herança, você tem a opção de qual classe usar para declarar suas variáveis de objeto.</span><span class="sxs-lookup"><span data-stu-id="772a0-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="772a0-140">Ao fazer essa escolha, você deve balancear a flexibilidade da atribuição de objeto contra o acesso a membros de uma classe.</span><span class="sxs-lookup"><span data-stu-id="772a0-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="772a0-141">Por exemplo, considere a hierarquia de herança que leva à <xref:System.Windows.Forms.Form?displayProperty=nameWithType> classe:</span><span class="sxs-lookup"><span data-stu-id="772a0-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="772a0-142">Suponha que seu aplicativo defina uma classe de formulário chamada `specialForm` , que herda da classe <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="772a0-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="772a0-143">Você pode declarar uma variável de objeto que se refere especificamente a `specialForm` , como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="772a0-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="772a0-144">A declaração no exemplo anterior limita a variável `nextForm` a objetos da classe `specialForm` , mas também torna todos os métodos e propriedades de `specialForm` disponíveis para `nextForm` , bem como todos os membros de todas as classes das quais o `specialForm` herda.</span><span class="sxs-lookup"><span data-stu-id="772a0-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="772a0-145">Você pode tornar uma variável de objeto mais geral declarando-a como sendo do tipo <xref:System.Windows.Forms.Form> , como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="772a0-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="772a0-146">A declaração no exemplo anterior permite que você atribua qualquer formulário em seu aplicativo ao `anyForm` .</span><span class="sxs-lookup"><span data-stu-id="772a0-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="772a0-147">No entanto, embora `anyForm` o possa acessar todos os membros da classe <xref:System.Windows.Forms.Form> , ele não pode usar nenhum dos métodos ou propriedades adicionais definidos para formulários específicos, como `specialForm` .</span><span class="sxs-lookup"><span data-stu-id="772a0-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="772a0-148">Todos os membros de uma classe base estão disponíveis para classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.</span><span class="sxs-lookup"><span data-stu-id="772a0-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772a0-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="772a0-149">See also</span></span>

- [<span data-ttu-id="772a0-150">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-150">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="772a0-151">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-151">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="772a0-152">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-152">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="772a0-153">Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="772a0-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="772a0-154">Como acessar membros de um objeto</span><span class="sxs-lookup"><span data-stu-id="772a0-154">How to: Access Members of an Object</span></span>](how-to-access-members-of-an-object.md)
- [<span data-ttu-id="772a0-155">Novo operador</span><span class="sxs-lookup"><span data-stu-id="772a0-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="772a0-156">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="772a0-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="772a0-157">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="772a0-157">Local Type Inference</span></span>](local-type-inference.md)
