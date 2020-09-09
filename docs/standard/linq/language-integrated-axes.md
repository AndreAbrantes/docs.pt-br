---
title: Eixos integrados à linguagem no Visual Basic-LINQ to XML
description: LINQ to XML fornece acesso fácil ao XML usando os eixos integrados ao Visual Basic
ms.date: 07/20/2015
ms.assetid: d450a556-a134-4261-b011-44e399660894
ms.openlocfilehash: 75c3063806e7e3dc1633e78ca25f1f6afc3e7ae3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551987"
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="d74e4-103">Eixos integrados à linguagem em Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d74e4-103">Language-integrated axes in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="d74e4-104">Os recursos do Axis são integrados ao Visual Basic, facilitando o acesso a XML.</span><span class="sxs-lookup"><span data-stu-id="d74e4-104">Axis features are integrated into Visual Basic, making it easy to access XML.</span></span> <span data-ttu-id="d74e4-105">Muitos dos exemplos na documentação do LINQ to XML usam esses recursos, que são descritos nos artigos listados nesta tabela:</span><span class="sxs-lookup"><span data-stu-id="d74e4-105">Many of the examples in the LINQ to XML documentation use these features, which are described in the articles listed in this table:</span></span>

|<span data-ttu-id="d74e4-106">Artigo</span><span class="sxs-lookup"><span data-stu-id="d74e4-106">Article</span></span>|<span data-ttu-id="d74e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d74e4-107">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="d74e4-108">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="d74e4-108">XML Child Axis Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="d74e4-109">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="d74e4-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="d74e4-110">Esse eixo é equivalente ao eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="d74e4-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|
|[<span data-ttu-id="d74e4-111">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="d74e4-111">XML Descendant Axis Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="d74e4-112">Fornece acesso aos descendentes dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , ou uma coleção de <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="d74e4-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d74e4-113">Esse eixo é equivalente ao eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="d74e4-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|
|[<span data-ttu-id="d74e4-114">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="d74e4-114">XML Attribute Axis Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="d74e4-115">Fornece acesso a um atributo de um objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d74e4-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="d74e4-116">Esse eixo é aproximadamente equivalente ao eixo de <xref:System.Xml.Linq.XElement.Attribute%2A> .</span><span class="sxs-lookup"><span data-stu-id="d74e4-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="d74e4-117">Esse eixo difere do eixo de <xref:System.Xml.Linq.XElement.Attribute%2A> que retorna o valor do atributo, não um objeto de <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d74e4-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|
|[<span data-ttu-id="d74e4-118">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="d74e4-118">Extension Indexer Property</span></span>](../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="d74e4-119">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="d74e4-119">Provides access to individual elements in a collection.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d74e4-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="d74e4-120">See also</span></span>

- [<span data-ttu-id="d74e4-121">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="d74e4-121">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)