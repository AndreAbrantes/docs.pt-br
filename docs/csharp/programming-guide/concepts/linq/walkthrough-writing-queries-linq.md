---
title: "Instruções passo a passo: escrevendo consultas em C# (LINQ) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 5692bd4b2fae4c5e17d48c12e98eb2e18523ba61
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Instruções passo a passo: escrevendo consultas em C# (LINQ)
Essas instruções passo a passo demonstram os recursos de linguagem C# que são usados para gravar expressões de consulta LINQ.  
  
## <a name="create-a-c-project"></a>Criar um Projeto C#  
  
> [!NOTE]
>  As instruções a seguir são para o Visual Studio. Se você estiver usando um ambiente de desenvolvimento diferente, crie um projeto de console com uma referência a System.Core.dll e uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=fullName>.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Para criar um projeto no Visual Studio  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  Expanda **Instalado**, expanda **Modelos**, expanda **Visual C#** e, em seguida, escolha **Aplicativo de Console**.  
  
4.  Na caixa de texto **Nome**, insira um nome diferente ou aceite o nome padrão e escolha o botão **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
5.  Observe que o projeto tem uma referência a System.Core.dll e a uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=fullName>.  
  
## <a name="create-an-in-memory-data-source"></a>Criar uma Fonte de Dados na Memória  
 A fonte de dados para as consultas é uma lista simples de objetos `Student`. Cada registro `Student` tem um nome, sobrenome e uma matriz de inteiros que representa seus resultados de testes na classe. Copie este código no seu projeto. Observe as seguintes características:  
  
-   A classe `Student` consiste em propriedades autoimplementadas.  
  
-   Cada aluno na lista é inicializado com um inicializador de objeto.  
  
