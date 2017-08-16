---
title: "Vida útil do objeto: Como os objetos são criados e destruídos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Constructor
dev_langs:
- VB
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime, objects
- Sub New constructor, object lifetime
- Finalize method, object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method, object lifetime
- Class_Initialize
- object creation, object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection, Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
caps.latest.revision: 22
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
ms.openlocfilehash: 404c21c39a24d54c008fddf6dc386cc2895fe3a0
ms.lasthandoff: 03/13/2017

---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Tempo de vida do objeto: como os objetos são criados e destruídos (Visual Basic)
Uma instância de uma classe, um objeto, é criada usando a palavra-chave `New`. Tarefas de inicialização geralmente devem ser executadas em novos objetos antes de serem usadas. Tarefas comuns de inicialização incluem abrir arquivos, conectar-se aos bancos de dados e ler os valores das chaves do registro. Visual Basic controla a inicialização de novos objetos usando procedimentos denominados *construtores* (métodos especiais que permitem o controle sobre a inicialização).  
  
 Depois que um objeto sai do escopo, ele é liberado pelo common language runtime (CLR). Visual Basic controla o lançamento dos recursos do sistema usando procedimentos denominados *destruidores*. Juntos, os construtores e os destruidores oferecem suporte à criação de bibliotecas de classe robusta e previsível.  
  
## <a name="using-constructors-and-destructors"></a>Usando construtores e destruidores  
 Os construtores e os destruidores controlam a criação e a destruição de objetos. Os procedimentos `Sub New` e `Sub Finalize` no Visual Basic inicializam e destroem objetos; eles substituem os métodos `Class_Initialize` e `Class_Terminate` usados no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 e em versões anteriores.  
  
