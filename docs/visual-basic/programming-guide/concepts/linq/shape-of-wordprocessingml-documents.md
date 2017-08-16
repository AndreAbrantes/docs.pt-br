---
title: Forma de documentos de WordprocessingML (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e1982110ccf01f52ace20db6985d7329407357d8
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017


---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Forma de documentos de WordprocessingML (Visual Basic)
Este tópico apresenta a forma XML de um documento WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formatos do Microsoft Office  
 O formato de arquivo nativo para o sistema do Microsoft Office 2007 é Office Open XML (geralmente chamado de Open XML). O Open XML é um formato baseado em XML que tem um padrão Ecma e está no momento passando por um processo de padrões de ISO-IEC. A linguagem de marcação para arquivos de processamento de texto dentro do Open XML é chamada de WordprocessingML. Este tutorial usa arquivos de origem do WordprocessingML como entrada para os exemplos.  
  
 Se você estiver usando o Microsoft Office 2003, pode salvar documentos no formato Office Open XML se instalou os formatos de arquivo do Pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>O formato de documentos de WordprocessingML  
 A primeira coisa a entender é a forma dos documentos de WordprocessingML. Um documento de WordprocessingML contém um elemento do corpo (chamado `w:body`) que contém os parágrafos do documento. Cada parágrafo contém uma ou mais execuções de texto (chamado `w:r`). Cada execução de texto contém uma ou mais partes de texto (chamado `w:t`).  
  
 Veja a seguir um documento muito simples de WordprocessingML:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 Este documento contém dois parágrafos. Ambos contêm uma única execução de texto, e cada execução de texto contém uma única parte de texto.  
  
 A maneira mais fácil para ver o conteúdo de um documento de WordprocessingML no formato XML é criar um usando Microsoft Word, salvá-lo e executar o seguinte programa que lê XML no console.  
  
 Este exemplo usa as classes encontradas no assembly WindowsBase. Ele usa tipos no <xref:System.IO.Packaging?displayProperty=fullName>namespace.</xref:System.IO.Packaging?displayProperty=fullName>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a>Recursos externos  
 [Introduzindo os formatos de arquivo do Office (2007) Open XML](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [Visão geral de WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [Office 2003: Página de Download de esquemas de referência XML](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

