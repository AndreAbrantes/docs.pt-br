---
title: Implementando lógica de negócios (LINQ te o SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3d703f7a13f21947fb5d2b5adcac8ae4df6a1547
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158364"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="c0020-102">Implementando lógica de negócios (LINQ te o SQL)</span><span class="sxs-lookup"><span data-stu-id="c0020-102">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="c0020-103">O termo “lógica de negócios” neste tópico faz referência a todas as regras personalizadas ou testes de validação que você aplica a dados antes de eles serem inseridos, atualizados ou excluídos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c0020-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="c0020-104">A lógica de negócios às vezes também é conhecida como "regras de negócio" ou "lógica de domínio".</span><span class="sxs-lookup"><span data-stu-id="c0020-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="c0020-105">Em aplicativos de n camadas ela normalmente é criada como uma camada lógica para que possa ser modificada independentemente da camada de apresentação ou da camada de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="c0020-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="c0020-106">A lógica de negócios pode ser chamada pela camada de acesso a dados antes ou depois de qualquer atualização, inserção ou exclusão de dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c0020-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="c0020-107">A lógica de negócios pode ser tão simples quanto uma validação de esquema para garantir que o tipo do campo seja compatível com o tipo da coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="c0020-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="c0020-108">Ou pode consistir em um conjunto de objetos que interagem de maneiras arbitrariamente complexas.</span><span class="sxs-lookup"><span data-stu-id="c0020-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="c0020-109">As regras podem ser implementadas como procedimentos armazenados no banco de dados ou como objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="c0020-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="c0020-110">No entanto, a lógica de negócios é implementada, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] permite que você use classes parciais e métodos parciais para separar a lógica de negócios do código de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="c0020-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="c0020-111">Como o LINQ to SQL chama sua lógica de negócios</span><span class="sxs-lookup"><span data-stu-id="c0020-111">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="c0020-112">Quando você gera uma classe de entidade em tempo de design, seja manualmente ou usando o Object Relational Designer ou SqlMetal, ela é definida como uma classe parcial.</span><span class="sxs-lookup"><span data-stu-id="c0020-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="c0020-113">Isso significa que, em um arquivo de código separado, você pode definir outra parte da classe de entidade que contém a lógica de negócios personalizada.</span><span class="sxs-lookup"><span data-stu-id="c0020-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="c0020-114">No momento da compilação, as duas partes são mescladas em uma única classe.</span><span class="sxs-lookup"><span data-stu-id="c0020-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="c0020-115">Mas se você precisar regenerar suas classes de entidade usando o Object Relational Designer ou SqlMetal, poderá fazer isso e sua parte da classe não será modificada.</span><span class="sxs-lookup"><span data-stu-id="c0020-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="c0020-116">As classes parciais que definem entidades e o <xref:System.Data.Linq.DataContext> contêm métodos parciais.</span><span class="sxs-lookup"><span data-stu-id="c0020-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="c0020-117">Esses são os pontos de extensibilidade que você pode usar para aplicar sua lógica de negócios antes e depois de qualquer atualização, inserção ou exclusão de uma entidade ou propriedade de entidade.</span><span class="sxs-lookup"><span data-stu-id="c0020-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="c0020-118">Os métodos parciais podem ser considerados como eventos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="c0020-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="c0020-119">O gerador de código define uma assinatura do método e chama os métodos nos acessadores de propriedade get e set, o construtor de `DataContext` e, em alguns casos o código em segundo plano quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="c0020-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="c0020-120">Entretanto, se você não implementar um método parcial específico, todas as referências a ele e a definição serão removidos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="c0020-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="c0020-121">Na definição da implementação que você escreve no arquivo de código separado, você pode executar qualquer lógica personalizada que seja necessária.</span><span class="sxs-lookup"><span data-stu-id="c0020-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="c0020-122">Você pode usar a classe parcial própria como a camada de domínio ou chamar da definição de sua implementação do método parcial em um objeto ou objetos separados.</span><span class="sxs-lookup"><span data-stu-id="c0020-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="c0020-123">De qualquer forma, sua lógica de negócios é corretamente separada do seu código de acesso a dados e do seu código da camada de apresentação.</span><span class="sxs-lookup"><span data-stu-id="c0020-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="c0020-124">Uma visão mais profunda dos pontos de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="c0020-124">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="c0020-125">O exemplo a seguir mostra parte do código gerado pelo Object Relational Designer para a `DataContext` classe que tem duas tabelas: `Customers` e `Orders` .</span><span class="sxs-lookup"><span data-stu-id="c0020-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="c0020-126">Observe que os métodos Insert, Update e Delete são definidos para cada tabela da classe.</span><span class="sxs-lookup"><span data-stu-id="c0020-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="c0020-127">Se você implementar os métodos Insert, Update e Delete em sua classe parcial, o runtime do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] os chamará em vez de seus próprios métodos padrão quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> for chamado.</span><span class="sxs-lookup"><span data-stu-id="c0020-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="c0020-128">Isso permite que você substitua o comportamento padrão para operações de criação/leitura/atualização/exclusão.</span><span class="sxs-lookup"><span data-stu-id="c0020-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="c0020-129">Para obter mais informações, consulte [Walkthrough: Personalizando o comportamento de inserção, atualização e exclusão de classes de entidade](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="c0020-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="c0020-130">O método `OnCreated` é chamado no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="c0020-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="c0020-131">As classes de entidade têm três métodos que são chamados pelo runtime do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em que a entidade é criada, carregada, e validada (quando `SubmitChanges` é chamado).</span><span class="sxs-lookup"><span data-stu-id="c0020-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="c0020-132">As classes de entidade também têm dois métodos parciais para cada propriedade, um que é chamado antes de a propriedade ser definida, e um que é chamado depois.</span><span class="sxs-lookup"><span data-stu-id="c0020-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="c0020-133">O exemplo de código a seguir mostra alguns dos métodos gerados para a classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="c0020-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="c0020-134">Os métodos são chamados no acessador de definição da propriedade conforme mostrado no exemplo a seguir para a propriedade `CustomerID`:</span><span class="sxs-lookup"><span data-stu-id="c0020-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="c0020-135">Na sua parte da classe, você escreve uma definição de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="c0020-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="c0020-136">No Visual Studio, depois de digitar, `partial` você verá o IntelliSense para as definições de método na outra parte da classe.</span><span class="sxs-lookup"><span data-stu-id="c0020-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="c0020-137">Para obter mais informações sobre como adicionar lógica de negócios a seu aplicativo usando métodos parciais, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0020-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="c0020-138">Como adicionar validação a classes de entidade</span><span class="sxs-lookup"><span data-stu-id="c0020-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="c0020-139">Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade</span><span class="sxs-lookup"><span data-stu-id="c0020-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="c0020-140">[Passo a passo: Adicionar validação a classes de entidade](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c0020-140">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0020-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0020-141">See also</span></span>

- [<span data-ttu-id="c0020-142">Classes parciais e métodos</span><span class="sxs-lookup"><span data-stu-id="c0020-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="c0020-143">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="c0020-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="c0020-144">Ferramentas LINQ to SQL no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0020-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="c0020-145">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="c0020-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
