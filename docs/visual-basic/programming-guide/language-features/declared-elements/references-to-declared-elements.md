---
title: "Referências a elementos declarados (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements
- references, declared elements
- qualified names
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48a04f81075accc073b0d1f5b7a61006bef807ae
ms.lasthandoff: 03/13/2017

---
# <a name="references-to-declared-elements-visual-basic"></a>Referências a elementos declarados (Visual Basic)
Quando seu código se refere a um elemento declarado, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador corresponde ao nome na sua referência com a declaração adequada daquele nome. Se mais de um elemento é declarado com o mesmo nome, você pode controlar qual desses elementos deve ser referenciada por *qualificado* seu nome.  
  
 O compilador tenta coincidir uma referência de nome a uma declaração de nome com o *escopo mais restrito*. Isso significa que ele começa com o código fazendo a referência e trabalha externamente através de níveis sucessivos de elementos recipientes.  
  
 O exemplo a seguir mostra referências a duas variáveis com o mesmo nome. O exemplo declara duas variáveis, cada uma nomeada `totalCount`, em diferentes níveis de escopo no módulo `container`. Quando o procedimento `showCount` exibe `totalCount` sem qualificação, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolve a referência para a declaração com o escopo mais restrito, ou seja, a declaração dentro de `showCount`. Quando ele qualifica `totalCount` com o módulo recipiente `container`, o compilador resolve a referência para a declaração com o escopo mais amplo.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Um nome de elemento de qualificação  
 Se você quiser substituir esse processo de pesquisa e especificar um nome declarado em um escopo mais amplo, você deve *qualificar* o nome com o elemento que contém o escopo mais amplo. Em alguns casos, você também pode precisar qualificar o elemento que contém.  
  
 Classificar um nome significa precedê-lo na sua declaração de código-fonte com informações que identificam onde o elemento de destino é definido. Esta informação é chamada uma *sequência de qualificação*. Ele pode incluir um ou mais namespaces e um módulo, classe ou estrutura.  
  
 A cadeia de caracteres de qualificação inequivocamente deve especificar o módulo, classe ou estrutura que contém o elemento de destino. O contêiner por sua vez pode ser localizado em outro contendo elemento, normalmente um namespace. Talvez seja necessário incluir vários elementos continentes na cadeia de caracteres de qualificação.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Para acessar um elemento declarado classificando seu nome  
  
