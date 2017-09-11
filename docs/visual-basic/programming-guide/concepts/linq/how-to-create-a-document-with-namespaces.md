---
title: 'Como: criar um documento com Namespaces (LINQ to XML) (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 60206722fff1d10c8368cbdd24ec6ca15dd207be
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="e3bd4-102">Como: Crie um documento com namespaces (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3bd4-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e3bd4-103">Este tópico mostra como criar um documento com namespaces no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="e3bd4-104">Ao usar literais XML no Visual Basic, os usuários podem definir um namespace XML global padrão.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="e3bd4-105">Este namespace é o namespace padrão para literais XML e propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="e3bd4-106">O namespace XML padrão pode ser definida no nível de projeto ou nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="e3bd4-107">Se for definida em nível de arquivo, substitui o namespace padrão no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="e3bd4-108">Você também pode definir namespaces, e especifica os prefixos de namespace para esses namespaces.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="e3bd4-109">Você define dois namespaces padrão e namespaces com um prefixo usando a palavra-chave `Imports` .</span><span class="sxs-lookup"><span data-stu-id="e3bd4-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="e3bd4-110">Para obter mais informações, consulte [Introdução a literais XML no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="e3bd4-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="e3bd4-111">Observe que o namespace XML padrão se aplica somente aos elementos e não a atributos.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="e3bd4-112">Atributos são sempre por padrão em qualquer namespace.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="e3bd4-113">No entanto, você pode usar um prefixo de namespace para colocar um atributo em um namespace.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3bd4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3bd4-114">Example</span></span>  
 <span data-ttu-id="e3bd4-115">Este exemplo cria um documento que contém um namespace.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e3bd4-116">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e3bd4-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e3bd4-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3bd4-117">Example</span></span>  
 <span data-ttu-id="e3bd4-118">Este exemplo cria um documento que contém dois namespaces, uma que é o namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="e3bd4-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e3bd4-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e3bd4-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3bd4-120">Example</span></span>  
 <span data-ttu-id="e3bd4-121">O exemplo a seguir cria um documento que contém vários namespaces, tanto com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="e3bd4-122">Quando serializar uma árvore XML, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] emite-se declarações namespace como necessário para que cada elemento está no namespace designada.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="e3bd4-123">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e3bd4-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3bd4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3bd4-124">See Also</span></span>  
 [<span data-ttu-id="e3bd4-125">Trabalhando com Namespaces XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3bd4-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
