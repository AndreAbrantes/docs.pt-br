---
title: Referência de esquema de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963366"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="ede8a-102">Referência de esquema de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="ede8a-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="ede8a-103">Este tópico descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever tipos de Common Language Runtime (CLR) para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="ede8a-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="ede8a-104">Mapeamentos do DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="ede8a-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="ede8a-105">O `DataContractSerializer` mapeia os tipos CLR para XSD quando os metadados são exportados de um serviço de Windows Communication Foundation (WCF) usando um ponto de extremidade de metadados ou a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ede8a-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="ede8a-106">Para obter mais informações, consulte [serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="ede8a-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>

<span data-ttu-id="ede8a-107">O `DataContractSerializer` também mapeia XSD para tipos CLR quando svcutil. exe é usado para acessar os documentos WSDL (linguagem de descrição de serviços Web) ou XSD e gerar contratos de dados para serviços ou clientes.</span><span class="sxs-lookup"><span data-stu-id="ede8a-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="ede8a-108">Somente as instâncias de esquema XML que estão em conformidade com os requisitos declarados neste documento podem ser mapeadas para tipos CLR usando `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="ede8a-109">Níveis de suporte</span><span class="sxs-lookup"><span data-stu-id="ede8a-109">Support Levels</span></span>

<span data-ttu-id="ede8a-110">O `DataContractSerializer` fornece os seguintes níveis de suporte para um determinado recurso de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="ede8a-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="ede8a-111">**Com suporte**.</span><span class="sxs-lookup"><span data-stu-id="ede8a-111">**Supported**.</span></span> <span data-ttu-id="ede8a-112">Há um mapeamento explícito desse recurso para tipos CLR ou atributos (ou ambos) usando `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="ede8a-113">**Ignorado**.</span><span class="sxs-lookup"><span data-stu-id="ede8a-113">**Ignored**.</span></span> <span data-ttu-id="ede8a-114">O recurso é permitido em esquemas importados pelo `DataContractSerializer`, mas não tem efeito sobre a geração de código.</span><span class="sxs-lookup"><span data-stu-id="ede8a-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="ede8a-115">**Proibido**.</span><span class="sxs-lookup"><span data-stu-id="ede8a-115">**Forbidden**.</span></span> <span data-ttu-id="ede8a-116">O `DataContractSerializer` não dá suporte à importação de um esquema usando o recurso.</span><span class="sxs-lookup"><span data-stu-id="ede8a-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="ede8a-117">Por exemplo, svcutil. exe, ao acessar um WSDL com um esquema que usa esse recurso, volta a usar o <xref:System.Xml.Serialization.XmlSerializer> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ede8a-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="ede8a-118">Isso é por padrão.</span><span class="sxs-lookup"><span data-stu-id="ede8a-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="ede8a-119">Informações Gerais</span><span class="sxs-lookup"><span data-stu-id="ede8a-119">General Information</span></span>

- <span data-ttu-id="ede8a-120">O namespace do esquema é descrito em [esquema XML](https://www.w3.org/2001/XMLSchema).</span><span class="sxs-lookup"><span data-stu-id="ede8a-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="ede8a-121">O prefixo "XS" é usado neste documento.</span><span class="sxs-lookup"><span data-stu-id="ede8a-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="ede8a-122">Todos os atributos com um namespace não esquema são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="ede8a-123">Todas as anotações (exceto aquelas descritas neste documento) são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="ede8a-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="ede8a-124">\<xs: Schema >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="ede8a-125">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-125">Attribute</span></span>|<span data-ttu-id="ede8a-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="ede8a-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="ede8a-127">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="ede8a-128">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="ede8a-129">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-129">Must be qualified.</span></span> <span data-ttu-id="ede8a-130">Todos os elementos devem ser qualificados para que um esquema seja suportado pelo `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="ede8a-131">Isso pode ser feito definindo xs:schema/@elementFormDefault como "qualificado" ou definindo xs:element/@form como "qualificado" em cada declaração de elemento individual.</span><span class="sxs-lookup"><span data-stu-id="ede8a-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="ede8a-132">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="ede8a-133">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="ede8a-134">Com suporte e mapeado para o namespace de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="ede8a-135">Se esse atributo não for especificado, o namespace em branco será usado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="ede8a-136">Não pode ser o namespace reservado `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="ede8a-137">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="ede8a-138">\<xs:schema>: contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="ede8a-139">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-139">Contents</span></span>|<span data-ttu-id="ede8a-140">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="ede8a-141">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-141">Supported.</span></span> <span data-ttu-id="ede8a-142">o `DataContractSerializer` dá suporte a xs: include e xs: import.</span><span class="sxs-lookup"><span data-stu-id="ede8a-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="ede8a-143">No entanto, svcutil. exe restringe as referências a seguir `xs:include/@schemaLocation` e `xs:import/@location` quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="ede8a-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="ede8a-144">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; os documentos de esquema do `include`d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="ede8a-145">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-145">Forbidden.</span></span> <span data-ttu-id="ede8a-146">O uso de `xs:redefine` é proibido por `DataContractSerializer` por motivos de segurança: `x:redefine` requer que `schemaLocation` seja seguido.</span><span class="sxs-lookup"><span data-stu-id="ede8a-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="ede8a-147">Em determinadas circunstâncias, svcutil. exe usando DataContract restringe o uso de `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="ede8a-148">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-148">Supported.</span></span> <span data-ttu-id="ede8a-149">o `DataContractSerializer` dá suporte a `xs:include` e `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="ede8a-150">No entanto, svcutil. exe restringe as referências a seguir `xs:include/@schemaLocation` e `xs:import/@location` quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="ede8a-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="ede8a-151">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; os documentos de esquema do `include`d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="ede8a-152">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-152">Supported.</span></span> <span data-ttu-id="ede8a-153">Consulte a seção `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="ede8a-154">Com suporte, mapeia para contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="ede8a-155">Consulte a seção `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="ede8a-156">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-156">Ignored.</span></span> <span data-ttu-id="ede8a-157">`DataContractSerializer` não dá suporte ao uso de `xs:group`, `xs:attributeGroup`e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="ede8a-158">Essas declarações são ignoradas como filhos de `xs:schema`, mas não podem ser referenciadas em `complexType` ou em outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="ede8a-159">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-159">Ignored.</span></span> <span data-ttu-id="ede8a-160">`DataContractSerializer` não dá suporte ao uso de `xs:group`, `xs:attributeGroup`e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="ede8a-161">Essas declarações são ignoradas como filhos de `xs:schema`, mas não podem ser referenciadas em `complexType` ou em outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="ede8a-162">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-162">Supported.</span></span> <span data-ttu-id="ede8a-163">Consulte declaração de elemento global (teste).</span><span class="sxs-lookup"><span data-stu-id="ede8a-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="ede8a-164">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-164">Ignored.</span></span> <span data-ttu-id="ede8a-165">`DataContractSerializer` não dá suporte ao uso de `xs:group`, `xs:attributeGroup`e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="ede8a-166">Essas declarações são ignoradas como filhos de `xs:schema`, mas não podem ser referenciadas em `complexType` ou em outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="ede8a-167">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="ede8a-168">Tipos complexos – \<xs: complexType ></span><span class="sxs-lookup"><span data-stu-id="ede8a-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="ede8a-169">Informações Gerais</span><span class="sxs-lookup"><span data-stu-id="ede8a-169">General Information</span></span>

<span data-ttu-id="ede8a-170">Cada tipo complexo \<xs: complexType > é mapeado para um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="ede8a-171">\<xs: complexType >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="ede8a-172">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-172">Attribute</span></span>|<span data-ttu-id="ede8a-173">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="ede8a-174">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="ede8a-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="ede8a-175">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="ede8a-176">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="ede8a-177">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="ede8a-178">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="ede8a-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="ede8a-179">Com suporte e mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="ede8a-180">Se houver períodos no nome, será feita uma tentativa de mapear o tipo para um tipo interno.</span><span class="sxs-lookup"><span data-stu-id="ede8a-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="ede8a-181">Por exemplo, um tipo complexo chamado `A.B` é mapeado para um tipo de contrato de dados que é um tipo interno de um tipo com o nome do contrato de dados `A`, mas somente se existir um tipo de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="ede8a-182">Mais de um nível de aninhamento é possível: por exemplo, `A.B.C` pode ser um tipo interno, mas somente se `A` e `A.B` ambos existirem.</span><span class="sxs-lookup"><span data-stu-id="ede8a-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="ede8a-183">\<xs:complexType>: contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="ede8a-184">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-184">Contents</span></span>|<span data-ttu-id="ede8a-185">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="ede8a-186">As extensões são proibidas.</span><span class="sxs-lookup"><span data-stu-id="ede8a-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="ede8a-187">A restrição só é permitida a partir de `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="ede8a-188">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-188">Supported.</span></span> <span data-ttu-id="ede8a-189">Consulte "herança".</span><span class="sxs-lookup"><span data-stu-id="ede8a-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="ede8a-190">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="ede8a-191">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="ede8a-192">Proibido</span><span class="sxs-lookup"><span data-stu-id="ede8a-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="ede8a-193">Com suporte, mapeia para membros de dados de um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="ede8a-194">Proibido, mesmo que use = "proibido" (com uma exceção).</span><span class="sxs-lookup"><span data-stu-id="ede8a-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="ede8a-195">Há suporte apenas para atributos opcionais do namespace de esquema de serialização padrão.</span><span class="sxs-lookup"><span data-stu-id="ede8a-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="ede8a-196">Eles não são mapeados para membros de dados no modelo de programação de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="ede8a-197">Atualmente, apenas um desses atributos tem significado e é discutido na seção ISerializable.</span><span class="sxs-lookup"><span data-stu-id="ede8a-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="ede8a-198">Todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="ede8a-199">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-199">Forbidden.</span></span> <span data-ttu-id="ede8a-200">Na versão v1 do WCF, `DataContractSerializer` ignora a presença de `attributeGroup` dentro `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="ede8a-201">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-201">Forbidden.</span></span>|
|<span data-ttu-id="ede8a-202">(vazio)</span><span class="sxs-lookup"><span data-stu-id="ede8a-202">(empty)</span></span>|<span data-ttu-id="ede8a-203">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="ede8a-204">\<xs: Sequence > em um tipo complexo: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="ede8a-205">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-205">Attribute</span></span>|<span data-ttu-id="ede8a-206">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="ede8a-207">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="ede8a-208">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="ede8a-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="ede8a-209">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="ede8a-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="ede8a-210">\<xs: Sequence > em um tipo complexo: Contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="ede8a-211">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-211">Contents</span></span>|<span data-ttu-id="ede8a-212">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="ede8a-213">Cada instância é mapeada para um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="ede8a-214">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="ede8a-215">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="ede8a-216">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="ede8a-217">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-217">Forbidden.</span></span>|
|<span data-ttu-id="ede8a-218">(vazio)</span><span class="sxs-lookup"><span data-stu-id="ede8a-218">(empty)</span></span>|<span data-ttu-id="ede8a-219">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="ede8a-220">Elementos – \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="ede8a-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="ede8a-221">Informações Gerais</span><span class="sxs-lookup"><span data-stu-id="ede8a-221">General Information</span></span>

<span data-ttu-id="ede8a-222">`<xs:element>` pode ocorrer nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="ede8a-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="ede8a-223">Isso pode ocorrer em um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados regular (não de coleção).</span><span class="sxs-lookup"><span data-stu-id="ede8a-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="ede8a-224">Nesse caso, o atributo `maxOccurs` deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="ede8a-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="ede8a-225">(Um valor de 0 não é permitido).</span><span class="sxs-lookup"><span data-stu-id="ede8a-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="ede8a-226">Isso pode ocorrer em um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="ede8a-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="ede8a-227">Nesse caso, o atributo `maxOccurs` deve ser maior que 1 ou "não associado".</span><span class="sxs-lookup"><span data-stu-id="ede8a-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="ede8a-228">Isso pode ocorrer dentro de um `<xs:schema>` como uma declaração de elemento global (teste).</span><span class="sxs-lookup"><span data-stu-id="ede8a-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="ede8a-229">\<xs: element > com maxOccurs = 1 em um \<xs: Sequence > (membros de dados)</span><span class="sxs-lookup"><span data-stu-id="ede8a-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="ede8a-230">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-230">Attribute</span></span>|<span data-ttu-id="ede8a-231">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="ede8a-232">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="ede8a-233">Com suporte, é mapeado para o nome do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="ede8a-234">Com suporte, mapeia para o tipo de membro de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="ede8a-235">Para obter mais informações, consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="ede8a-236">Se não for especificado (e o elemento não contiver um tipo anônimo), `xs:anyType` será assumida.</span><span class="sxs-lookup"><span data-stu-id="ede8a-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="ede8a-237">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="ede8a-238">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="ede8a-239">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="ede8a-240">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-240">Must be qualified.</span></span> <span data-ttu-id="ede8a-241">Esse atributo pode ser definido por meio de `elementFormDefault` em `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="ede8a-242">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="ede8a-243">1</span><span class="sxs-lookup"><span data-stu-id="ede8a-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="ede8a-244">Mapeia para a propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> de um membro de dados (`IsRequired` é true quando `minOccurs` é 1).</span><span class="sxs-lookup"><span data-stu-id="ede8a-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="ede8a-245">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-245">Affects type mapping.</span></span> <span data-ttu-id="ede8a-246">Consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="ede8a-247">\<xs: element > com maxOccurs > 1 em um \<xs: Sequence > (Collections)</span><span class="sxs-lookup"><span data-stu-id="ede8a-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="ede8a-248">Mapeia para um <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="ede8a-249">Em tipos de coleção, apenas um xs: Element é permitido dentro de uma sequência xs:.</span><span class="sxs-lookup"><span data-stu-id="ede8a-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="ede8a-250">As coleções podem ser dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="ede8a-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="ede8a-251">Coleções regulares (por exemplo, matrizes).</span><span class="sxs-lookup"><span data-stu-id="ede8a-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="ede8a-252">Coleções de dicionário (mapeando um valor para outro; por exemplo, um <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="ede8a-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="ede8a-253">A única diferença entre um dicionário e uma matriz de um tipo de par chave/valor está no modelo de programação gerado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="ede8a-254">Há um mecanismo de anotação de esquema que pode ser usado para indicar que um determinado tipo é uma coleção de dicionários.</span><span class="sxs-lookup"><span data-stu-id="ede8a-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="ede8a-255">As regras para os atributos `ref`, `block`, `default`, `fixed`, `form`e `id` são as mesmas para o caso sem coleção.</span><span class="sxs-lookup"><span data-stu-id="ede8a-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="ede8a-256">Outros atributos incluem os da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="ede8a-257">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-257">Attribute</span></span>|<span data-ttu-id="ede8a-258">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="ede8a-259">Com suporte, mapeia para a propriedade <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> no atributo `CollectionDataContractAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="ede8a-260">Com suporte, é mapeado para o tipo armazenado na coleção.</span><span class="sxs-lookup"><span data-stu-id="ede8a-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="ede8a-261">Maior que 1 ou "não associado".</span><span class="sxs-lookup"><span data-stu-id="ede8a-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="ede8a-262">O esquema de DC deve usar "não associado".</span><span class="sxs-lookup"><span data-stu-id="ede8a-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="ede8a-263">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="ede8a-264">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-264">Affects type mapping.</span></span> <span data-ttu-id="ede8a-265">Esse atributo é ignorado para coleções de dicionário.</span><span class="sxs-lookup"><span data-stu-id="ede8a-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="ede8a-266">\<xs: element > em uma declaração de elemento global \<xs: Schema ></span><span class="sxs-lookup"><span data-stu-id="ede8a-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="ede8a-267">Uma declaração de elemento global (teste) que tem o mesmo nome e namespace como um tipo no esquema, ou que define um tipo anônimo dentro dele mesmo, é considerada associada ao tipo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="ede8a-268">Exportação de esquema: os GEDs associados são gerados para cada tipo gerado, simples e complexo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="ede8a-269">Desserialização/serialização: os GEDs associados são usados como elementos raiz para o tipo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="ede8a-270">Importação de esquema: os GEDs associados não são necessários e serão ignorados se seguirem as seguintes regras (a menos que eles definam tipos).</span><span class="sxs-lookup"><span data-stu-id="ede8a-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="ede8a-271">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-271">Attribute</span></span>|<span data-ttu-id="ede8a-272">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="ede8a-273">Deve ser false para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="ede8a-274">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="ede8a-275">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="ede8a-276">Deve ser false para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="ede8a-277">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="ede8a-278">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="ede8a-279">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-279">Supported.</span></span> <span data-ttu-id="ede8a-280">Consulte a definição de GEDs associada.</span><span class="sxs-lookup"><span data-stu-id="ede8a-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="ede8a-281">Deve ser verdadeiro para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="ede8a-282">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="ede8a-283">Com suporte, e deve corresponder ao tipo associado para GEDs associado (a menos que o elemento contenha um tipo anônimo).</span><span class="sxs-lookup"><span data-stu-id="ede8a-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="ede8a-284">\<xs: element >: Contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="ede8a-285">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-285">Contents</span></span>|<span data-ttu-id="ede8a-286">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="ede8a-287">Com suporte. \*</span><span class="sxs-lookup"><span data-stu-id="ede8a-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="ede8a-288">Com suporte. \*</span><span class="sxs-lookup"><span data-stu-id="ede8a-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="ede8a-289">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="ede8a-290">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="ede8a-291">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-291">Ignored.</span></span>|
|<span data-ttu-id="ede8a-292">(blank)</span><span class="sxs-lookup"><span data-stu-id="ede8a-292">(blank)</span></span>|<span data-ttu-id="ede8a-293">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-293">Supported.</span></span>|

<span data-ttu-id="ede8a-294">\* ao usar o `simpleType` e o mapeamento de `complexType,` para tipos anônimos é o mesmo para tipos não anônimos, exceto que não há nenhum contrato de dados anônimo e, portanto, um contrato de dados nomeado é criado, com um nome gerado derivado do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="ede8a-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="ede8a-295">As regras para tipos anônimos estão na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede8a-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="ede8a-296">Detalhe de implementação do WCF: se o nome da `xs:element` não contiver pontos, o tipo anônimo será mapeado para um tipo interno do tipo de contrato de dados externo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="ede8a-297">Se o nome contiver pontos, o tipo de contrato de dados resultante será independente (não um tipo interno).</span><span class="sxs-lookup"><span data-stu-id="ede8a-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="ede8a-298">O nome do contrato de dados gerado do tipo interno é o nome do contrato de dados do tipo externo seguido de um ponto, o nome do elemento e a cadeia de caracteres "tipo".</span><span class="sxs-lookup"><span data-stu-id="ede8a-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="ede8a-299">Se já existir um contrato de dados com esse nome, o nome será exclusivo acrescentando "1", "2", "3" e assim por diante até que um nome exclusivo seja criado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="ede8a-300">Tipos simples-\<xs: simpleType ></span><span class="sxs-lookup"><span data-stu-id="ede8a-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="ede8a-301">\<xs: simpleType >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="ede8a-302">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-302">Attribute</span></span>|<span data-ttu-id="ede8a-303">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="ede8a-304">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="ede8a-305">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="ede8a-306">Com suporte, é mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="ede8a-307">\<xs:simpleType>: contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="ede8a-308">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-308">Contents</span></span>|<span data-ttu-id="ede8a-309">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="ede8a-310">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-310">Supported.</span></span> <span data-ttu-id="ede8a-311">Mapeia para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="ede8a-312">Esse atributo será ignorado se não corresponder ao padrão de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="ede8a-313">Consulte a seção restrições de `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="ede8a-314">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-314">Supported.</span></span> <span data-ttu-id="ede8a-315">Mapeia para sinalizar contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="ede8a-316">Consulte a seção listas de `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="ede8a-317">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-317">Forbidden.</span></span>|

### <a name="xsrestriction"></a><span data-ttu-id="ede8a-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="ede8a-318">\<xs:restriction></span></span>

- <span data-ttu-id="ede8a-319">Há suporte para restrições de tipo complexo somente para base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="ede8a-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="ede8a-320">As restrições de tipo simples de `xs:string` que não têm facetas de restrição que não sejam `xs:enumeration` são mapeadas para os contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="ede8a-321">Todas as outras restrições de tipo simples são mapeadas para os tipos que elas restringem.</span><span class="sxs-lookup"><span data-stu-id="ede8a-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="ede8a-322">Por exemplo, uma restrição de `xs:int` é mapeada para um inteiro, assim como `xs:int`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="ede8a-323">Para obter mais informações sobre mapeamento de tipo primitivo, consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="ede8a-324">\<xs: Restriction >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="ede8a-325">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-325">Attribute</span></span>|<span data-ttu-id="ede8a-326">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="ede8a-327">Deve ser um tipo simples ou `xs:anyType`com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="ede8a-328">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="ede8a-329">\<xs: Restriction > para todos os outros casos: conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="ede8a-330">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-330">Contents</span></span>|<span data-ttu-id="ede8a-331">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="ede8a-332">Se presente, deve ser derivado de um tipo primitivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="ede8a-333">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="ede8a-334">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="ede8a-335">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="ede8a-336">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="ede8a-337">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="ede8a-338">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="ede8a-339">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="ede8a-340">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="ede8a-341">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="ede8a-342">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="ede8a-343">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="ede8a-344">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-344">Ignored.</span></span>|
|<span data-ttu-id="ede8a-345">(blank)</span><span class="sxs-lookup"><span data-stu-id="ede8a-345">(blank)</span></span>|<span data-ttu-id="ede8a-346">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="ede8a-347">Enumeração</span><span class="sxs-lookup"><span data-stu-id="ede8a-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="ede8a-348">\<xs: Restriction > para enumerações: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="ede8a-349">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-349">Attribute</span></span>|<span data-ttu-id="ede8a-350">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="ede8a-351">Se presente, deve ser `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="ede8a-352">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="ede8a-353">\<xs: Restriction > para enumerações: Contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="ede8a-354">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-354">Contents</span></span>|<span data-ttu-id="ede8a-355">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="ede8a-356">Se presente, deve ser uma restrição de enumeração com suporte do contrato de dados (esta seção).</span><span class="sxs-lookup"><span data-stu-id="ede8a-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="ede8a-357">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="ede8a-358">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="ede8a-359">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="ede8a-360">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="ede8a-361">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="ede8a-362">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="ede8a-363">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="ede8a-364">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="ede8a-365">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="ede8a-366">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-366">Supported.</span></span> <span data-ttu-id="ede8a-367">A enumeração "ID" é ignorada e "valor" é mapeado para o nome do valor no contrato de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="ede8a-368">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="ede8a-369">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-369">Forbidden.</span></span>|
|<span data-ttu-id="ede8a-370">(vazio)</span><span class="sxs-lookup"><span data-stu-id="ede8a-370">(empty)</span></span>|<span data-ttu-id="ede8a-371">Com suporte, mapeia para o tipo de enumeração vazio.</span><span class="sxs-lookup"><span data-stu-id="ede8a-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="ede8a-372">O código a seguir mostra C# uma classe de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="ede8a-373">Essa classe é mapeada para o esquema a seguir pelo `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="ede8a-374">Se os valores de enumeração começarem de 1, os blocos de `xs:annotation` não serão gerados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a><span data-ttu-id="ede8a-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="ede8a-375">\<xs:list></span></span>

<span data-ttu-id="ede8a-376">`DataContractSerializer` mapeia os tipos de enumeração marcados com `System.FlagsAttribute` para `xs:list` derivados de `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="ede8a-377">Não há suporte para outras variações de `xs:list`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-377">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="ede8a-378">\<xs: list >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-378">\<xs:list>: attributes</span></span>

|<span data-ttu-id="ede8a-379">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-379">Attribute</span></span>|<span data-ttu-id="ede8a-380">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-380">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="ede8a-381">Negado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-381">Forbidden.</span></span>|
|`id`|<span data-ttu-id="ede8a-382">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-382">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="ede8a-383">\<xs: list >: Contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-383">\<xs:list>: contents</span></span>

|<span data-ttu-id="ede8a-384">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-384">Contents</span></span>|<span data-ttu-id="ede8a-385">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-385">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="ede8a-386">Deve ser restrição de `xs:string` usando `xs:enumeration` faceta.</span><span class="sxs-lookup"><span data-stu-id="ede8a-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="ede8a-387">Se o valor de enumeração não seguir uma potência de 2 progressão (padrão para sinalizadores), o valor será armazenado no elemento `xs:annotation/xs:appInfo/ser:EnumerationValue`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="ede8a-388">Por exemplo, o código a seguir sinaliza um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ede8a-388">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="ede8a-389">Esse tipo é mapeado para o esquema a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-389">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="ede8a-390">{1&gt;Herança&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ede8a-390">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="ede8a-391">Regras gerais</span><span class="sxs-lookup"><span data-stu-id="ede8a-391">General rules</span></span>

<span data-ttu-id="ede8a-392">Um contrato de dados pode herdar de outro contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="ede8a-393">Esses contratos de dados são mapeados para uma base e são derivados por tipos de extensão usando a construção de esquema `<xs:extension>` XML.</span><span class="sxs-lookup"><span data-stu-id="ede8a-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="ede8a-394">Um contrato de dados não pode herdar de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="ede8a-394">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="ede8a-395">Por exemplo, o código a seguir é um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-395">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="ede8a-396">Este contrato de dados é mapeado para a seguinte declaração de tipo de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="ede8a-396">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="ede8a-397">\<xs: complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-397">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="ede8a-398">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-398">Attribute</span></span>|<span data-ttu-id="ede8a-399">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-399">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="ede8a-400">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-400">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="ede8a-401">Deve ser false.</span><span class="sxs-lookup"><span data-stu-id="ede8a-401">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="ede8a-402">\<xs: complexContent >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-402">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="ede8a-403">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ede8a-403">Contents</span></span>|<span data-ttu-id="ede8a-404">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-404">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="ede8a-405">Proibido, exceto quando base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="ede8a-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="ede8a-406">O último é equivalente a colocar o conteúdo do `xs:restriction` diretamente sob o contêiner do `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="ede8a-407">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-407">Supported.</span></span> <span data-ttu-id="ede8a-408">Mapeia para herança de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-408">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="ede8a-409">\<xs: Extension > em \<xs: complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="ede8a-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="ede8a-410">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede8a-410">Attribute</span></span>|<span data-ttu-id="ede8a-411">Schema</span><span class="sxs-lookup"><span data-stu-id="ede8a-411">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="ede8a-412">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-412">Ignored.</span></span>|
|`base`|<span data-ttu-id="ede8a-413">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-413">Supported.</span></span> <span data-ttu-id="ede8a-414">Mapeia para o tipo de contrato de dados base do qual este tipo herda.</span><span class="sxs-lookup"><span data-stu-id="ede8a-414">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="ede8a-415">\<xs: Extension > em \<xs: complexContent >: Contents</span><span class="sxs-lookup"><span data-stu-id="ede8a-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="ede8a-416">As regras são as mesmas para `<xs:complexType>` conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-416">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="ede8a-417">Se um `<xs:sequence>` for fornecido, seus elementos de membro serão mapeados para membros de dados adicionais que estão presentes no contrato de dados derivado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="ede8a-418">Se um tipo derivado contiver um elemento com o mesmo nome de um elemento em um tipo base, a declaração de elemento duplicado será mapeada para um membro de dados com um nome que é gerado para ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="ede8a-419">Números inteiros positivos são adicionados ao nome do membro de dados ("member1", "membro2" e assim por diante) até que um nome exclusivo seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="ede8a-420">Por outro lado</span><span class="sxs-lookup"><span data-stu-id="ede8a-420">Conversely:</span></span>

- <span data-ttu-id="ede8a-421">Se um contrato de dados derivado tiver um membro de dados com o mesmo nome e tipo como um membro de dados em um contrato de dados base, `DataContractSerializer` gerará esse elemento correspondente no tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="ede8a-422">Se um contrato de dados derivado tiver um membro de dados com o mesmo nome que um membro de dados em um contrato de dados base, mas um tipo diferente, o `DataContractSerializer` importará um esquema com um elemento do tipo `xs:anyType` no tipo base e nas declarações de tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="ede8a-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="ede8a-423">O nome do tipo original é preservado no `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="ede8a-424">Ambas as variações podem levar a um esquema com um modelo de conteúdo ambíguo, que depende da ordem dos respectivos membros de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="ede8a-425">Mapeamento de tipo/primitivo</span><span class="sxs-lookup"><span data-stu-id="ede8a-425">Type/primitive mapping</span></span>

<span data-ttu-id="ede8a-426">O `DataContractSerializer` usa o mapeamento a seguir para tipos primitivos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="ede8a-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="ede8a-427">Tipo XSD</span><span class="sxs-lookup"><span data-stu-id="ede8a-427">XSD type</span></span>|<span data-ttu-id="ede8a-428">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="ede8a-428">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="ede8a-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-429"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="ede8a-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-430"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="ede8a-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-431"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="ede8a-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-432"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="ede8a-433"><xref:System.DateTime> e <xref:System.TimeSpan> para o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="ede8a-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="ede8a-434">Consulte a serialização de DateTimeOffset abaixo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-434">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="ede8a-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-435"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="ede8a-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-436"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="ede8a-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-437"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="ede8a-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-438"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="ede8a-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-439"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="ede8a-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-440"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="ede8a-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-441"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="ede8a-442">Matriz <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-442"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="ede8a-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-443"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="ede8a-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-444"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="ede8a-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-445"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="ede8a-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-446"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="ede8a-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="ede8a-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-448"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="ede8a-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-449"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="ede8a-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-450"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="ede8a-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-451"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="ede8a-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-452"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="ede8a-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-453"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="ede8a-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-454"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="ede8a-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-455"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="ede8a-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-456"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="ede8a-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-457"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="ede8a-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-458"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="ede8a-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-459"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="ede8a-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-460"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="ede8a-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-461"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="ede8a-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-462"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="ede8a-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-463"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="ede8a-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-464"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="ede8a-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-465"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="ede8a-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-466"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="ede8a-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-467"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="ede8a-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-468"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="ede8a-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-469"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="ede8a-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-470"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="ede8a-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-471"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="ede8a-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-472"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="ede8a-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-473"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="ede8a-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-474"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="ede8a-475">Mapeamento de tipos ISerializable</span><span class="sxs-lookup"><span data-stu-id="ede8a-475">ISerializable types mapping</span></span>

<span data-ttu-id="ede8a-476">Na versão .NET Framework 1,0, <xref:System.Runtime.Serialization.ISerializable> foi introduzido como um mecanismo geral para serializar objetos para persistência ou transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="ede8a-476">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="ede8a-477">Há muitos tipos de .NET Framework que implementam `ISerializable` e que podem ser passados entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ede8a-477">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="ede8a-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturalmente fornece suporte para classes de `ISerializable`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="ede8a-479">O `DataContractSerializer` mapeia `ISerializable` tipos de esquema de implementação que diferem apenas pelo QName (nome qualificado) do tipo e são efetivamente coleções de propriedades.</span><span class="sxs-lookup"><span data-stu-id="ede8a-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="ede8a-480">Por exemplo, o `DataContractSerializer` mapeia <xref:System.Exception> para o seguinte tipo XSD no namespace `http://schemas.datacontract.org/2004/07/System`.</span><span class="sxs-lookup"><span data-stu-id="ede8a-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="ede8a-481">O atributo opcional `ser:FactoryType` declarado no esquema de serialização do contrato de dados faz referência a uma classe de fábrica que pode desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="ede8a-482">A classe de fábrica deve fazer parte da coleção de tipos conhecidos da instância de `DataContractSerializer` que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="ede8a-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="ede8a-483">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="ede8a-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="ede8a-484">Esquema de serialização DataContract</span><span class="sxs-lookup"><span data-stu-id="ede8a-484">DataContract Serialization Schema</span></span>

<span data-ttu-id="ede8a-485">Vários esquemas exportados pelo `DataContractSerializer` usam tipos, elementos e atributos de um namespace de serialização de contrato de dados especial:</span><span class="sxs-lookup"><span data-stu-id="ede8a-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="ede8a-486">A seguir está uma declaração de esquema de serialização de contrato de dados completa.</span><span class="sxs-lookup"><span data-stu-id="ede8a-486">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="ede8a-487">O seguinte deve ser observado:</span><span class="sxs-lookup"><span data-stu-id="ede8a-487">The following should be noted:</span></span>

- <span data-ttu-id="ede8a-488">`ser:char` é introduzido para representar caracteres Unicode do tipo <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="ede8a-489">O `valuespace` de `xs:duration` é reduzido a um conjunto ordenado para que ele possa ser mapeado para um <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="ede8a-490">`FactoryType` é usado em esquemas exportados de tipos que são derivados de <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="ede8a-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="ede8a-491">Importando esquemas não DataContract</span><span class="sxs-lookup"><span data-stu-id="ede8a-491">Importing non-DataContract schemas</span></span>

<span data-ttu-id="ede8a-492">`DataContractSerializer` tem a opção `ImportXmlTypes` para permitir a importação de esquemas que não estão de acordo com o perfil XSD `DataContractSerializer` (consulte a propriedade <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>).</span><span class="sxs-lookup"><span data-stu-id="ede8a-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="ede8a-493">Definir essa opção como `true` permite a aceitação de tipos de esquema não conformes e o mapeamento para a implementação a seguir, <xref:System.Xml.Serialization.IXmlSerializable> encapsulando uma matriz de <xref:System.Xml.XmlNode> (somente o nome da classe difere).</span><span class="sxs-lookup"><span data-stu-id="ede8a-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="ede8a-494">Serialização de DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ede8a-494">DateTimeOffset Serialization</span></span>

<span data-ttu-id="ede8a-495">O <xref:System.DateTimeOffset> não é tratado como um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="ede8a-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="ede8a-496">Em vez disso, ele é serializado como um elemento complexo com duas partes.</span><span class="sxs-lookup"><span data-stu-id="ede8a-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="ede8a-497">A primeira parte representa a data e hora, e a segunda parte representa o deslocamento a partir da data e hora.</span><span class="sxs-lookup"><span data-stu-id="ede8a-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="ede8a-498">Um exemplo de um valor de DateTimeOffset serializado é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede8a-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="ede8a-499">O esquema é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="ede8a-499">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="ede8a-500">Veja também</span><span class="sxs-lookup"><span data-stu-id="ede8a-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="ede8a-501">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="ede8a-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
