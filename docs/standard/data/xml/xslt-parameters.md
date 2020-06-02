---
title: Parâmetros XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282526"
---
# <a name="xslt-parameters"></a><span data-ttu-id="5a6bb-102">Parâmetros XSLT</span><span class="sxs-lookup"><span data-stu-id="5a6bb-102">XSLT Parameters</span></span>
<span data-ttu-id="5a6bb-103">Os parâmetros XSLT são adicionados a <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="5a6bb-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="5a6bb-104">Um nome qualificado e URI de namespace são associados com o objeto de parâmetro no momento.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="5a6bb-105">Para usar um parâmetro XSLT</span><span class="sxs-lookup"><span data-stu-id="5a6bb-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="5a6bb-106">Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o parâmetro usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="5a6bb-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="5a6bb-107">Chame o parâmetro folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="5a6bb-108">Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="5a6bb-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="5a6bb-109">Tipos de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5a6bb-109">Parameter Types</span></span>  
 <span data-ttu-id="5a6bb-110">O objeto de parâmetro deve corresponder a um tipo W3C.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="5a6bb-111">A tabela seguinte mostra tipos correspondentes W3C, as classes equivalentes do Microsoft.NET (tipo), e se o tipo W3C é um tipo XPath ou tipo de fonte.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="5a6bb-112">Tipo W3C</span><span class="sxs-lookup"><span data-stu-id="5a6bb-112">W3C type</span></span>|<span data-ttu-id="5a6bb-113">Classe. NET equivalente (tipo)</span><span class="sxs-lookup"><span data-stu-id="5a6bb-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="5a6bb-114">XPath ou tipo XSLT</span><span class="sxs-lookup"><span data-stu-id="5a6bb-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="5a6bb-115">XPath</span><span class="sxs-lookup"><span data-stu-id="5a6bb-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="5a6bb-116">XPath</span><span class="sxs-lookup"><span data-stu-id="5a6bb-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5a6bb-117">XPath</span><span class="sxs-lookup"><span data-stu-id="5a6bb-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="5a6bb-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="5a6bb-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="5a6bb-119">XPath</span><span class="sxs-lookup"><span data-stu-id="5a6bb-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="5a6bb-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="5a6bb-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="5a6bb-121">XPath</span><span class="sxs-lookup"><span data-stu-id="5a6bb-121">XPath</span></span>|  
  
 <span data-ttu-id="5a6bb-122">os \*This são equivalentes a um nó definida que contém um único nó.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="5a6bb-123">Se o objeto de parâmetro não é uma das classes anterior, ele é convertido de acordo com as regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="5a6bb-124">Os tipos numéricos do Common Language Runtime (CLR) são convertidos a <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="5a6bb-125">O tipo <xref:System.DateTime> é convertido em <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="5a6bb-126">Os tipos <xref:System.Xml.XPath.IXPathNavigable> são convertidos em <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="5a6bb-127">**XPathNavigator[]** é convertido em <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="5a6bb-128">Todos os outros tipos lançam um erro.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a6bb-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a6bb-129">Example</span></span>  
 <span data-ttu-id="5a6bb-130">O exemplo a seguir usa o método de <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> para criar um parâmetro para armazenar calculou a data de desconto.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="5a6bb-131">A data de desconto é calculada para ser a 20 dias de data pedido.</span><span class="sxs-lookup"><span data-stu-id="5a6bb-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="5a6bb-132">Entrada</span><span class="sxs-lookup"><span data-stu-id="5a6bb-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="5a6bb-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="5a6bb-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="5a6bb-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="5a6bb-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="5a6bb-135">Saída</span><span class="sxs-lookup"><span data-stu-id="5a6bb-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a6bb-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="5a6bb-136">See also</span></span>

- [<span data-ttu-id="5a6bb-137">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="5a6bb-137">XSLT Transformations</span></span>](xslt-transformations.md)
