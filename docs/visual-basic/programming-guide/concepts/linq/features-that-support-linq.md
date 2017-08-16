---
title: Recursos do Visual Basic que suportam LINQ | Documentos do Microsoft
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
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3bca15a07a88195589b9c9de5f9842eea42912f1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-features-that-support-linq"></a>Funcionalidades do Visual Basic que suportam LINQ
O nome [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] refere-se à tecnologia no Visual Basic que oferece suporte à sintaxe de consulta e outra linguagem constrói diretamente na linguagem. Com [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], você não precisa aprender uma nova linguagem para consulta em uma fonte de dados externa. É possível consultar dados em bancos de dados relacionais, armazenamentos XML ou objetos usando o Visual Basic. Essa integração de recursos de consulta para o idioma permite a verificação de tempo de compilação para erros de sintaxe e segurança de tipo. Essa integração também garante que você já sabe a maioria dos quais você precisa saber para escrever consultas sofisticadas, variadas no Visual Basic.  
  
 As seções a seguir descrevem as construções de linguagem que oferecem suporte a LINQ em detalhes suficientes para que você possa começar a ler a documentação de Introdução, exemplos de código e aplicativos de exemplo. Você também pode clicar nos links para obter explicações mais detalhadas sobre como os recursos de idioma se reúnem para habilitar a consulta integrada à linguagem. Um bom lugar para começar é [passo a passo: escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Expressões de consulta  
 Expressões de consulta no Visual Basic podem ser expressa em uma sintaxe declarativa semelhante do SQL ou XQuery. Em tempo de compilação, a sintaxe de consulta é convertida em chamadas de método para a implementação de um provedor LINQ dos métodos de extensão de operador de consulta padrão. Controle de aplicativos que os operadores de consulta padrão estão no escopo, especificando o namespace apropriado com um `Imports` instrução. Sintaxe para uma expressão de consulta do Visual Basic tem esta aparência:  
  
 [!code-vb[VbLINQVbFeatures n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Variáveis digitadas implicitamente  
 Em vez de especificar explicitamente um tipo quando declarar e inicializar uma variável, você pode habilitar o compilador inferir e atribuir o tipo. Isso é conhecido como *inferência de tipo local*.  
  
 Variáveis cujos tipos são inferidos são fortemente tipadas, como as variáveis cujo tipo você especificar explicitamente. Inferência de tipo local só funciona quando você está definindo uma variável local dentro de um corpo de método. Para obter mais informações, consulte [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 O exemplo a seguir ilustra a inferência de tipo local. Para usar este exemplo, você deve definir `Option Infer` para `On`.  
  
 [!code-vb[VbLINQVbFeatures n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Inferência de tipo local também torna possível criar tipos anônimos, que são descritos posteriormente nesta seção e são necessários para consultas LINQ.  
  
 No exemplo a seguir LINQ, a inferência de tipo ocorre se `Option Infer` seja `On` ou `Off`. Ocorrerá um erro de tempo de compilação se `Option Infer` é `Off` e `Option Strict` é `On`.  
  
 [!code-vb[VbLINQVbFeatures n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Inicializadores de objeto  
 Inicializadores de objeto são usados em expressões de consulta quando você precisa criar um tipo anônimo para manter os resultados de uma consulta. Eles também podem ser usados para inicializar objetos dos tipos nomeados fora de consultas. Usando um inicializador de objeto, você pode inicializar um objeto em uma única linha sem chamar explicitamente um construtor. Supondo que você tenha uma classe chamada `Customer` que tem pública `Name` e `Phone` propriedades, junto com outras propriedades, um inicializador de objeto pode ser usado desta maneira:  
  
 [!code-vb[VbLINQVbFeatures n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Tipos anônimos  
 Tipos anônimos fornecem uma maneira conveniente de agrupar temporariamente um conjunto de propriedades em um elemento que você deseja incluir em um resultado de consulta. Isso permite que você escolha qualquer combinação de campos disponíveis na consulta, em qualquer ordem, sem definir um tipo de dados chamado para o elemento.  
  
 Um *tipo anônimo* é construído dinamicamente pelo compilador. O nome do tipo é atribuído pelo compilador e pode alterar com cada nova compilação. Portanto, o nome não pode ser usado diretamente. Tipos anônimos são inicializados da seguinte maneira:  
  
 [!code-vb[VbLINQVbFeatures n º&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Métodos de extensão  
 Métodos de extensão permitem que você adicione métodos para um tipo de dados ou a interface de fora da definição. Esse recurso permite que você, na verdade, adicionar novos métodos para um tipo existente sem modificar o tipo de fato. Os operadores de consulta padrão são um conjunto de métodos de extensão que fornecem [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] funcionalidade de consulta para qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Outras extensões para <xref:System.Collections.Generic.IEnumerable%601>incluem <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>e <xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601>  
  
 O método de extensão a seguir adiciona um método de impressão para a <xref:System.String>classe.</xref:System.String>  
  
 [!code-vb[VbLINQVbFeatures n º&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 O método é chamado como um método de instância comum de <xref:System.String>:</xref:System.String>  
  
 [!code-vb[VbLINQVbFeatures&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Para obter mais informações, consulte [métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressões lambda  
 Uma expressão lambda é uma função sem um nome que calcula e retorna um único valor. Ao contrário de funções nomeadas, uma expressão lambda pode ser definida e executada ao mesmo tempo. O exemplo a seguir exibe 4.  
  
 [!code-vb[VbLINQVbFeatures n º&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Você pode atribuir a definição da expressão lambda para um nome de variável e, em seguida, usar o nome para chamar a função. O exemplo a seguir também exibe 4.  
  
 [!code-vb[VbLINQVbFeatures&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 Em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], expressões lambda são a base de muitos dos operadores de consulta padrão. O compilador cria expressões lambda para capturar os cálculos definidos nos métodos fundamentais de consulta como `Where`, `Select`, `Order By`, `Take While`e outros.  
  
 Por exemplo, o código a seguir define uma consulta que retorna todos os alunos sênior de uma lista de alunos.  
  
 [!code-vb[VbLINQVbFeatures n º&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 A definição de consulta é compilada em código que é semelhante ao exemplo a seguir, que usa duas expressões lambda para especificar os argumentos para `Where` e `Select`.  
  
 [!code-vb[VbLINQVbFeatures n º&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 A versão pode ser executada usando um `For Each` loop:  
  
 [!code-vb[VbLINQVbFeatures n º&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Para obter mais informações, consulte [expressões Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Consulta integrada à linguagem (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