1.  Determine o local no qual o elemento foi definido. Isso pode incluir um namespace, ou mesmo uma hierarquia de namespaces. Dentro do namespace de nível mais baixo, o elemento deve estar contido em um módulo, classe ou estrutura.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  Determine um caminho de qualificação com base na localização do elemento de destino. Inicie com o namespace de nível mais alto, vá para o namespace de nível mais baixo e terminar com o módulo, classe ou estrutura que contém o elemento de destino. Cada elemento no caminho deve conter um elemento que o segue.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Prepare a cadeia de caracteres de qualificação para o elemento de destino. Coloque um ponto final (`.`) após cada elemento no caminho. Seu aplicativo deve ter acesso a todos os elementos na cadeia de caracteres de qualificação.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  Escreva a expressão ou instrução de atribuição referindo-se ao elemento de destino da maneira normal.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Preceda o nome do elemento de destino com a cadeia de caracteres de qualificação. O nome deve seguir imediatamente o período (`.`) que segue o módulo, classe ou estrutura que contém o elemento.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  O compilador usa a cadeia de caracteres de qualificação para localizar uma declaração clara e inequívoca para que ela pode corresponder a referência de elemento de destino.  
  
 Você também pode precisar qualificar uma referência de nome se seu aplicativo tem acesso a mais de um elemento de programação que tem o mesmo nome. Por exemplo, o <xref:System.Windows.Forms>e <xref:System.Web.UI.WebControls>os dois namespaces contêm uma `Label` classe (<xref:System.Windows.Forms.Label?displayProperty=fullName> e <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>).</xref:System.Web.UI.WebControls.Label?displayProperty=fullName> </xref:System.Windows.Forms.Label?displayProperty=fullName> </xref:System.Web.UI.WebControls> </xref:System.Windows.Forms> Se o aplicativo usa ambas, ou se ele define sua própria `Label` classe, você deve distinguir diferentes `Label` objetos. Inclua o alias de namespace ou de importação na declaração da variável. O exemplo a seguir usa o alias de importação.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Membros de outros elementos recipientes  
 Quando você usa um membro não compartilhado de outra classe ou estrutura, primeiro você deve qualificar o nome do membro com uma variável ou expressão que aponta para uma instância da classe ou estrutura. No exemplo a seguir, `demoClass` é uma instância de uma classe chamada `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Você não pode usar o nome da classe para qualificar um membro que não seja [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md). Você deve primeiro criar uma instância em uma variável de objeto (nesse caso `demoClass`) e, em seguida, fazer referência a ela, pelo nome da variável.  
  
 Se uma classe ou estrutura tiver um `Shared` membro, você pode qualificar desse membro com o nome de classe ou estrutura ou com uma variável ou expressão que aponta para uma instância.  
  
 Um módulo não tem nenhuma instância separada, e todos os seus membros são `Shared` por padrão. Portanto, você pode qualificar um membro de módulo com o nome do módulo.  
  
 O exemplo a seguir mostra referências qualificadas a procedimentos de membro de módulo. O exemplo declara dois `Sub` procedimentos, nomeados `perform`, em diferentes módulos em um projeto. Cada um deles pode ser especificado sem qualificação no seu próprio módulo mas deve ser qualificado se referenciado de qualquer outro lugar. Como referência final em `module3` não se qualificam `perform`, o compilador não pode resolver essa referência.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Referências a projetos  
 Usar [pública](../../../../visual-basic/language-reference/modifiers/public.md) elementos definidos em outro projeto, você deve primeiro definir um *referência* à biblioteca de tipo ou assembly do projeto. Para definir uma referência, clique em **adicionar referência** sobre o **projeto** menu ou use o [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador de linha de comando.  
  
 Por exemplo, você pode usar o modelo de objeto XML a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Se você definir uma referência para o <xref:System.Xml>namespace, você pode declarar e usar qualquer uma das suas classes, como <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument> </xref:System.Xml> O exemplo a seguir usa <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importando contendo elementos  
 Você pode usar o [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para *importar* os namespaces que contêm os módulos ou classes que você deseja usar. Isso permite que você se refira aos elementos definidos em um namespace importado sem qualificar totalmente seus nomes. O exemplo a seguir reescreve o exemplo anterior para importar o <xref:System.Xml>namespace.</xref:System.Xml>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Além disso, o `Imports` instrução pode definir um *alias de importação* para cada namespace importado. Isso pode tornar o código-fonte mais curto e fácil de ler. O exemplo a seguir reescreve o exemplo anterior para usar `xD` como um alias para o <xref:System.Xml>namespace.</xref:System.Xml>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 O `Imports` instrução não torna os elementos de outros projetos disponíveis para seu aplicativo. Ou seja, ele não substitui o definindo uma referência. Importar um namespace apenas remove a necessidade de qualificar nomes definidos nesse namespace.  
  
 Você também pode usar o `Imports` instrução de importação de módulos, classes, estruturas e enumerações. Você pode usar os membros de tais elementos importados sem qualificação. No entanto, você sempre deve qualificar os membros não compartilhados de classes e estruturas com uma variável ou expressão que é avaliada como uma instância da classe ou estrutura.  
  
## <a name="naming-guidelines"></a>Diretrizes de nomenclatura  
 Quando você define dois ou mais elementos de programação que têm o mesmo nome, uma *nome ambiguidade* pode resultar quando o compilador tenta resolver uma referência a esse nome. Se mais de uma definição estiver em escopo, ou se nenhuma definição estiver em escopo, a referência é possível resolver. Para obter um exemplo, consulte "Exemplo de referência qualificada" nessa página da Ajuda.  
  
 Você pode evitar ambiguidade de nomes fornecendo nomes exclusivos a todos os seus elementos. Em seguida, você pode fazer referência a qualquer elemento sem precisar qualificar seu nome com um namespace, módulo ou classe. Você também pode reduzir as chances de acidentalmente se referir ao elemento errado.  
  
## <a name="shadowing"></a>Sombreamento  
 Quando dois elementos de programação compartilham o mesmo nome, um deles pode ocultar, ou *sombra*, outro. Um elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento sombreado, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolve para o elemento de sombreamento. Para obter uma explicação mais detalhada com exemplos, consulte [sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Consulte também  
 [Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Novo operador](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Público](../../../../visual-basic/language-reference/modifiers/public.md)
