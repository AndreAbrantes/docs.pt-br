---
title: Regras para inferir tipos de nó e estrutura de esquema
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: e49e50dc21951d739b12cdfa60c6a48f67576873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697591"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="cf319-102">Regras para inferir tipos de nó e estrutura de esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-102">Rules for Inferring Schema Node Types and Structure</span></span>

<span data-ttu-id="cf319-103">Este tópico descreve como o processo de inferência de esquema converte os tipos de nós em um documento XML a estrutura do idioma da definição de esquema XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="cf319-103">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="cf319-104">Regras de inferência de elemento</span><span class="sxs-lookup"><span data-stu-id="cf319-104">Element Inference Rules</span></span>  

 <span data-ttu-id="cf319-105">Esta seção descreve as regras de inferência para declarações elemento.</span><span class="sxs-lookup"><span data-stu-id="cf319-105">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="cf319-106">Há oito estruturas das declarações de elemento que serão inferidas:</span><span class="sxs-lookup"><span data-stu-id="cf319-106">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="cf319-107">Elemento do tipo simples</span><span class="sxs-lookup"><span data-stu-id="cf319-107">Element of simple type</span></span>  
  
2. <span data-ttu-id="cf319-108">Elemento vazio</span><span class="sxs-lookup"><span data-stu-id="cf319-108">Empty element</span></span>  
  
