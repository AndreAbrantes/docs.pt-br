---
title: Para cada um... Next Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
dev_langs:
- VB
helpviewer_keywords:
- infinite loops
- Next statement, For Each...Next
- endless loops
- loop structures, For Each...Next
- loops, endless
- Each keyword
- instructions, repeating
- For Each statement
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement, For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e0173877fa4a57da76fd774d70ce63d2beda23ad
ms.lasthandoff: 03/13/2017

---
# <a name="for-eachnext-statement-visual-basic"></a>Instrução For Each...Next (Visual Basic)
Repete um grupo de instruções para cada elemento em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário o `For Each` instrução. Opcional no `Next` instrução. Variável. Usado para percorrer os elementos da coleção.|  
|`datatype`|Necessário se `element` já não está declarado. Tipo de dados de `element`.|  
|`group`|Necessário. Uma variável com um tipo que é um tipo de coleção ou objeto. Refere-se a coleção na qual o `statements` devem ser repetidos.|  
|`statements`|Opcional. Uma ou mais instruções entre `For Each` e `Next` que são executados em cada item na `group`.|  
|`Continue For`|Opcional. Transfere o controle para o início do `For Each` loop.|  
|`Exit For`|Opcional. Transfere o controle do `For Each` loop.|  
|`Next`|Necessário. Finaliza a definição de `For Each` loop.|  
  
## <a name="simple-example"></a>Exemplo simples  
 Use a `For Each`... `Next` loop para repetir um conjunto de instruções para cada elemento de uma coleção ou matriz.  
  
