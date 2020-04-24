---
title: Digite suporte nas classes de System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710096"
---
# <a name="type-support-in-the-systemxml-classes"></a>Digite suporte nas classes de System.Xml
No .NET Framework versão 2,0, as classes XML principais foram aprimoradas para incluir recursos de suporte de tipo. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> incluem recursos de suporte do tipo que incluem a capacidade de conversão entre tipos esquema XML e Common Language Runtime (CLR) tipos.  
  
 No .NET Framework versão 2,0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> foram aprimorados para incluir recursos de suporte do tipo.  
  
- As classes <xref:System.Xml.XmlReader> e <xref:System.Xml.XPath.XPathNavigator> incluem uma propriedade **SchemaInfo** que retorna informações de esquema em um nó.  
  
- **ReadContentAs** e **ReadElementContentAs** e os métodos na classe <xref:System.Xml.XmlReader> leem um valor de texto e o convertem em um valor de CLR em uma única chamada de método.  
  
- O método de <xref:System.Xml.XmlWriter.WriteValue%2A> na classe de <xref:System.Xml.XmlWriter> converter um tipo de CLR a um tipo de esquema XML para gravar XML.  
  
- As propriedades **ValueAs** e <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> na classe <xref:System.Xml.XPath.XPathNavigator> retornam um valor do nó e o convertem em um valor de CLR em uma única chamada de método.  
  
> [!NOTE]
> Na versão 1,0 do.NET Framework a classe de <xref:System.Xml.XmlConvert> foi necessária para converter entre o esquema XML e os tipos de CLR.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tipos de dados XML de mapeamento para tipos de CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Descreve os mapeamentos padrão de tipos de dados XML para tipos de CLR.  
  
 [Notas de implementação de suporte do tipo XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Descreve alguns dos detalhes de implementação de suporte de tipo.  
  
 [Conversão de tipos de dados XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Descreve como usar a classe de <xref:System.Xml.XmlConvert> para converter entre o esquema XML e os tipos de CLR.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Acessando dados fortemente tipados XML usando XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
