---
title: 'Como: criar um documento com namespaces (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: a440c9d810798eb5ebd025a336cbb17fface23b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414628"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="b4c1d-102">Como: Crie um documento com namespaces (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4c1d-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b4c1d-103">Este tópico mostra como criar um documento com namespaces no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="b4c1d-104">Ao usar literais XML no Visual Basic, os usuários podem definir um namespace XML global padrão.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="b4c1d-105">Este namespace é o namespace padrão para literais XML e propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="b4c1d-106">O namespace XML padrão pode ser definida no nível de projeto ou nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="b4c1d-107">Se for definida em nível de arquivo, substitui o namespace padrão no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="b4c1d-108">Você também pode definir namespaces, e especifica os prefixos de namespace para esses namespaces.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="b4c1d-109">Você define dois namespaces padrão e namespaces com um prefixo usando a palavra-chave `Imports` .</span><span class="sxs-lookup"><span data-stu-id="b4c1d-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="b4c1d-110">Para obter mais informações, consulte [introdução aos literais XML no Visual Basic](introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="b4c1d-110">For more information, see [Introduction to XML Literals in Visual Basic](introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="b4c1d-111">Observe que o namespace XML padrão se aplica somente aos elementos e não a atributos.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="b4c1d-112">Atributos são sempre por padrão em qualquer namespace.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="b4c1d-113">No entanto, você pode usar um prefixo de namespace para colocar um atributo em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4c1d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4c1d-114">Example</span></span>  
 <span data-ttu-id="b4c1d-115">Este exemplo cria um documento que contém um namespace.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="b4c1d-116">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4c1d-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b4c1d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4c1d-117">Example</span></span>  
 <span data-ttu-id="b4c1d-118">Este exemplo cria um documento que contém dois namespaces, uma que é o namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="b4c1d-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4c1d-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b4c1d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4c1d-120">Example</span></span>  
 <span data-ttu-id="b4c1d-121">O exemplo a seguir cria um documento que contém vários namespaces, tanto com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="b4c1d-122">Quando serializar uma árvore XML, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emite-se declarações namespace como necessário para que cada elemento está no namespace designada.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="b4c1d-123">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4c1d-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4c1d-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4c1d-124">See also</span></span>

- [<span data-ttu-id="b4c1d-125">Visão geral de namespaces (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4c1d-125">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