3. <span data-ttu-id="cf319-109">Elemento vazio com atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-109">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="cf319-110">Elemento com atributos e conteúdo simples</span><span class="sxs-lookup"><span data-stu-id="cf319-110">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="cf319-111">Elemento com uma sequência de elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf319-111">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="cf319-112">Elemento com uma sequência de elementos filho e atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-112">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="cf319-113">Elemento com uma sequência das opções de elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf319-113">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="cf319-114">Elemento com uma sequência das opções de elementos filho e atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-114">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf319-115">Todas as declarações de `complexType` são inferidas como tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="cf319-115">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="cf319-116">O único elemento global é inferido o elemento raiz; todos os outros elementos são locais.</span><span class="sxs-lookup"><span data-stu-id="cf319-116">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="cf319-117">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-117">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="cf319-118">Elemento tipado simples</span><span class="sxs-lookup"><span data-stu-id="cf319-118">Simple Typed Element</span></span>  

 <span data-ttu-id="cf319-119">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-119">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-120">O elemento negrito mostra o esquema inferido para o elemento de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="cf319-120">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="cf319-121">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-121">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-122">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-122">XML</span></span>|<span data-ttu-id="cf319-123">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-123">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="cf319-124">Elemento vazio</span><span class="sxs-lookup"><span data-stu-id="cf319-124">Empty Element</span></span>  

 <span data-ttu-id="cf319-125">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-125">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-126">O elemento negrito mostra o esquema inferido para o elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="cf319-126">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="cf319-127">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-127">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-128">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-128">XML</span></span>|<span data-ttu-id="cf319-129">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-129">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="cf319-130">Elemento vazio com atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-130">Empty Element with Attributes</span></span>  

 <span data-ttu-id="cf319-131">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-131">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-132">Os elementos negritos mostram o esquema inferido para o elemento vazio com atributos.</span><span class="sxs-lookup"><span data-stu-id="cf319-132">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="cf319-133">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-133">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-134">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-134">XML</span></span>|<span data-ttu-id="cf319-135">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-135">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="cf319-136">Elemento com atributos e conteúdo simples</span><span class="sxs-lookup"><span data-stu-id="cf319-136">Element with Attributes and Simple Content</span></span>  

 <span data-ttu-id="cf319-137">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-137">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-138">Os elementos negritos mostram o esquema inferido para um elemento com atributos e conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="cf319-138">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="cf319-139">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-139">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-140">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-140">XML</span></span>|<span data-ttu-id="cf319-141">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-141">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="cf319-142">Elemento com uma sequência de elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf319-142">Element with a Sequence of Child Elements</span></span>  

 <span data-ttu-id="cf319-143">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-143">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-144">Os elementos negritos mostram o esquema inferido para um elemento com uma sequência de elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="cf319-144">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf319-145">Se um elemento é apenas um elemento filho, ainda é tratado como uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cf319-145">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="cf319-146">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-146">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-147">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-147">XML</span></span>|<span data-ttu-id="cf319-148">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-148">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="cf319-149">Elemento com uma sequência de elementos filho e atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-149">Element with a Sequence of Child Elements and Attributes</span></span>  

 <span data-ttu-id="cf319-150">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-150">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-151">Os elementos negritos mostram o esquema inferido para um elemento com uma sequência de elementos filho e atributos.</span><span class="sxs-lookup"><span data-stu-id="cf319-151">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf319-152">Se um elemento é apenas um elemento filho, ainda é tratado como uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cf319-152">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="cf319-153">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-153">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-154">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-154">XML</span></span>|<span data-ttu-id="cf319-155">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-155">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="cf319-156">Elemento com uma sequência e opções de elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf319-156">Element with a Sequence and Choices of Child Elements</span></span>  

 <span data-ttu-id="cf319-157">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-157">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-158">Os elementos negritos mostram o esquema inferido para um elemento com uma sequência e uma opção de elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="cf319-158">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf319-159">O atributo de `maxOccurs` do elemento de `xs:choice` é definido como `"unbounded"` no esquema inferido.</span><span class="sxs-lookup"><span data-stu-id="cf319-159">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="cf319-160">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-160">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-161">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-161">XML</span></span>|<span data-ttu-id="cf319-162">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-162">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="cf319-163">Elemento com uma sequência e uma escolha dos elementos filho e atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-163">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  

 <span data-ttu-id="cf319-164">A tabela a seguir mostra XML conectado ao método de <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> , e o esquema XML gerado.</span><span class="sxs-lookup"><span data-stu-id="cf319-164">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="cf319-165">Os elementos negritos mostram o esquema inferido para um elemento com uma sequência e uma escolha dos elementos filho e atributos.</span><span class="sxs-lookup"><span data-stu-id="cf319-165">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf319-166">O atributo de `maxOccurs` do elemento de `xs:choice` é definido como `"unbounded"` no esquema inferido.</span><span class="sxs-lookup"><span data-stu-id="cf319-166">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="cf319-167">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-167">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="cf319-168">XML</span><span class="sxs-lookup"><span data-stu-id="cf319-168">XML</span></span>|<span data-ttu-id="cf319-169">Esquema</span><span class="sxs-lookup"><span data-stu-id="cf319-169">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="cf319-170">Processamento de atributos</span><span class="sxs-lookup"><span data-stu-id="cf319-170">Attribute Processing</span></span>  

 <span data-ttu-id="cf319-171">Sempre que um novo atributo é encontrado dentro de um nó, é adicionado à definição inferido do nó com `use="required"`.</span><span class="sxs-lookup"><span data-stu-id="cf319-171">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="cf319-172">Na próxima vez que o mesmo nó é encontrado na instância, o processo de inferência comparará atributos de instância atual com que já inferidas.</span><span class="sxs-lookup"><span data-stu-id="cf319-172">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="cf319-173">Se alguma de inferidos já está ausente na instância, `use="optional"` é adicionado à definição de atributo.</span><span class="sxs-lookup"><span data-stu-id="cf319-173">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="cf319-174">Novos atributos são adicionados às declarações existentes com `use="optional"`.</span><span class="sxs-lookup"><span data-stu-id="cf319-174">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="cf319-175">Restrições de clique</span><span class="sxs-lookup"><span data-stu-id="cf319-175">Occurrence Constraints</span></span>  

 <span data-ttu-id="cf319-176">Durante o processo de inferência de esquema, os atributos de `minOccurs` e de `maxOccurs` são gerados, para componentes inferidos de um esquema, com os valores `"0"` ou `"1"` e `"1"` ou `"unbounded"`.</span><span class="sxs-lookup"><span data-stu-id="cf319-176">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="cf319-177">Os valores `"1"` e `"unbounded"` são usados somente quando valores `"0"` e `"1"` não podem validar o documento XML (por exemplo, se `MinOccurs="0"` não descreve exatamente um elemento, `minOccurs="1"` é usado).</span><span class="sxs-lookup"><span data-stu-id="cf319-177">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="cf319-178">Conteúdo Misto</span><span class="sxs-lookup"><span data-stu-id="cf319-178">Mixed Content</span></span>  

 <span data-ttu-id="cf319-179">Se um elemento contém conteúdo misturado (por exemplo intercalado texto com elementos), o atributo de `mixed="true"` é gerado para a definição de tipo complexo inferido.</span><span class="sxs-lookup"><span data-stu-id="cf319-179">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="cf319-180">Outras regras de inferência de tipo de nó</span><span class="sxs-lookup"><span data-stu-id="cf319-180">Other Node Type Inference Rules</span></span>  

 <span data-ttu-id="cf319-181">A tabela a seguir descreve as regras de inferência para a instrução de processamento, o comentário, a referência de entidade, o CDATA, o tipo de documento, e os nós de namespace.</span><span class="sxs-lookup"><span data-stu-id="cf319-181">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="cf319-182">Tipo de nó</span><span class="sxs-lookup"><span data-stu-id="cf319-182">Node Type</span></span>|<span data-ttu-id="cf319-183">Tradução</span><span class="sxs-lookup"><span data-stu-id="cf319-183">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf319-184">Instrução de processamento</span><span class="sxs-lookup"><span data-stu-id="cf319-184">Processing instruction</span></span>|<span data-ttu-id="cf319-185">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="cf319-185">Ignored.</span></span>|  
