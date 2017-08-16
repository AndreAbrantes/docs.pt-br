---
title: 'Como: escrever consultas no XML nos Namespaces (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5af26b7ec0a2ab465917cd0ee62f65a97f5f0e40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Como: escrever consultas no XML nos Namespaces (Visual Basic)
Para escrever uma consulta em XML que está em um namespace, você deve usar <xref:System.Xml.Linq.XName>objetos que têm o namespace correto.</xref:System.Xml.Linq.XName>  
  
 No Visual Basic, a abordagem mais comum é definir um namespace global e, em seguida, usar os literais XML e as propriedades XML que usam o namespace global. Você pode definir um namespace global padrão nesse caso, no qual os elementos nos literais XML estarão no namespace por padrão. Como alternativa, você pode definir um namespace global com um prefixo e, em seguida, usar o prefixo como necessário nos literais XML e nas propriedades XML. Como ocorre com outros formatos de XML, os atributos estão sempre em nenhum namespace por padrão.  
  
 O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão. O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma árvore XML que está em um namespace padrão. Ele então recupera uma coleção de elementos.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Exemplo  
 No Visual Basic, no entanto, escrever consultas em uma árvore XML que usa um namespace com um prefixo é bastante suficiente de consultar uma árvore XML em um namespace padrão. Normalmente você usa a instrução `Imports` para importar o namespace com um prefixo. Você em seguida usa o prefixo em nomes de elementos e atributos quando constrói a árvore XML. Você também usa o prefixo para consultar uma árvore XML usando propriedades XML.  
  
 O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo. Ele então recupera uma coleção de elementos.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
