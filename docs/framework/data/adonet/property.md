---
title: propriedade
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 6aeb29c5aa608987466ec858416a4ac141ff1da3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180914"
---
# <a name="property"></a><span data-ttu-id="f6a80-102">propriedade</span><span class="sxs-lookup"><span data-stu-id="f6a80-102">property</span></span>

<span data-ttu-id="f6a80-103">*As propriedades* são os blocos de construção fundamentais dos tipos de [entidade](entity-type.md) e [tipos complexos](complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="f6a80-103">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="f6a80-104">As propriedades definem a forma e as características de dados que uma instância do tipo de entidade ou a instância do tipo complexo conterão.</span><span class="sxs-lookup"><span data-stu-id="f6a80-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="f6a80-105">As propriedades em um modelo conceitual são análogas as propriedades definidas em uma classe.</span><span class="sxs-lookup"><span data-stu-id="f6a80-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="f6a80-106">Da mesma forma que as propriedades em uma classe definem a forma da classe e transportam informações sobre objetos, as propriedades em um modelo conceitual definem a forma de um tipo de entidade e transportam informações sobre as instâncias dos tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="f6a80-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a80-107">As propriedades, como descrito neste tópico, são diferentes de propriedades de navegação.</span><span class="sxs-lookup"><span data-stu-id="f6a80-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="f6a80-108">Para obter mais informações, consulte [Propriedades de navegação](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="f6a80-108">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="f6a80-109">Uma definição de propriedade contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="f6a80-109">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="f6a80-110">Um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f6a80-110">A property name.</span></span> <span data-ttu-id="f6a80-111">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="f6a80-111">(Required)</span></span>  
  
- <span data-ttu-id="f6a80-112">Um tipo de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f6a80-112">A property type.</span></span> <span data-ttu-id="f6a80-113">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="f6a80-113">(Required)</span></span>  
  
- <span data-ttu-id="f6a80-114">Um conjunto de [facetas](facet.md).</span><span class="sxs-lookup"><span data-stu-id="f6a80-114">A set of [facets](facet.md).</span></span> <span data-ttu-id="f6a80-115">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="f6a80-115">(Optional)</span></span>  
  
 <span data-ttu-id="f6a80-116">Uma propriedade pode conter dados primitivos (como uma cadeia de caracteres, um número inteiro ou um valor booliano) ou dados estruturados (como um tipo complexo).</span><span class="sxs-lookup"><span data-stu-id="f6a80-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="f6a80-117">As propriedades que são do tipo primitivo também são chamadas propriedades escalares.</span><span class="sxs-lookup"><span data-stu-id="f6a80-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="f6a80-118">Para obter mais informações, consulte [modelo de dados de entidade: tipos de dados primitivos](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f6a80-118">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6a80-119">Um tipo complexo pode, em si, para ter as propriedades que são tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="f6a80-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6a80-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6a80-120">Example</span></span>  

 <span data-ttu-id="f6a80-121">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="f6a80-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="f6a80-122">Cada tipo de entidade tem várias propriedades, embora as informações de tipo para cada propriedade não é transmitida no diagrama.</span><span class="sxs-lookup"><span data-stu-id="f6a80-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="f6a80-123">As propriedades que são [chaves de entidade](entity-key.md) são indicadas com (chave).</span><span class="sxs-lookup"><span data-stu-id="f6a80-123">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="f6a80-125">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="f6a80-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f6a80-126">CSDL seguir define o tipo de entidade de `Book` (conforme mostrado no diagrama anterior) e indica o tipo e o nome de cada propriedade usando atributos XML.</span><span class="sxs-lookup"><span data-stu-id="f6a80-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="f6a80-127">Um aspecto opcional, `Nullable`, também é definida usando um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="f6a80-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="f6a80-128">É possível que uma das propriedades mostradas no diagrama é uma propriedade do tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="f6a80-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="f6a80-129">Por exemplo, a propriedade de `Address` no tipo de entidade de `Publisher` pode ser uma propriedade do tipo complexo composto de várias propriedades escalares, como `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="f6a80-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="f6a80-130">A representação de CSDL de um tipo complexo seria como segue:</span><span class="sxs-lookup"><span data-stu-id="f6a80-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f6a80-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="f6a80-131">See also</span></span>

- [<span data-ttu-id="f6a80-132">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="f6a80-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f6a80-133">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="f6a80-133">Entity Data Model</span></span>](entity-data-model.md)
