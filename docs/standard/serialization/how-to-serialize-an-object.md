---
title: Como serializar um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 3e24d890d47747c51086214530073fc551321079
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159878"
---
# <a name="how-to-serialize-an-object"></a>Como serializar um objeto
Para serializar um objeto, primeiro crie o objeto a ser serializado e defina seus campos e propriedades públicos. Para fazer isso, você deve determinar o formato de transporte em que o fluxo XML deve ser armazenado: como um fluxo ou como um arquivo. Por exemplo, se o fluxo XML precisar ser salvo de uma forma permanente, crie um objeto <xref:System.IO.FileStream>.  
  
> [!NOTE]
> Para obter mais exemplos de serialização XML, consulte [Exemplos de Serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Para serializar um objeto  
  
1. Crie o objeto e defina seus campos e propriedades públicos.  
  
2. Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto. Para obter mais informações, consulte os construtores da classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
3. Chame o método <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> para gerar um fluxo XML ou uma representação em arquivo de propriedades e campos públicos do objeto. O exemplo a seguir cria um arquivo.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Veja também

- [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
