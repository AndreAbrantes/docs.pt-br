---
title: Lendo um documento XML no DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130838"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Lendo um documento XML no DOM
As informações XML são lidas na memória em diferentes formatos. Podem ser lidas de uma cadeia de caracteres, de um fluxo, de uma URL, de um leitor de texto ou de uma classe derivada de <xref:System.Xml.XmlReader>.  
  
 O método <xref:System.Xml.XmlDocument.Load%2A> leva o documento para a memória e tem métodos sobrecarregados disponíveis para utilizar dados de cada um dos diferentes formatos. Existe também um método <xref:System.Xml.XmlDocument.LoadXml%2A> que lê XML de uma cadeia de caracteres.  
  
 Diferentes métodos de <xref:System.Xml.XmlDocument.Load%2A> afetam os nós que são criados quando o DOM (Document Object Model) é carregado. A tabela a seguir lista as diferenças entre alguns dos métodos de <xref:System.Xml.XmlDocument.Load%2A> e os tópicos que os abordam.  
  
|Assunto|Tópico|  
|-------------|-----------|  
|Criação de nós de espaços em branco|O objeto usado para carregar o DOM tem um efeito no espaço em branco e nos nós de espaço em branco significativos gerados no DOM. Para saber mais, confira [Espaço em branco e tratamento de espaço em branco significativo ao carregar o DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Carregando o XML a partir de um nó específico ou carregando todo o documento XML|Ao usar o método <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType>, os dados podem ser carregados de um nó específico no DOM. Confira mais informações em [Carregar dados de um leitor](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Validando o XML à medida que é carregado|Os dados XML carregados no DOM podem ser validados à medida que são carregados. Isso é feito usando um <xref:System.Xml.XmlReader> de validação. Confira mais informações sobre como validar um XML quando ele é carregado em [Validando um documento XML no DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 O exemplo a seguir mostra o XML que está sendo carregado com o método <xref:System.Xml.XmlDocument.LoadXml%2A> e os dados salvos subsequentemente em um arquivo de texto chamado `data.xml`.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>Veja também

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
