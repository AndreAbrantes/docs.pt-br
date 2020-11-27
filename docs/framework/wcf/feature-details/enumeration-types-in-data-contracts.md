---
title: Tipos de enumeração em contratos de dados
description: Saiba mais sobre como o modelo de contrato de dados expressa enumerações como parte do modelo de programação WFC.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 88bf2513435a9c00cf11a0681b32871992c8d2b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276653"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="71ee8-103">Tipos de enumeração em contratos de dados</span><span class="sxs-lookup"><span data-stu-id="71ee8-103">Enumeration Types in Data Contracts</span></span>

<span data-ttu-id="71ee8-104">As enumerações podem ser expressas no modelo de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="71ee8-104">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="71ee8-105">Este tópico descreve vários exemplos que explicam o modelo de programação.</span><span class="sxs-lookup"><span data-stu-id="71ee8-105">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="71ee8-106">Noções básicas de enumeração</span><span class="sxs-lookup"><span data-stu-id="71ee8-106">Enumeration Basics</span></span>  

 <span data-ttu-id="71ee8-107">Uma maneira de usar tipos de enumeração no modelo de contrato de dados é aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> atributo ao tipo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-107">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="71ee8-108">Em seguida, você deve aplicar o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo a cada membro que deve ser incluído no contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="71ee8-108">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="71ee8-109">O exemplo a seguir mostra duas classes.</span><span class="sxs-lookup"><span data-stu-id="71ee8-109">The following example shows two classes.</span></span> <span data-ttu-id="71ee8-110">O primeiro usa a enumeração e a segunda define a enumeração.</span><span class="sxs-lookup"><span data-stu-id="71ee8-110">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="71ee8-111">Uma instância da `Car` classe pode ser enviada ou recebida somente se o `condition` campo for definido como um dos valores `New` , `Used` ou `Rental` .</span><span class="sxs-lookup"><span data-stu-id="71ee8-111">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="71ee8-112">Se `condition` for `Broken` ou `Stolen` , um <xref:System.Runtime.Serialization.SerializationException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="71ee8-112">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="71ee8-113">Você pode usar as <xref:System.Runtime.Serialization.DataContractAttribute> Propriedades ( <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> e <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> ) normalmente para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="71ee8-113">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="71ee8-114">Valores de membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="71ee8-114">Enumeration Member Values</span></span>  

 <span data-ttu-id="71ee8-115">Geralmente, o contrato de dados inclui nomes de membros de enumeração, não valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="71ee8-115">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="71ee8-116">No entanto, ao usar o modelo de contrato de dados, se o lado de recebimento for um cliente WCF, o esquema exportado preservará os valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="71ee8-116">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="71ee8-117">Observe que esse não é o caso ao usar o [usando a classe XmlSerializer](using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="71ee8-117">Note that this is not the case when using the [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="71ee8-118">No exemplo anterior, se `condition` é definido como `Used` e os dados são serializados para XML, o XML resultante é `<condition>Used</condition>` e não `<condition>1</condition>` .</span><span class="sxs-lookup"><span data-stu-id="71ee8-118">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="71ee8-119">Portanto, o contrato de dados a seguir é equivalente ao contrato de dados do `CarConditionEnum` .</span><span class="sxs-lookup"><span data-stu-id="71ee8-119">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="71ee8-120">Por exemplo, você pode usar `CarConditionEnum` no lado de envio e `CarConditionWithNumbers` no lado de recebimento.</span><span class="sxs-lookup"><span data-stu-id="71ee8-120">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="71ee8-121">Embora o lado de envio use o valor "1" para `Used` e o lado de recebimento use o valor "20", a representação XML é `<condition>Used</condition>` para ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="71ee8-121">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="71ee8-122">Para ser incluído no contrato de dados, você deve aplicar o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-122">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="71ee8-123">Na .NET Framework, você sempre pode aplicar o valor especial 0 (zero) a uma enumeração, que também é o valor padrão para qualquer enumeração.</span><span class="sxs-lookup"><span data-stu-id="71ee8-123">In the .NET Framework, you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="71ee8-124">No entanto, mesmo esse valor zero especial não pode ser serializado, a menos que esteja marcado com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-124">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="71ee8-125">Há duas exceções a isso:</span><span class="sxs-lookup"><span data-stu-id="71ee8-125">There are two exceptions to this:</span></span>  
  
- <span data-ttu-id="71ee8-126">Sinalize enumerações (discutidas posteriormente neste tópico).</span><span class="sxs-lookup"><span data-stu-id="71ee8-126">Flag enumerations (discussed later in this topic).</span></span>  
  
- <span data-ttu-id="71ee8-127">Membros de dados de enumeração com a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade definida como `false` (nesse caso, a enumeração com o valor zero é omitida dos dados serializados).</span><span class="sxs-lookup"><span data-stu-id="71ee8-127">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="71ee8-128">Personalizando valores de membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="71ee8-128">Customizing Enumeration Member Values</span></span>  

 <span data-ttu-id="71ee8-129">Você pode personalizar o valor do membro de enumeração que forma uma parte do contrato de dados usando a <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> Propriedade do <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-129">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="71ee8-130">Por exemplo, o contrato de dados a seguir também é equivalente ao contrato de dados do `CarConditionEnum` .</span><span class="sxs-lookup"><span data-stu-id="71ee8-130">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="71ee8-131">Quando serializado, o valor de `PreviouslyOwned` tem a representação XML `<condition>Used</condition>` .</span><span class="sxs-lookup"><span data-stu-id="71ee8-131">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="71ee8-132">Enumerações simples</span><span class="sxs-lookup"><span data-stu-id="71ee8-132">Simple Enumerations</span></span>  

 <span data-ttu-id="71ee8-133">Você também pode serializar tipos de enumeração aos quais o <xref:System.Runtime.Serialization.DataContractAttribute> atributo não foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="71ee8-133">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="71ee8-134">Esses tipos de enumeração são tratados exatamente como descrito anteriormente, exceto pelo fato de que cada membro (que não tem o <xref:System.NonSerializedAttribute> atributo aplicado) é tratado como se o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo tenha sido aplicado.</span><span class="sxs-lookup"><span data-stu-id="71ee8-134">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="71ee8-135">Por exemplo, a seguinte enumeração tem implicitamente um contrato de dados equivalente ao `CarConditionEnum` exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="71ee8-135">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="71ee8-136">Você pode usar enumerações simples quando não precisar personalizar o nome do contrato de dados da enumeração e o namespace e os valores de membro da enumeração.</span><span class="sxs-lookup"><span data-stu-id="71ee8-136">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="71ee8-137">Observações sobre enumerações simples</span><span class="sxs-lookup"><span data-stu-id="71ee8-137">Notes on Simple Enumerations</span></span>  

 <span data-ttu-id="71ee8-138">A aplicação do <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo a enumerações simples não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="71ee8-138">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="71ee8-139">Não faz diferença se o <xref:System.SerializableAttribute> atributo é aplicado ou não à enumeração.</span><span class="sxs-lookup"><span data-stu-id="71ee8-139">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="71ee8-140">O fato de que a <xref:System.Runtime.Serialization.DataContractSerializer> classe honra o <xref:System.NonSerializedAttribute> atributo aplicado aos membros da enumeração é diferente do comportamento do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e do <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="71ee8-140">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="71ee8-141">Ambos os serializadores ignoram o <xref:System.NonSerializedAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-141">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="71ee8-142">Enumerações de sinalizador</span><span class="sxs-lookup"><span data-stu-id="71ee8-142">Flag Enumerations</span></span>  

 <span data-ttu-id="71ee8-143">Você pode aplicar o <xref:System.FlagsAttribute> atributo a enumerações.</span><span class="sxs-lookup"><span data-stu-id="71ee8-143">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="71ee8-144">Nesse caso, uma lista de zero ou mais valores de enumeração pode ser enviada ou recebida simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="71ee8-144">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="71ee8-145">Para fazer isso, aplique o <xref:System.Runtime.Serialization.DataContractAttribute> atributo à enumeração de sinalizador e marque todos os membros que são potências de dois com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-145">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="71ee8-146">Observe que, para usar uma enumeração de sinalizador, a progressão deve ser uma sequência ininterrupta de potências de 2 (por exemplo, 1, 2, 4, 8, 16, 32, 64).</span><span class="sxs-lookup"><span data-stu-id="71ee8-146">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="71ee8-147">As etapas a seguir se aplicam ao envio do valor de enumeração de um sinalizador:</span><span class="sxs-lookup"><span data-stu-id="71ee8-147">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="71ee8-148">Tentativa de localizar um membro de enumeração (com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo aplicado) que é mapeado para o valor numérico.</span><span class="sxs-lookup"><span data-stu-id="71ee8-148">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="71ee8-149">Se for encontrado, envie uma lista que contenha apenas esse membro.</span><span class="sxs-lookup"><span data-stu-id="71ee8-149">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="71ee8-150">Tentativa de quebrar o valor numérico em uma soma de modo que haja membros de enumeração (cada um com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo aplicado) que é mapeado para cada parte da soma.</span><span class="sxs-lookup"><span data-stu-id="71ee8-150">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="71ee8-151">Envie a lista de todos esses membros.</span><span class="sxs-lookup"><span data-stu-id="71ee8-151">Send the list of all these members.</span></span> <span data-ttu-id="71ee8-152">Observe que o *algoritmo de ávido* é usado para encontrar essa soma e, portanto, não há nenhuma garantia de que essa soma seja encontrada, mesmo que esteja presente.</span><span class="sxs-lookup"><span data-stu-id="71ee8-152">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="71ee8-153">Para evitar esse problema, certifique-se de que os valores numéricos dos membros da enumeração sejam potências de dois.</span><span class="sxs-lookup"><span data-stu-id="71ee8-153">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="71ee8-154">Se as duas etapas anteriores falharem e o valor numérico for diferente de zero, lance a <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="71ee8-154">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="71ee8-155">Se o valor numérico for zero, envie a lista vazia.</span><span class="sxs-lookup"><span data-stu-id="71ee8-155">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="71ee8-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71ee8-156">Example</span></span>  

 <span data-ttu-id="71ee8-157">O exemplo de enumeração a seguir pode ser usado em uma operação de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="71ee8-157">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="71ee8-158">Os valores de exemplo a seguir são serializados conforme indicado.</span><span class="sxs-lookup"><span data-stu-id="71ee8-158">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="71ee8-159">Veja também</span><span class="sxs-lookup"><span data-stu-id="71ee8-159">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="71ee8-160">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="71ee8-160">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="71ee8-161">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="71ee8-161">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)
