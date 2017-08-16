---
title: "Refatoração em funções puras (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e622436905893872521994f6dc1a5bc1c8b3d06a
ms.lasthandoff: 03/13/2017


---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refatoração em funções puras (Visual Basic)
Um aspecto importante de transformações e puras é aprender como o código do refatorar usando funções puras.  
  
 Conforme observado anteriormente nesta seção, uma função pura tem duas características úteis:  
  
-   Não tem efeito colateral. A função não altera quaisquer variáveis ou os dados de qualquer tipo fora da função.  
  
-   É consistente. Dado o mesmo conjunto de dados de entrada, sempre retornará o mesmo valor de saída.  
  
 Uma maneira de fazer a transição para programação funcional é o código existente do refatorar para eliminar efeitos colaterais desnecessários e dependências externas. Dessa maneira, você pode criar versões puras de função do código existente.  
  
 Este tópico descreve o que é uma função pura e o que não é. O [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial mostra como manipular um documento de WordprocessingML e inclui dois exemplos de como refatorar usando uma função pura.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminando efeitos colaterais e dependências externas  
 Os seguintes exemplos contrastam duas funções não puras e uma função pura.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Função não pura que altera um membro de classe  
 No código a seguir, a função de `HypenatedConcat` não é uma função pura, porque altera o membro de dados `aMember` na classe:  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 Esse código gera a seguinte saída:  
  
```  
StringOne-StringTwo  
```  
  
 Observe que é irrelevante se os dados modificados tem `public` ou `private` o acesso, ou um `shared` membro ou um membro de instância. Uma função pura não altera quaisquer dados fora da função.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Função não pura que altera um argumento  
 Além disso, a seguinte versão dessa mesma função não é pura porque modifica o conteúdo do seu parâmetro, `sb`.  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 Esta versão do programa produz a mesma saída como a primeira versão, porque o `HypenatedConcat` função tiver alterado o valor (estado) do seu primeiro parâmetro ao chamar o <xref:System.Text.StringBuilder.Append%2A>função de membro.</xref:System.Text.StringBuilder.Append%2A> Observe que essa mudança ocorre independentemente do fato de que `HypenatedConcat` usa passar o parâmetro de atendimento-por- valor.  
  
> [!IMPORTANT]
>  Para tipos de referência, se você passa um parâmetro por valor, ele resulta em uma cópia de referência a um objeto que está sendo passado. Esta cópia ainda está associada com os mesmos dados de instância que a referência original (até que a variável de referência é atribuído a um novo objeto). a Atendimento-por- referência não necessariamente é necessária para uma função modifique um parâmetro.  
  
### <a name="pure-function"></a>Função pura  
 Seguir essa versão de hows de programa como implementar a função de `HypenatedConcat` como uma função pura.  
  
```vb  
Module Module1  
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String  
        Return (s & "-" & appendStr)  
    End Function  
  
    Sub Main()  
        Dim s1 As String = "StringOne"  
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")  
        Console.WriteLine(s2)  
    End Sub  
End Module  
```  
  
 Além disso, esta versão gerencia a mesma linha de saída: `StringOne-StringTwo`. Observe que para manter o valor concatenado, ele é armazenado em `s2`variável intermediária.  
  
 Uma abordagem que pode ser muito útil é escrever as funções que são localmente impuros (isto é, declare e alteram variáveis locais) mas é global pura. Tais funções têm muitas das características desejáveis de composability, mas impedem alguns de linguagem e mais complicados de programação, como ter que usar a recursão quando um loop simples realizaria a mesma coisa.  
  
## <a name="standard-query-operators"></a>Operadores de consulta padrão  
 Uma característica importante dos operadores de consulta padrão é que são implementados como funções puras.  
  
 Para obter mais informações, consulte [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações e puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Programação funcional versus Programação imperativa (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
