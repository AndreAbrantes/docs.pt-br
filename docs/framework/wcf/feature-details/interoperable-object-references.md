---
title: Referências de objeto interoperável
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: bf395c187c46e88406bfb81798c7e359b48255e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263224"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="c1a7e-102">Referências de objeto interoperável</span><span class="sxs-lookup"><span data-stu-id="c1a7e-102">Interoperable object references</span></span>

<span data-ttu-id="c1a7e-103">Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="c1a7e-104">Você pode usar a <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriedade para instruir o serializador de contrato de dados a preservar referências de objeto ao serializar objetos.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="c1a7e-105">XML gerado</span><span class="sxs-lookup"><span data-stu-id="c1a7e-105">Generated XML</span></span>  

 <span data-ttu-id="c1a7e-106">Como exemplo, considere o seguinte objeto:</span><span class="sxs-lookup"><span data-stu-id="c1a7e-106">As an example, consider the following object:</span></span>  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 <span data-ttu-id="c1a7e-107">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `false` (o padrão), o seguinte XML é gerado:</span><span class="sxs-lookup"><span data-stu-id="c1a7e-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="c1a7e-108">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `true` , o seguinte XML é gerado:</span><span class="sxs-lookup"><span data-stu-id="c1a7e-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="c1a7e-109">No entanto, <xref:System.Runtime.Serialization.XsdDataContractExporter> o não descreve os `id` `ref` atributos e em seu esquema, mesmo quando a `preserveObjectReferences` propriedade é definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="c1a7e-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="c1a7e-110">Usando IsReference</span><span class="sxs-lookup"><span data-stu-id="c1a7e-110">Using IsReference</span></span>  

 <span data-ttu-id="c1a7e-111">Para gerar informações de referência de objeto que são válidas de acordo com o esquema que a descreve, aplique o <xref:System.Runtime.Serialization.DataContractAttribute> atributo a um tipo e defina o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> sinalizador como `true` .</span><span class="sxs-lookup"><span data-stu-id="c1a7e-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="c1a7e-112">O exemplo a seguir modifica a classe `X` no exemplo anterior adicionando `IsReference` :</span><span class="sxs-lookup"><span data-stu-id="c1a7e-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 <span data-ttu-id="c1a7e-113">O XML gerado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c1a7e-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="c1a7e-114">O uso `IsReference` de garante a conformidade com o ida e volta da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="c1a7e-115">Sem ele, quando um tipo é gerado a partir do esquema, a saída XML para esse tipo não é necessariamente compatível com o esquema assumido originalmente.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="c1a7e-116">Em outras palavras, embora os `id` `ref` atributos e tenham sido serializados, o esquema original poderia ter bloqueado esses atributos (ou todos os atributos) da ocorrência no XML.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="c1a7e-117">Com `IsReference` aplicado a um membro de dados, o membro continua a ser reconhecido como *referenciable* quando movimentado por ida e volta.</span><span class="sxs-lookup"><span data-stu-id="c1a7e-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a7e-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1a7e-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
