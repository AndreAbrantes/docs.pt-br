---
title: Escrevendo atributos personalizados
description: Crie seus próprios atributos personalizados no .NET. Os atributos personalizados são essencialmente classes derivadas de forma direta ou indireta de System. Attribute.
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 3cae8de9b76aa9953b21ad2e23ad003e97555aa9
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768476"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="e76f7-104">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="e76f7-104">Writing Custom Attributes</span></span>
<span data-ttu-id="e76f7-105">Para criar seus próprios atributos personalizados, não é preciso dominar muitos novos conceitos.</span><span class="sxs-lookup"><span data-stu-id="e76f7-105">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="e76f7-106">Se estiver familiarizado com a programação orientada a objeto e souber como criar classes, você já domina a maior parte do conhecimento necessário.</span><span class="sxs-lookup"><span data-stu-id="e76f7-106">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="e76f7-107">Os atributos personalizados são classes essencialmente tradicionais que derivam direta ou indiretamente de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e76f7-107">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e76f7-108">Como acontece nas classes tradicionais, os atributos personalizados contêm métodos que armazenam e recuperam dados.</span><span class="sxs-lookup"><span data-stu-id="e76f7-108">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="e76f7-109">As principais etapas para criar corretamente classes de atributos personalizados são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="e76f7-109">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="e76f7-110">Aplicar o AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="e76f7-110">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="e76f7-111">Declarar a classe de atributos</span><span class="sxs-lookup"><span data-stu-id="e76f7-111">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="e76f7-112">Declarar constructos</span><span class="sxs-lookup"><span data-stu-id="e76f7-112">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="e76f7-113">Declarar propriedades</span><span class="sxs-lookup"><span data-stu-id="e76f7-113">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="e76f7-114">Esta seção descreve cada uma dessas etapas e oferece um [exemplo de atributo personalizado](#custom-attribute-example) no fim.</span><span class="sxs-lookup"><span data-stu-id="e76f7-114">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="e76f7-115">Aplicar o AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="e76f7-115">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="e76f7-116">A declaração de um atributo personalizado começa com o <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, que define algumas das principais características da classe de atributos.</span><span class="sxs-lookup"><span data-stu-id="e76f7-116">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="e76f7-117">Por exemplo, é possível especificar se o atributo pode ser herdado por outras classes ou a quais elementos o atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="e76f7-117">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="e76f7-118">O fragmento de código a seguir demonstra como usar o <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e76f7-118">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="e76f7-119">O <xref:System.AttributeUsageAttribute> possui três membros que são importantes para a criação de atributos personalizados: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property) e [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="e76f7-119">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="e76f7-120">Membro de AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="e76f7-120">AttributeTargets Member</span></span>  
 <span data-ttu-id="e76f7-121">No exemplo anterior, <xref:System.AttributeTargets.All?displayProperty=nameWithType> é especificado, indicando que esse atributo pode ser aplicado a todos os elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="e76f7-121">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="e76f7-122">Como alternativa, você pode especificar <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, que indica que o atributo pode ser aplicado somente a uma classe, ou <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, que indica que o atributo pode ser aplicado a um único método.</span><span class="sxs-lookup"><span data-stu-id="e76f7-122">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="e76f7-123">Todos os elementos do programa podem ser marcados para serem descritos dessa maneira por um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e76f7-123">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="e76f7-124">Você também pode passar vários valores de <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="e76f7-124">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="e76f7-125">O fragmento de código a seguir especifica que um atributo personalizado pode ser aplicado a qualquer classe ou método.</span><span class="sxs-lookup"><span data-stu-id="e76f7-125">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="e76f7-126">Propriedade Inherited</span><span class="sxs-lookup"><span data-stu-id="e76f7-126">Inherited Property</span></span>  
 <span data-ttu-id="e76f7-127">A propriedade <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> indica se o atributo pode ser herdado pelas classes derivadas das classes às quais o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="e76f7-127">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="e76f7-128">Essa propriedade aceita um sinalizador `true` (o padrão) ou `false`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-128">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="e76f7-129">No exemplo a seguir, `MyAttribute` tem um valor padrão <xref:System.AttributeUsageAttribute.Inherited%2A> de `true`, enquanto `YourAttribute` tem um valor <xref:System.AttributeUsageAttribute.Inherited%2A> de `false`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-129">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="e76f7-130">Em seguida, os dois atributos são aplicados a um método na classe base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-130">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="e76f7-131">Por fim, a classe `YourClass` é herdada da classe base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-131">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="e76f7-132">O método `MyMethod` mostra `MyAttribute`, mas não mostra `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-132">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="e76f7-133">Propriedade AllowMultiple</span><span class="sxs-lookup"><span data-stu-id="e76f7-133">AllowMultiple Property</span></span>  
 <span data-ttu-id="e76f7-134">A propriedade <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> indica se várias instâncias do atributo podem existir em um elemento.</span><span class="sxs-lookup"><span data-stu-id="e76f7-134">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="e76f7-135">Se for definida como `true`, várias instâncias serão permitidas; se for definida como `false` (padrão), apenas uma instância será permitida.</span><span class="sxs-lookup"><span data-stu-id="e76f7-135">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="e76f7-136">No exemplo a seguir, `MyAttribute` tem um valor padrão <xref:System.AttributeUsageAttribute.AllowMultiple%2A> de `false`, enquanto `YourAttribute` tem um valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-136">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="e76f7-137">Quando várias instâncias desses atributos são aplicadas, `MyAttribute` produz um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="e76f7-137">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="e76f7-138">O exemplo de código a seguir mostra o uso válido de `YourAttribute` e o uso inválido de `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e76f7-138">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="e76f7-139">Se as propriedades <xref:System.AttributeUsageAttribute.AllowMultiple%2A> e <xref:System.AttributeUsageAttribute.Inherited%2A> estiverem definidas como `true`, uma classe herdada de outra classe poderá herdar um atributo e ter outra instância do mesmo atributo aplicada à mesma classe filho.</span><span class="sxs-lookup"><span data-stu-id="e76f7-139">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="e76f7-140">Se <xref:System.AttributeUsageAttribute.AllowMultiple%2A> estiver definida como `false`, os valores de todos os atributos na classe pai serão substituídos pelas novas instâncias do mesmo atributo na classe filho.</span><span class="sxs-lookup"><span data-stu-id="e76f7-140">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="e76f7-141">Declarar a classe de atributos</span><span class="sxs-lookup"><span data-stu-id="e76f7-141">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="e76f7-142">Depois de aplicar o <xref:System.AttributeUsageAttribute>, comece a definir as especificações do seu atributo.</span><span class="sxs-lookup"><span data-stu-id="e76f7-142">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="e76f7-143">A declaração de uma classe de atributos é semelhante à declaração de uma classe tradicional, como demonstrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e76f7-143">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="e76f7-144">Esta definição de atributo demonstra os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="e76f7-144">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="e76f7-145">As classes de atributos devem ser declaradas como classes públicas.</span><span class="sxs-lookup"><span data-stu-id="e76f7-145">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="e76f7-146">Por convenção, o nome da classe de atributos termina com a palavra **Attribute**.</span><span class="sxs-lookup"><span data-stu-id="e76f7-146">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="e76f7-147">Embora não seja necessária, essa convenção é recomendada para facilitar a leitura.</span><span class="sxs-lookup"><span data-stu-id="e76f7-147">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="e76f7-148">Quando o atributo é aplicado, a inclusão da palavra Attribute torna-se opcional.</span><span class="sxs-lookup"><span data-stu-id="e76f7-148">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="e76f7-149">Todas as classes de atributos devem ser herdadas diretamente ou indiretamente de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e76f7-149">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="e76f7-150">No Microsoft Visual Basic, todas as classes de atributos personalizados devem ter o atributo <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e76f7-150">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="e76f7-151">Declarar constructos</span><span class="sxs-lookup"><span data-stu-id="e76f7-151">Declaring Constructors</span></span>  
 <span data-ttu-id="e76f7-152">Os atributos são inicializados com constructos, como as classes tradicionais.</span><span class="sxs-lookup"><span data-stu-id="e76f7-152">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="e76f7-153">O fragmento de código a seguir ilustra um constructo de atributo típico.</span><span class="sxs-lookup"><span data-stu-id="e76f7-153">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="e76f7-154">Esse construtor público aceita um parâmetro e define uma variável de membro igual ao seu valor.</span><span class="sxs-lookup"><span data-stu-id="e76f7-154">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="e76f7-155">Você pode sobrecarregar o constructo para acomodar diferentes combinações de valores.</span><span class="sxs-lookup"><span data-stu-id="e76f7-155">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="e76f7-156">Se também definir uma [propriedade](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) para sua classe de atributos personalizados, você poderá usar uma combinação de parâmetros nomeados e posicionais ao inicializar o atributo.</span><span class="sxs-lookup"><span data-stu-id="e76f7-156">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="e76f7-157">Normalmente, você define todos os parâmetros necessários como posicionais e todos os parâmetros opcionais como nomeados.</span><span class="sxs-lookup"><span data-stu-id="e76f7-157">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="e76f7-158">Nesse caso, o atributo não pode ser inicializado sem o parâmetro necessário.</span><span class="sxs-lookup"><span data-stu-id="e76f7-158">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="e76f7-159">Todos os outros parâmetros são opcionais.</span><span class="sxs-lookup"><span data-stu-id="e76f7-159">All other parameters are optional.</span></span> <span data-ttu-id="e76f7-160">Observe que, no Visual Basic, o constructos de uma classe de atributos não devem usar um argumento ParamArray.</span><span class="sxs-lookup"><span data-stu-id="e76f7-160">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="e76f7-161">O exemplo de código a seguir mostra como um atributo que usa o constructo anterior pode ser aplicado usando parâmetros necessários e opcionais.</span><span class="sxs-lookup"><span data-stu-id="e76f7-161">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="e76f7-162">Ele pressupõe que o atributo tem um valor booliano necessário e uma cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="e76f7-162">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="e76f7-163">Declarar propriedades</span><span class="sxs-lookup"><span data-stu-id="e76f7-163">Declaring Properties</span></span>  
 <span data-ttu-id="e76f7-164">Se quiser definir um parâmetro nomeado ou disponibilizar uma maneira fácil de retornar os valores armazenados pelo seu atributo, declare uma [propriedade](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e76f7-164">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="e76f7-165">As propriedades de atributos devem ser declaradas como entidades públicas com uma descrição do tipo de dados que será retornado.</span><span class="sxs-lookup"><span data-stu-id="e76f7-165">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="e76f7-166">Defina a variável que conterá o valor de sua propriedade e irá associá-la aos métodos **get** e **set**.</span><span class="sxs-lookup"><span data-stu-id="e76f7-166">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="e76f7-167">O exemplo de código a seguir demonstra como implementar uma propriedade simples em seu atributo.</span><span class="sxs-lookup"><span data-stu-id="e76f7-167">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="e76f7-168">Exemplo de Atributo personalizado</span><span class="sxs-lookup"><span data-stu-id="e76f7-168">Custom Attribute Example</span></span>  
 <span data-ttu-id="e76f7-169">Esta seção incorpora as informações anteriores e mostra como criar um atributo simples que documenta informações sobre o autor de uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="e76f7-169">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="e76f7-170">O atributo neste exemplo armazena o nome e o nível do programador, e se o código foi revisado.</span><span class="sxs-lookup"><span data-stu-id="e76f7-170">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="e76f7-171">Ele usa três variáveis privadas para armazenar os valores reais que serão salvos.</span><span class="sxs-lookup"><span data-stu-id="e76f7-171">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="e76f7-172">Cada variável é representada por uma propriedade pública que obtém e define os valores.</span><span class="sxs-lookup"><span data-stu-id="e76f7-172">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="e76f7-173">Por fim, o constructo é definido com dois parâmetros necessários.</span><span class="sxs-lookup"><span data-stu-id="e76f7-173">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="e76f7-174">Você pode aplicar esse atributo usando o nome completo, `DeveloperAttribute`, ou usando o nome abreviado, `Developer`, em uma das seguintes maneiras.</span><span class="sxs-lookup"><span data-stu-id="e76f7-174">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="e76f7-175">O primeiro exemplo mostra o atributo aplicado com apenas os parâmetros nomeados necessários e o segundo mostra o atributo aplicado com os parâmetros necessários e opcionais.</span><span class="sxs-lookup"><span data-stu-id="e76f7-175">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76f7-176">Veja também</span><span class="sxs-lookup"><span data-stu-id="e76f7-176">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="e76f7-177">Atributos</span><span class="sxs-lookup"><span data-stu-id="e76f7-177">Attributes</span></span>](index.md)