### <a name="sub-new"></a>Sub New  
 O construtor `Sub New` pode ser executado apenas uma vez quando uma classe é criada. Não pode ser chamado explicitamente em qualquer lugar que não seja na primeira linha do código de outro construtor da mesma classe ou de uma classe derivada. Além disso, o código no método `Sub New` sempre é executado antes de qualquer outro código em uma classe. [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]e versões posteriores implicitamente criam um `Sub New` construtor em tempo de execução se você não definir explicitamente uma `Sub New` procedimento para uma classe.  
  
 Para criar um construtor para uma classe, crie um procedimento denominado `Sub New` em qualquer lugar na definição de classe. Para criar um construtor com parâmetros, especifique os nomes e tipos de dados dos argumentos para `Sub New` exatamente como você faria para qualquer outro procedimento, como no seguinte código:  
  
 [!code-vb[VbVbalrOOP&42;](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 Os construtores são frequentemente sobrecarregados, como no seguinte código:  
  
 [!code-vb[VbVbalrOOP&#116;](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 Quando você define uma classe derivada de outra classe, a primeira linha do construtor deve ser uma chamada para o construtor da classe base, a menos que a classe base tenha um construtor acessível que não utiliza parâmetros. Uma chamada para a classe base que contém o construtor acima, por exemplo, seria `MyBase.New(s)`. Caso contrário, o `MyBase.New` é opcional e o tempo de execução [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] o chama implicitamente.  
  
 Depois de escrever o código para chamar o construtor do objeto pai, você pode adicionar qualquer código de inicialização adicional para o procedimento `Sub New`. `Sub New` pode aceitar argumentos quando chamado como um construtor com parâmetros. Esses parâmetros são passados do procedimento que está chamando o construtor, por exemplo, `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Antes da liberação de objetos, o CLR chama automaticamente o método `Finalize` para objetos que definem um procedimento `Sub Finalize`. O método `Finalize` pode conter códigos que precisam ser executados antes que um objeto seja destruído, como o código para fechar arquivos e salvar as informações de estado. Há uma pequena perda de desempenho para executar `Sub Finalize`, portanto, você deve definir um método `Sub Finalize` somente quando precisar liberar objetos explicitamente.  
  
> [!NOTE]
>  O coletor de lixo do CLR não considera (e não pode) descartar *não gerenciado objetos*, objetos que o sistema operacional executa diretamente, fora do ambiente do CLR. Isso ocorre porque diferentes objetos não gerenciados devem ser descartados de maneiras diferentes. Essas informações não estão diretamente associadas ao objeto não gerenciado; devem ser encontradas na documentação do objeto. Uma classe que usa objetos não gerenciados deve descartá-los em seu método `Finalize`.  
  
 O destruidor `Finalize` é um método protegido que pode ser chamado somente da classe à qual pertence ou de classes derivadas. O sistema automaticamente chama `Finalize` quando um objeto é destruído, assim, você não deve chamar explicitamente o `Finalize` de fora de uma implementação `Finalize` de classe derivada.  
  
 Diferentemente de `Class_Terminate`, que é executado assim que um objeto é definido como nada, normalmente existe um atraso entre o momento em que um objeto perde o escopo e o momento em que o Visual Basic chama o destruidor `Finalize`. [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]e versões posteriores permitem um segundo tipo de destruidor, <xref:System.IDisposable.Dispose%2A>, que pode ser chamado explicitamente a qualquer momento para liberar recursos imediatamente.</xref:System.IDisposable.Dispose%2A>  
  
> [!NOTE]
>  Um destruidor `Finalize` não deve lançar exceções, já que elas não podem ser tratadas pelo aplicativo e podem fazer com que o aplicativo seja finalizado.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Como os métodos novos e de finalização funcionam em uma hierarquia de classe  
 Sempre que uma instância de uma classe é criada, o common language runtime (CLR) tenta executar um procedimento denominado `New`, se ele existir nesse objeto. `New` é um tipo de procedimento denominado `constructor` que é usado para inicializar novos objetos antes que qualquer outro código em um objeto seja executado. Um construtor `New` pode ser usado para abrir arquivos, conectar-se aos bancos de dados, inicializar variáveis e cuidar de quaisquer outras tarefas que precisam ser feitas antes que um objeto pode ser usado.  
  
 Quando uma instância de uma classe derivada é criada, o construtor `Sub New` da classe base é executado primeiro, seguido pelos construtores em classes derivadas. Isso acontece porque a primeira linha do código em um construtor `Sub New` usa a sintaxe `MyBase.New()` para chamar o construtor da classe imediatamente acima de si próprio na hierarquia de classe. O construtor `Sub New` é chamado para cada classe na hierarquia de classe, até que o construtor de classe base seja atingido. Nesse ponto, o código no construtor para a classe base é executado, seguido pelo código em cada construtor em todas as classes derivadas e o código na maioria das classes derivadas é executado por último.  
  
 ![Construtores e herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")  
  
 Quando um objeto não for necessário, o CLR chama o <xref:System.Object.Finalize%2A>método para o objeto antes de liberar sua memória.</xref:System.Object.Finalize%2A> O <xref:System.Object.Finalize%2A>método é chamado um `destructor` porque ele realiza tarefas de limpeza, como salvar informações do estado, fechar arquivos e conexões com bancos de dados e outras tarefas que devem ser executadas antes de liberar o objeto.</xref:System.Object.Finalize%2A>  
  
 ![Construtores e herança&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")  
  
## <a name="idisposable-interface"></a>Interface IDisposable  
 Instâncias de classe geralmente controlam os recursos não gerenciados pelo CLR, assim como identificadores do Windows e conexões de banco de dados. Esses recursos devem ser descartados no método `Finalize` da classe, para que eles sejam liberados quando o objeto for destruído pelo coletor de lixo. No entanto, o coletor de lixo destrói objetos somente quando o CLR exige mais memória livre. Isso significa que os recursos podem não ser liberados até muito tempo depois que o objeto sair do escopo.  
  
 Para complementar a coleta de lixo, suas classes podem fornecer um mecanismo para gerenciar ativamente os recursos do sistema se eles implementam o <xref:System.IDisposable>interface.</xref:System.IDisposable> <xref:System.IDisposable>tem um método, <xref:System.IDisposable.Dispose%2A>, os clientes devem chamar quando terminarem de usar um objeto.</xref:System.IDisposable.Dispose%2A></xref:System.IDisposable> Você pode usar o <xref:System.IDisposable.Dispose%2A>método para liberar recursos imediatamente e executar tarefas como fechar arquivos e conexões de banco de dados.</xref:System.IDisposable.Dispose%2A> Ao contrário do `Finalize` destruidor, o <xref:System.IDisposable.Dispose%2A>método não é chamado automaticamente.</xref:System.IDisposable.Dispose%2A> Os clientes de uma classe devem chamar explicitamente <xref:System.IDisposable.Dispose%2A>quando desejar liberar recursos imediatamente.</xref:System.IDisposable.Dispose%2A>  
  
### <a name="implementing-idisposable"></a>Implementando IDisposable  
 Uma classe que implementa o <xref:System.IDisposable>interface deve incluir essas seções de código:</xref:System.IDisposable>  
  
-   Um campo para controlar se o objeto foi descartado:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Uma sobrecarga de <xref:System.IDisposable.Dispose%2A>que libera recursos da classe.</xref:System.IDisposable.Dispose%2A> Esse método deve ser chamado <xref:System.IDisposable.Dispose%2A>e `Finalize` métodos da classe base:</xref:System.IDisposable.Dispose%2A>  
  
    ```  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposed Then  
            If disposing Then  
                ' Insert code to free managed resources.  
            End If  
            ' Insert code to free unmanaged resources.  
        End If  
        Me.disposed = True  
    End Sub  
    ```  
  
-   Uma implementação de <xref:System.IDisposable.Dispose%2A>que contém apenas o código a seguir:</xref:System.IDisposable.Dispose%2A>  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   Uma substituição do método `Finalize` que contém apenas o código a seguir:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>Derivação de uma classe que implementa IDisposable  
 Uma classe que deriva de uma classe base que implementa o <xref:System.IDisposable>interface não precisa substituir qualquer um dos métodos base, a menos que ele utilize recursos adicionais que precisam ser descartados.</xref:System.IDisposable> Nessa situação, a classe derivada deve substituir o método `Dispose(disposing)` de classe base para descartar os recursos da classe derivada. Essa substituição deve chamar o método `Dispose(disposing)` da classe base.  
  
```  
Protected Overrides Sub Dispose(ByVal disposing As Boolean)  
    If Not Me.disposed Then  
        If disposing Then  
            ' Insert code to free managed resources.  
        End If  
        ' Insert code to free unmanaged resources.  
    End If  
    MyBase.Dispose(disposing)  
End Sub  
```  
  
 Uma classe derivada não deve substituir a classe base <xref:System.IDisposable.Dispose%2A>e `Finalize` métodos.</xref:System.IDisposable.Dispose%2A> Quando esses métodos são chamados de uma instância da classe derivada, a implementação da classe base desses métodos chamam a substituição da classe derivada do método `Dispose(disposing)`.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>A coleta de lixo e o destruidor de finalização  
 O [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] usa o *coleta de lixo de rastreamento de referência* sistema periodicamente liberar recursos não utilizados. Visual Basic 6.0 e versões anteriores usaram um sistema diferente denominado *contagem de referência* para gerenciar recursos. Embora os dois sistemas executem a mesma função automaticamente, existem algumas diferenças importantes.  
  
 O CLR destrói periodicamente objetos quando o sistema determina que esses objetos não são mais necessários. Os objetos são liberados mais rapidamente quando os recursos de sistema estão em fornecimento pequeno e, em caso contrário, menos frequente. O atraso entre quando um objeto perde o escopo e quando o CLR libera, significa que, diferente dos objetos no Visual Basic 6.0 e versões anteriores, você não pode determinar exatamente quando o objeto será destruído. Nessa situação, os objetos são considerados como tendo *tempo de vida não determinístico*. Na maioria dos casos, o tempo de vida não determinístico não altera o modo como você grava aplicativos, desde que você se lembre de que o destruidor `Finalize` pode não ser executado imediatamente quando um objeto perde o escopo.  
  
 Outra diferença entre os sistemas de coleta de lixo envolve o uso de `Nothing`. Para aproveitar a contagem de referência no Visual Basic 6.0 e em versões anteriores, os programadores às vezes atribuem `Nothing` para as variáveis de objeto para liberar as referências que essas variáveis mantinham. Se a variável mantiver a última referência ao objeto, os recursos do objeto são lançados imediatamente. Em versões posteriores do Visual Basic, embora haja casos em que esse procedimento ainda é importante, executá-lo nunca faz com que o objeto referenciado libere seus recursos imediatamente. Para liberar recursos imediatamente, use o objeto <xref:System.IDisposable.Dispose%2A>método, se disponível.</xref:System.IDisposable.Dispose%2A> A única vez em que você deve definir uma variável para `Nothing` é quando seu tempo de vida é longo em relação ao tempo que o coletor de lixo leva para detectar objetos órfãos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IDisposable.Dispose%2A></xref:System.IDisposable.Dispose%2A>   
 [Inicialização e término de componentes](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)   
 [Novo operador](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Limpeza de recursos não gerenciados](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)
