---
title: "Depurando árvores de expressão no Visual Studio (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 14ab67e78a3b4c4819ddca36a406526e78f5485e
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Depurando árvores de expressão no Visual Studio (C#)
Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão. Para obter uma rápida visão geral da estrutura da árvore de expressão, você pode usar a propriedade `DebugView`, que está disponível apenas no modo de depuração. Para obter mais informações sobre depuração, consulte [Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).  
  
 Para melhor representar o conteúdo das árvores de expressão, a propriedade `DebugView` usa os visualizadores do Visual Studio. Para obter mais informações, consulte [Criar visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Para abrir um visualizador para uma árvore de expressão  
  
1.  Clique no ícone de lupa que aparece ao lado da propriedade `DebugView` de uma árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.  
  
     Uma lista de visualizadores é exibida.  
  
2.  Clique no visualizador que você deseja usar.  
  
 Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com um símbolo de "$" no início.  
  
 Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.  
  
 Para tipos numéricos que têm sufixos padrão como literais de C#, o sufixo é adicionado ao valor. A tabela a seguir mostra os sufixos associados com vários tipos numéricos.  
  
|Tipo|Sufixo|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >). Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 Os objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com os tipos delegados.  
  
 Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.  
  
 O token `.Label` indica o início do rótulo. O token `.LabelTarget` indica o local para o qual o destino deve saltar.  
  
 Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Operadores verificados  
 Os operadores verificados são exibidos com o símbolo "#" na frente do operador. Por exemplo, o operador de adição verificado é exibido como `#+`.  
  
### <a name="examples"></a>Exemplos  
  
|Expressão|Propriedade `DebugView`|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Consulte também  
 [Árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [Criar visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)
