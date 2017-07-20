---
title: "Visão geral dos eixos LINQ to XML (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ec77ddc5cf689fc0bcc4cf9faddb00201ca7b721
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017


---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>Visão geral dos eixos LINQ to XML (Visual Basic)
Após criar uma árvore XML ou carregar um documento XML em uma árvore XML, você poderá consultá-la para localizar elementos e atributos, e recuperar seus valores. Você recupera coleções por meio dos *métodos de eixo*, também denominados *eixos*. Alguns eixos são métodos nas classes <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XDocument> que retornam coleções <xref:System.Collections.Generic.IEnumerable%601>. Alguns eixos são métodos de extensão na classe <xref:System.Xml.Linq.Extensions>. Os eixos implementados como métodos de extensão operam em coleções e retornam coleções.  
  
 Conforme descrito em [Visão geral da classe XElement](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), um objeto <xref:System.Xml.Linq.XElement> representa um nó de um único elemento. O conteúdo de um elemento pode ser complexo (às vezes denominado conteúdo estruturado) ou pode ser um elemento simples. Um elemento simples pode ser vazio ou conter um valor. Se o nó contiver o conteúdo estruturado, você poderá usar os vários métodos de eixo para recuperar enumerações de elementos descendentes. Os métodos de eixo mais usados do eixo são <xref:System.Xml.Linq.XContainer.Elements%2A> e <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Além dos métodos de eixo, que retornam coleções, há mais dois métodos que você geralmente usa nas consultas do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. O método <xref:System.Xml.Linq.XContainer.Element%2A> retorna um <xref:System.Xml.Linq.XElement> único. O método <xref:System.Xml.Linq.XElement.Attribute%2A> retorna um <xref:System.Xml.Linq.XAttribute> único.  
  
 Em várias circunstâncias, as consultas do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fornecem a maneira mais eficiente de examinar uma árvore, extrair dados dela e transformá-la. As consultas do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] operam em objetos que implementam o <xref:System.Collections.Generic.IEnumerable%601>, e os eixos do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] retornam o <xref:System.Collections.Generic.IEnumerable%601> das coleções <xref:System.Xml.Linq.XElement> e o <xref:System.Collections.Generic.IEnumerable%601> das coleções <xref:System.Xml.Linq.XAttribute>. Você precisa dessas coleções para executar suas consultas.  
  
 Além dos métodos de eixo que recuperam coleções de elementos e atributos, há métodos de eixo que permitem a você iterar na árvore detalhadamente. Por exemplo, em vez de tratar elementos e atributos, você pode trabalhar com os nós da árvore. Os nós são um nível mais refinado de granularidade do que os elementos e os atributos. Ao trabalhar com os nós, você pode examinar comentários XML, nós de texto, instruções de processamento e muito mais. Essa funcionalidade é importante, por exemplo, para alguém que estiver escrevendo em um processador de texto e deseja salvar documentos como XML. No entanto, a maioria dos programadores XML se preocupam basicamente com os elementos, os atributos e seus valores.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Métodos para recuperar uma coleção de elementos  
 Este é um resumo dos métodos da classe <xref:System.Xml.Linq.XElement> (ou de suas classes base) que você chama em um <xref:System.Xml.Linq.XElement> para retornar uma coleção de elementos.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos ancestrais desse elemento. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos ancestrais que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos descendentes desse elemento. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos descendentes que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos filho desse elemento. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos filho que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos que vêm após esse elemento. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos após esse elemento que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos que vêm antes desse elemento. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos antes desse elemento que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos e seus ancestrais. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos que têm o <xref:System.Xml.Linq.XName> especificado.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> desse elemento e seus descendentes. Uma sobrecarga retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> dos elementos que têm o <xref:System.Xml.Linq.XName> especificado.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Método para recuperar um único elemento  
 O método a seguir recupera um único filho de um objeto <xref:System.Xml.Linq.XElement>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|Retorna o primeiro objeto filho <xref:System.Xml.Linq.XElement> que tem o <xref:System.Xml.Linq.XName> especificado.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Método para recuperar uma coleção de atributos  
 O método a seguir recupera atributos de um objeto <xref:System.Xml.Linq.XElement>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|Retorna um <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XAttribute> de todos os atributos.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Método para recuperar um único atributo  
 O método a seguir recupera um único atributo de um objeto <xref:System.Xml.Linq.XElement>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|Retorna o <xref:System.Xml.Linq.XAttribute> que tem o <xref:System.Xml.Linq.XName> especificado.|  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