|<span data-ttu-id="cf319-186">Comentário</span><span class="sxs-lookup"><span data-stu-id="cf319-186">Comment</span></span>|<span data-ttu-id="cf319-187">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="cf319-187">Ignored.</span></span>|  
|<span data-ttu-id="cf319-188">Referência de entidade</span><span class="sxs-lookup"><span data-stu-id="cf319-188">Entity reference</span></span>|<span data-ttu-id="cf319-189">A classe de <xref:System.Xml.Schema.XmlSchemaInference> não trata referências a entidades.</span><span class="sxs-lookup"><span data-stu-id="cf319-189">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="cf319-190">Se um documento XML contém referências a entidades, você precisará usar um leitor que expande as entidades.</span><span class="sxs-lookup"><span data-stu-id="cf319-190">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="cf319-191">Por exemplo, você pode passar <xref:System.Xml.XmlTextReader> com a propriedade de <xref:System.Xml.XmlTextReader.EntityHandling%2A> definida como <xref:System.Xml.EntityHandling.ExpandEntities> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf319-191">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="cf319-192">Se as referências a entidades são localizadas e o leitor não expande entidades, uma exceção é throw.</span><span class="sxs-lookup"><span data-stu-id="cf319-192">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="cf319-193">CDATA</span><span class="sxs-lookup"><span data-stu-id="cf319-193">CDATA</span></span>|<span data-ttu-id="cf319-194">Todas as seções de `<![CDATA[ … ]]` em um documento XML serão inferidas como `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="cf319-194">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="cf319-195">Tipo de documento</span><span class="sxs-lookup"><span data-stu-id="cf319-195">Document type</span></span>|<span data-ttu-id="cf319-196">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="cf319-196">Ignored.</span></span>|  
|<span data-ttu-id="cf319-197">Namespaces</span><span class="sxs-lookup"><span data-stu-id="cf319-197">Namespaces</span></span>|<span data-ttu-id="cf319-198">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="cf319-198">Ignored.</span></span>|  
  
 <span data-ttu-id="cf319-199">Para saber mais sobre o processo de inferência de esquema, consulte [Inferência de esquemas de documentos XML](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="cf319-199">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf319-200">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf319-200">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="cf319-201">SOM (Schema Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="cf319-201">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="cf319-202">Inferindo um esquema XML</span><span class="sxs-lookup"><span data-stu-id="cf319-202">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="cf319-203">Inferindo esquemas de documentos XML</span><span class="sxs-lookup"><span data-stu-id="cf319-203">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="cf319-204">Regras para inferir tipos simples</span><span class="sxs-lookup"><span data-stu-id="cf319-204">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
