---
title: Exibindo informações de tipo
description: Exiba informações de tipo usando System. Type, que é central para reflexão no .NET. Examine ConstructorInfo, MemberInfo, MethodInfo, FieldInfo e PropertyInfo.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
ms.openlocfilehash: cd74021e1f1a79626e171db13def98e546cd51df
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865197"
---
# <a name="viewing-type-information"></a><span data-ttu-id="9da4e-104">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="9da4e-104">Viewing Type Information</span></span>
<span data-ttu-id="9da4e-105">A classe <xref:System.Type?displayProperty=nameWithType> é fundamental para reflexão.</span><span class="sxs-lookup"><span data-stu-id="9da4e-105">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="9da4e-106">O Common Language Runtime cria o **Type** para um tipo carregado quando a reflexão solicitá-lo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-106">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="9da4e-107">Você pode usar os métodos, campos, propriedades e classes aninhadas de um objeto **Tipo** para descobrir tudo sobre o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="9da4e-107">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="9da4e-108">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> para obter objetos **Tipo** de assemblies que não foram carregados, passando o nome do tipo ou tipos que você deseja.</span><span class="sxs-lookup"><span data-stu-id="9da4e-108">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="9da4e-109">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> para obter objetos **Tipo** de um assembly que já foi carregado.</span><span class="sxs-lookup"><span data-stu-id="9da4e-109">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="9da4e-110">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> e <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> para obter objetos **Type** do módulo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-110">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9da4e-111">Se você quiser examinar e manipular tipos genéricos e métodos, consulte as informações adicionais fornecidas na [Reflexão e tipos genéricos](reflection-and-generic-types.md) e [Como examinar e instanciar tipos genéricos com reflexão](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9da4e-111">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="9da4e-112">O exemplo a seguir mostra a sintaxe necessária obter o objeto <xref:System.Reflection.Assembly> e o módulo para um assembly.</span><span class="sxs-lookup"><span data-stu-id="9da4e-112">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="9da4e-113">O exemplo a seguir demonstra como obter objetos de **Tipo** de um assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="9da4e-113">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="9da4e-114">Depois de obter um **Tipo**, há várias maneiras de descobrir informações sobre os membros desse tipo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-114">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="9da4e-115">Por exemplo, você pode descobrir sobre todos os membros do tipo chamando o método <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>, que obtém uma matriz de objetos <xref:System.Reflection.MemberInfo> que descrevem cada um dos membros do tipo atual.</span><span class="sxs-lookup"><span data-stu-id="9da4e-115">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="9da4e-116">Você também pode usar métodos na classe **Tipo** para recuperar informações sobre um ou mais construtores, métodos, eventos, campos ou propriedades que você especifica por nome.</span><span class="sxs-lookup"><span data-stu-id="9da4e-116">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="9da4e-117">Por exemplo, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsula um construtor específico da classe atual.</span><span class="sxs-lookup"><span data-stu-id="9da4e-117">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="9da4e-118">Se você tiver um **Tipo**, poderá usar a propriedade <xref:System.Type.Module%2A?displayProperty=nameWithType> para obter um objeto que encapsula o módulo que contém esse tipo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-118">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="9da4e-119">Use a propriedade <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> para localizar um objeto que encapsula o assembly que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-119">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="9da4e-120">Você pode obter o assembly que encapsula o tipo diretamente usando a propriedade <xref:System.Type.Assembly%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9da4e-120">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="9da4e-121">System.Type e ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="9da4e-121">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="9da4e-122">O exemplo a seguir mostra como listar os construtores de uma classe, nesse caso, a classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="9da4e-122">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="9da4e-123">MemberInfo, MethodInfo, FieldInfo e PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="9da4e-123">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="9da4e-124">Obtenha informações sobre métodos, propriedades, eventos e campos do tipo usando os objetos <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo> ou <xref:System.Reflection.PropertyInfo>.</span><span class="sxs-lookup"><span data-stu-id="9da4e-124">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="9da4e-125">O exemplo a seguir usa **MemberInfo** para listar o número de membros na classe **System.IO.File** e usa a propriedade <xref:System.Type.IsPublic%2A> para determinar a visibilidade da classe.</span><span class="sxs-lookup"><span data-stu-id="9da4e-125">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="9da4e-126">O exemplo a seguir examina o tipo do membro especificado.</span><span class="sxs-lookup"><span data-stu-id="9da4e-126">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="9da4e-127">Ele executa reflexão em um membro da classe **MemberInfo** e lista seu tipo.</span><span class="sxs-lookup"><span data-stu-id="9da4e-127">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="9da4e-128">O exemplo a seguir usa todas as classes de \*\* \* informações\*\* de reflexão junto com <xref:System.Reflection.BindingFlags> para listar todos os membros (construtores, campos, propriedades, eventos e métodos) da classe especificada, dividindo os membros em categorias de instância e estática.</span><span class="sxs-lookup"><span data-stu-id="9da4e-128">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9da4e-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="9da4e-129">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="9da4e-130">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="9da4e-130">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