-   A lista em si é inicializada com um inicializador de coleção.  
  
 Essa estrutura de dados inteira será inicializada e instanciada sem chamadas explícitas para nenhum construtor ou acesso de membro explícito. Para obter mais informações sobre esses novos recursos, consulte [Propriedades autoimplementadas](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Para adicionar a fonte de dados  
  
-   Adicione a classe `Student` e a lista inicializada de alunos à classe `Program` em seu projeto.  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Para adicionar um novo Aluno à lista de Alunos  
  
1.  Adicione um novo `Student` à lista `Students` e use um nome e pontuações de teste de sua escolha. Tente digitar as informações do novo aluno para aprender melhor a sintaxe do inicializador de objeto.  
  
## <a name="create-the-query"></a>Criar a Consulta  
  
#### <a name="to-create-a-simple-query"></a>Para criar uma consulta simples  
  
-   No método `Main` do aplicativo, crie uma consulta simples que, quando for executada, produzirá uma lista de todos os alunos cuja pontuação no primeiro teste foi superior a 90. Observe que como o objeto `Student` todo está selecionado, o tipo da consulta é `IEnumerable<Student>`. Embora o código também possa usar a tipagem implícita usando a palavra-chave [var](../../../../csharp/language-reference/keywords/var.md), a tipagem explícita é usada para ilustrar claramente os resultados. (Para obter mais informações sobre `var`, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Observe também que a variável de intervalo da consulta, `student`, também funciona como uma referência para cada `Student` na fonte, fornecendo acesso ao membro para cada objeto.  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Executar a Consulta  
  
#### <a name="to-execute-the-query"></a>Para executar a consulta  
  
1.  Agora escreva o loop `foreach` que fará com que a consulta seja executada. Observe o seguinte sobre o código:  
  
    -   Cada elemento na sequência retornada é acessado pela variável de iteração no loop `foreach`.  
  
    -   O tipo dessa variável é `Student` e o tipo da variável de consulta é compatível, `IEnumerable<Student>`.  
  
2.  Após você ter adicionado esse código, compile e execute o aplicativo para ver os resultados na janela **Console**.  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Para adicionar outra condição de filtro  
  
1.  Você pode combinar várias condições boolianas na cláusula `where` para refinar ainda mais uma consulta. O código a seguir adiciona uma condição de forma que a consulta retorna os alunos cuja primeira pontuação foi superior a 90 e cuja última pontuação foi inferior a 80. A cláusula `where` deve parecer com o código a seguir.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Para obter mais informações, consulte [Cláusula where](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Modificar a Consulta  
  
#### <a name="to-order-the-results"></a>Para ordenar os resultados  
  
1.  Será mais fácil verificar os resultados se eles estiverem em algum tipo de ordem. Você pode ordenar a sequência retornada por qualquer campo acessível nos elementos de origem. Por exemplo, a cláusula `orderby` a seguir ordena os resultados em ordem alfabética de A a Z de acordo com o sobrenome de cada aluno. Adicione a cláusula `orderby` a seguir à consulta, logo após a instrução `where` e antes da instrução `select`:  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Agora, altere a cláusula `orderby` para que ela ordene os resultados em ordem inversa de acordo com a pontuação no primeiro teste, da pontuação mais alta para a mais baixa.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Altere a cadeia de caracteres de formato `WriteLine` para que você possa ver as pontuações:  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Para agrupar os resultados  
  
1.  O agrupamento é uma poderosa funcionalidade em expressões de consulta. Uma consulta com uma cláusula group produz uma sequência de grupos e cada grupo em si contém um `Key` e uma sequência que consiste em todos os membros desse grupo. A nova consulta a seguir agrupa os alunos usando a primeira letra do sobrenome como a chave.  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Observe que o tipo da consulta agora mudou. Ele produz uma sequência de grupos que têm um tipo `char` como uma chave e uma sequência de objetos `Student`. Como o tipo de consulta foi alterado, o código a seguir altera o loop de execução `foreach` também:  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Execute o aplicativo e exiba os resultados na janela **Console**.  
  
     Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Para deixar as variáveis tipadas implicitamente  
  
1.  A codificação explícita `IEnumerables` de `IGroupings` pode se tornar entediante rapidamente. Você pode escrever a mesma consulta e o loop `foreach` muito mais convenientemente usado `var`. A palavra-chave `var` não altera os tipos de objetos, ela simplesmente instrui o compilador a inferir os tipos. Altere o tipo de `studentQuery` e a variável de iteração `group` para `var` e execute a consulta novamente. Observe que no loop `foreach` interno, a variável de iteração ainda tem o tipo `Student` e a consulta funciona exatamente como antes. Alterar a variável de iteração `s` para `var` e execute a consulta novamente. Você verá que obtém exatamente os mesmos resultados.  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Para obter mais informações sobre [var](../../../../csharp/language-reference/keywords/var.md), consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Para ordenar os grupos pelo valor da chave  
  
1.  Ao executar a consulta anterior, observe que os grupos não estão em ordem alfabética. Para alterar isso, você deve fornecer uma cláusula `orderby` após a cláusula `group`. Mas, para usar uma cláusula `orderby`, primeiro é necessário um identificador que serve como uma referência para os grupos criados pela cláusula `group`. Forneça o identificador usando a palavra-chave `into`, da seguinte maneira:  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Quando você executa essa consulta, você verá que os grupos agora estão classificados em ordem alfabética.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Para introduzir um identificador usando let  
  
1.  Você pode usar a palavra-chave `let` para introduzir um identificador para qualquer resultado da expressão na expressão de consulta. Esse identificador pode ser uma conveniência, como no exemplo a seguir ou ele pode melhorar o desempenho armazenando os resultados de uma expressão para que ele não precise ser calculado várias vezes.  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Para obter mais informações, consulte [Cláusula let](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Para usar a sintaxe do método em uma expressão de consulta  
  
1.  Conforme descrito em [Sintaxe de consulta e sintaxe de método em LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), algumas operações de consulta podem ser expressadas somente usando a sintaxe de método. O código a seguir calcula a pontuação total para cada `Student` na sequência de origem e então chama o método `Average()` nos resultados da consulta para calcular a pontuação média da classe. Observe a colocação de parênteses em torno da expressão de consulta.  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Para transformar ou projetar na cláusula select  
  
1.  É muito comum para uma consulta produzir uma sequência cujos elementos são diferentes dos elementos nas sequências de origem. Exclua ou comente o loop de consulta e execução anterior e substitua-o pelo código a seguir. Observe que a consulta retorna uma sequência de cadeias de caracteres (não `Students`) e esse fato é refletido no loop `foreach`.  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  O código anterior neste passo a passo indicou que a pontuação média de classe é de aproximadamente 334. Para produzir uma sequência de `Students` cuja pontuação total é maior que a média de classe, juntamente com seus `Student ID`, você pode usar um tipo anônimo na instrução `select`:  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Próximas etapas  
 Depois que estiver familiarizado com os aspectos básicos de como trabalhar com consultas em C#, você estará pronto para ler a documentação e exemplos para o tipo específico de provedor LINQ que lhe interessam:  
  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Consulte também  
 [LINQ (Consulta Integrada à Linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [Introdução ao LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
