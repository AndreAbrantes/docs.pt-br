---
title: Usando a classe XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 6fc29b523e59590138cb7ca4db1b0da1bfee99c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937940"
---
# <a name="using-the-xslcompiledtransform-class"></a>Usando a classe XslCompiledTransform
A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT do Microsoft .NET Framework. Essa classe é usada para compilar folhas de estilos e executar transformações XSLT.  
  
> [!NOTE]
> Embora o desempenho geral da classe <xref:System.Xml.Xsl.XslCompiledTransform> seja melhor do que o da classe <xref:System.Xml.Xsl.XslTransform>, o método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> da classe <xref:System.Xml.Xsl.XslCompiledTransform> possivelmente apresentará um desempenho mais lento do que o método <xref:System.Xml.Xsl.XslTransform.Load%2A> da classe <xref:System.Xml.Xsl.XslTransform> na primeira vez que for chamado em uma transformação. Isso ocorre porque o arquivo XSLT deve ser compilado antes que seja carregado. Para saber mais, confira a postagem de blog a seguir: [XslCompiledTransform mais lento do que XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Entradas para a classe de XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Descreve as opções de entrada XSLT disponíveis.  
  
 [Opções de saída na classe de XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Descreve as opções de saída XSLT disponíveis.  
  
 [Resolvendo recursos externos durante processamento XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Aborda o uso da classe <xref:System.Xml.XmlResolver> para resolver recursos externos.  
  
 [Estendendo folhas de estilos XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Aborda o suporte às extensões XSLT.  
  
|||  
|-|-|  
|[Erros recuperáveis de XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Lista os comportamentos discricionários permitidos pela recomendação da World Wide Web Consortium (W3C) XSLT 1.0 e descreve como esses comportamentos são tratados pela classe <xref:System.Xml.Xsl.XslCompiledTransform>.|  
|[Como transformar um fragmento do nó](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Descreve como transformar um fragmento de nó.|  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Migrando da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>  
  
## <a name="see-also"></a>Veja também

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
