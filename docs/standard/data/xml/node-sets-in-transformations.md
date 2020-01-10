---
title: Conjuntos de nó nas transformações
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 2828b95f6a4050dd05b38e7ab6ef740ee4eb16b4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710551"
---
# <a name="node-sets-in-transformations"></a>Conjuntos de nó nas transformações
Conjuntos de nó é um dos quatro tipos de dados básicos que são retornados das expressões de idioma do caminho de XML (XPath). Um conjunto de nó, que é uma coleção não ordenada de nós sem duplicatas, criada na ordem de documento, pode ser atribuído a um variável em uma folha de estilos.  
  
> [!NOTE]
> A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.  
  
 Conjuntos de nó é um dos quatro tipos de dados básicos que são retornados de expressões XPath. Um conjunto de nó, que é uma coleção não ordenada de nós sem duplicatas, criada na ordem de documento, pode ser atribuído a um variável em uma folha de estilos. Este conjunto de nó, que é um resultado de uma expressão XPath usado em um atributo de `select` em uma transformação, tem o mesmo comportamento que um nó definir o modelo de objeto (DOM) de documento XML. Você pode navegar em um conjunto de nós usando um conjunto de métodos mostrados em [Navegação do nó usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), diferentemente de um fragmento de árvore de resultado, que usa <xref:System.Xml.XPath.XPathNodeIterator> para navegação.  
  
 O exemplo de código a seguir mostra como iterar sobre um nó definida quando um elemento de `variable` ou de `parameter` em uma folha de estilos é avaliada como um conjunto de nó.  
  
## <a name="style-sheet"></a>Folha de Estilos  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Entrada  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Saída  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [A classe XslTransform implementa o processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