> [!TIP]
>  A [For... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) funciona bem quando você pode associar a uma variável de controle de cada iteração de um loop e determinar os valores inicial e final da variável. No entanto, quando você está lidando com uma coleção, o conceito de valores inicias e finais não é significativo e você não sabe quantos elementos a coleção tem necessariamente. Nesse tipo de caso, uma `For Each`... `Next` loop costuma ser uma opção melhor.  
  
 No exemplo a seguir, o `For Each`...`Next` instrução itera em todos os elementos de uma coleção de lista.  
  
 [!code-vb[VbVbalrStatements&#121;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Para obter mais exemplos, consulte [coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) e [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Loops aninhados  
 Você pode aninhar `For Each` loops colocando um loop dentro de outro.  
  
 O exemplo a seguir demonstra aninhada `For Each`...`Next` estruturas.  
  
 [!code-vb[VbVbalrStatements&#122;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Quando você aninhar loops, cada loop deve ter um único `element` variável.  
  
 Você também pode aninhar diferentes tipos de estruturas de controle em si. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Sair para e continuar  
 O [sair para](../../../visual-basic/language-reference/statements/exit-statement.md) instrução faz a execução saia do `For`...`Next` loop for e transfere o controle para a instrução que segue o `Next` instrução.  
  
 O `Continue For` instrução transfere o controle imediatamente para a próxima iteração do loop. Para obter mais informações, consulte [continuar instrução](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir mostra como usar o `Continue For` e `Exit For` instruções.  
  
 [!code-vb[VbVbalrStatements&123;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Você pode colocar qualquer número de `Exit For` instruções em um `For Each` loop. Quando usado dentro aninhados `For Each` loops, `Exit For` faz a execução saia do interno loop e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit For`é frequentemente usado após uma avaliação de alguma condição, por exemplo, em um `If`... `Then`... `Else` estrutura. Você talvez queira usar `Exit For` para as seguintes condições:  
  
-   Continuando a iteração é desnecessária ou impossível. Isso pode ser causado por um valor incorreto ou uma solicitação de encerramento.  
  
-   Uma exceção é detectada em um `Try`... `Catch`... `Finally`. Você pode usar `Exit For` no final o `Finally` bloco.  
  
-   Há um loop infinito, o que é um loop que pode executar um número grande ou mesmo infinito de vezes. Se você detectar tal condição, você pode usar `Exit For` para escapar do loop. Para obter mais informações, consulte [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iteradores  
 Você usa um *iterador* para executar uma iteração personalizada em uma coleção. Um iterador pode ser uma função ou um `Get` acessador. Ele usa um `Yield` instrução para retornar cada elemento da coleção um por vez.  
  
 Chamar um iterador usando um `For Each...Next` instrução. Cada iteração de `For Each` loop chama o iterador. Quando um `Yield` instrução for atingida no iterador, a expressão no `Yield` instrução será retornada e o local atual no código é retido. Execução é reiniciada a partir desse local na próxima vez que o iterador é chamado.  
  
 O exemplo a seguir usa uma função de iterador. A função de iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. No `ListEvenNumbers` cada iteração de um método, o `For Each` corpo da instrução cria uma chamada para a função do iterador, que passa para o próximo `Yield` instrução.  
  
 [!code-vb[VbVbalrStatements&#127;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Para obter mais informações, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7), [instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md), e [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 Quando um `For Each`...`Next` instrução é executada, Visual Basic avalia a coleção somente uma vez, antes que o loop for iniciado. Se o bloco de instrução altera `element` ou `group`, essas alterações não afetam a iteração do loop.  
  
 Quando todos os elementos na coleção sucessivamente receberam a `element`, o `For Each` loop para e o controle passa para a instrução depois de `Next` instrução.  
  
 Se `element` não tenha sido declarada fora desse loop, você deve declará-la no `For Each` instrução. Você pode declarar o tipo de `element` explicitamente usando um `As` instrução, ou você pode contar com a inferência de tipo para atribuir o tipo. Em ambos os casos, o escopo de `element` é o corpo do loop. No entanto, você não pode declarar `element` fora e dentro do loop.  
  
 Você pode opcionalmente especificar `element` no `Next` instrução. Isso melhora a legibilidade do programa, especialmente se você tiver aninhado `For Each` loops. Você deve especificar a mesma variável que aparece no correspondente `For Each` instrução.  
  
 Talvez você queira evitar a alteração do valor de `element` dentro de um loop. Isso pode tornar mais difícil de ler e depurar seu código. Alterar o valor de `group` não afeta a coleção ou seus elementos, o que foram determinados quando o loop foi acessado pela primeira vez.  
  
 Quando você estiver loops aninhados, se um `Next` declaração de um nível de aninhamento externa é encontrada antes do `Next` de um nível interno, o compilador sinaliza um erro. No entanto, o compilador pode detectar isso sobreposição de erro somente se você especificar `element` em cada `Next` instrução.  
  
 Se seu código depende de como percorrer uma coleção em uma ordem específica, um `For Each`... `Next` loop não é a melhor opção, a menos que saiba as características do objeto enumerator expõe a coleção. A ordem de passagem não é determinada pelo Visual Basic, mas pelo <xref:System.Collections.IEnumerator.MoveNext%2A>método do objeto enumerador.</xref:System.Collections.IEnumerator.MoveNext%2A> Portanto, você não poderá prever qual elemento da coleção é o primeiro a ser retornado em `element`, ou o que é o próximo a serem retornados após um determinado elemento. Você pode obter resultados mais confiáveis usando uma estrutura de loop diferentes, como `For`... `Next` or `Do`... `Loop`.  
  
 O tipo de dados `element` deve ser tal que o tipo de dados dos elementos de `group` pode ser convertido para ele.  
  
 O tipo de dados `group` deve ser um tipo de referência que se refere a uma coleção ou uma matriz que é enumerável. Geralmente isso significa que `group` refere-se a um objeto que implementa o <xref:System.Collections.IEnumerable>interface da `System.Collections` namespace ou o <xref:System.Collections.Generic.IEnumerable%601>interface do `System.Collections.Generic` namespace.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> `System.Collections.IEnumerable`Define o <xref:System.Collections.IEnumerable.GetEnumerator%2A>método, que retorna um objeto enumerador para a coleção.</xref:System.Collections.IEnumerable.GetEnumerator%2A> Implementa o objeto enumerador de `System.Collections.IEnumerator` interface da `System.Collections` namespace e expõe o <xref:System.Collections.IEnumerator.Current%2A>propriedade e o <xref:System.Collections.IEnumerator.Reset%2A>e <xref:System.Collections.IEnumerator.MoveNext%2A>métodos.</xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.Current%2A> Visual Basic usa para percorrer a coleção.  
  
### <a name="narrowing-conversions"></a>Conversões de redução  
 Quando `Option Strict` é definido como `On`, conversões de estreitamento normalmente causam erros de compilador. Em um `For Each` instrução, no entanto, as conversões de elementos no `group` para `element` são avaliadas e executada em tempo de execução e erros de compilador causados por conversões de estreitamento são suprimidos.  
  
 No exemplo a seguir, a atribuição de `m` como o valor inicial de `n` não compilar quando `Option Strict` está em como a conversão de um `Long` para um `Integer` é uma conversão de restrição. No `For Each` instrução, no entanto, não é nenhum erro de compilador relatados, mesmo que a atribuição ao `number` requer a mesma conversão de `Long` para `Integer`. No `For Each` instrução que contém um número grande, um erro de tempo de execução ocorre quando <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>é aplicado a grande número.</xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>  
  
 [!code-vb[VbVbalrStatements&#89;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>Chamadas de IEnumerator  
 Quando a execução de um `For Each`... `Next` loop for iniciado, o Visual Basic verifica se `group` refere-se a um objeto de coleção válido. Caso contrário, ele gerará uma exceção. Caso contrário, ele chama o <xref:System.Collections.IEnumerator.MoveNext%2A>método e o <xref:System.Collections.IEnumerator.Current%2A>propriedade do objeto enumerador retornar o primeiro elemento.</xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> Se `MoveNext` indica que não há nenhum próximo elemento, ou seja, se a coleção estiver vazia, o `For Each` loop para e o controle passa para a instrução depois de `Next` instrução. Caso contrário, o Visual Basic define `element` para o primeiro elemento e executa o bloco de instrução.  
  
 Cada vez que o Visual Basic encontra o `Next` instrução, ele retornará para a `For Each` instrução. Novamente, ele chama `MoveNext` e `Current` para retornar o próximo elemento e novamente ele executa o bloco de ou para o loop dependendo do resultado. Esse processo continua até `MoveNext` indica que não há nenhum próximo elemento ou um `Exit For` declaração é encontrada.  
  
 **Modificação da coleção.** O objeto de enumerador retornado por <xref:System.Collections.IEnumerable.GetEnumerator%2A>normalmente não permite que você altere a coleção, adicionar, excluir, substituir ou reordenar todos os elementos.</xref:System.Collections.IEnumerable.GetEnumerator%2A> Se você alterar a coleção depois que você inicia um `For Each`... `Next` loop, o objeto enumerador se torna inválido e faz com que a próxima tentativa de acessar um elemento um <xref:System.InvalidOperationException>exceção.</xref:System.InvalidOperationException>  
  
 No entanto, esse bloqueio de modificação não é determinado pelo [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], mas em vez disso, a implementação do <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> É possível implementar `IEnumerable` de forma que permite a modificação durante a iteração. Se você estiver considerando fazer essa modificação dinâmica, certifique-se de que você entenda as características do `IEnumerable` implementação na coleção que você está usando.  
  
 **Modificação de elementos da coleção.** O <xref:System.Collections.IEnumerator.Current%2A>é de propriedade do objeto enumerador [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), e retorna uma cópia local de cada elemento da coleção.</xref:System.Collections.IEnumerator.Current%2A> Isso significa que você não pode modificar os próprios elementos em um `For Each`... `Next` loop. Qualquer alteração que afeta somente a cópia local do `Current` e não será refletida de volta para a coleção subjacente. No entanto, se um elemento for um tipo de referência, você pode modificar os membros da instância para qual ele aponta. O exemplo a seguir modifica o `BackColor` membro de cada `thisControl` elemento. No entanto, você não pode modificar `thisControl` em si.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 O exemplo anterior pode modificar o `BackColor` membro de cada `thisControl` elemento, embora ele não é possível modificar `thisControl` em si.  
  
 **Atravessando matrizes.** Porque o <xref:System.Array>classe implementa o <xref:System.Collections.IEnumerable>interface, todas as matrizes expõem o <xref:System.Array.GetEnumerator%2A>método.</xref:System.Array.GetEnumerator%2A> </xref:System.Collections.IEnumerable> </xref:System.Array> Isso significa que você pode percorrer uma matriz com um `For Each`... `Next` loop. No entanto, você pode apenas ler os elementos da matriz. Você não pode alterá-los.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lista todas as pastas na pasta C:\ usando a <xref:System.IO.DirectoryInfo>classe.</xref:System.IO.DirectoryInfo>  
  
 [!code-vb[VbVbalrStatements&#124;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um procedimento para uma coleção de classificação. O exemplo classifica instâncias de um `Car` classe são armazenados em <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601> O `Car` classe implementa o <xref:System.IComparable%601>interface, que requer que o <xref:System.IComparable%601.CompareTo%2A>método ser implementado.</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601>  
  
 Cada chamada para o <xref:System.IComparable%601.CompareTo%2A>método faz uma comparação única que é usada para classificação.</xref:System.IComparable%601.CompareTo%2A> Códigos escritos pelo usuário no `CompareTo` método retorna um valor para cada comparação do objeto atual com outro objeto. O valor retornado é menor que zero se o objeto atual é menor do que o outro objeto maior do que zero se o objeto atual é maior do que o outro objeto e zero se eles forem iguais. Isso permite que você defina no código os critérios para maior que, menor que e igual.  
  
 No `ListCars` método, o `cars.Sort()` instrução classifica a lista. Essa chamada para o <xref:System.Collections.Generic.List%601.Sort%2A>método o <xref:System.Collections.Generic.List%601>faz com que o `CompareTo` método a ser chamado automaticamente para o `Car` objetos no `List`.</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A>  
  
 [!code-vb[VbVbalrStatements&125;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Inicializadores de objeto: Tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
