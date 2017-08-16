---
title: Para... Next Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
dev_langs:
- VB
helpviewer_keywords:
- infinite loops
- Next keyword, For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword, For...Next statements
- operator overloading, For...Next statement
- To keyword, For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement, For...Next
- For...Next statements
- loop structures, For...Next
- loops, infinite
- Exit statement, For...Next statements
- For statement
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
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
ms.openlocfilehash: 9f7577a21aa0cd89e12955fa5adcd3b3eb2748b3
ms.lasthandoff: 03/13/2017

---
# <a name="fornext-statement-visual-basic"></a>Instrução For...Next (Visual Basic)
Repete um grupo de instruções um número especificado de vezes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>Partes  
  
|Parte|Descrição|  
|----------|-----------------|  
|`counter`|Necessário o `For` instrução. Variável numérica. A variável de controle do loop. Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.|  
|`datatype`|Opcional. Tipo de dados de `counter`. Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.|  
|`start`|Necessário. Expressão numérica. O valor inicial de `counter`.|  
|`end`|Necessário. Expressão numérica. O valor final do `counter`.|  
|`step`|Opcional. Expressão numérica. O valor pelo qual `counter` é incrementado toda vez pelo loop.|  
|`statements`|Opcional. Uma ou mais instruções entre `For` e `Next` que executam o número de vezes especificado.|  
|`Continue For`|Opcional. Transfere o controle para a próxima iteração do loop.|  
|`Exit For`|Opcional. Transfere o controle do `For` loop.|  
|`Next`|Necessário. Finaliza a definição de `For` loop.|  
  
> [!NOTE]
>  O `To` nesta declaração, a palavra-chave é usada para especificar o intervalo para o contador. Você também pode usar essa palavra-chave no [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) e nas declarações de matriz. Para obter mais informações sobre declarações de matriz, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Exemplos simples  
 Você usa um `For`... `Next` estrutura quando quiser repetir um conjunto de instruções um número definido de vezes.  
  
 No exemplo a seguir, o `index` variável começa com um valor de 1 e incrementado com cada iteração do loop, terminando após o valor de `index` atinge 5.  
  
 [!code-vb[VbVbalrStatements&#111;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 No exemplo a seguir, o `number` variável começa em 2 e será reduzida 0,25 em cada iteração do loop, terminando após o valor do `number` chegar a 0. O `Step` argumento `-.25` reduz o valor por 0,25 em cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements&#112;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  Um [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) funciona bem quando você não sabe com antecedência quantas vezes para executar as instruções no loop. No entanto, quando você pretende executar o loop um número específico de vezes, uma `For`... `Next` loop é uma opção melhor. Determinar o número de iterações quando você entra no loop.  
  
## <a name="nesting-loops"></a>Loops aninhados  
 Você pode aninhar `For` loops colocando um loop dentro de outro. O exemplo a seguir demonstra aninhada `For`... `Next` estruturas que têm valores diferentes. O loop externo cria uma cadeia de caracteres para cada iteração do loop. Interno loop decrementa uma variável de contador de loop para cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements&#113;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Ao aninhar loops, cada loop deve ter um único `counter` variável.  
  
 Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Sair para e continuar  
 O `Exit For` instrução imediatamente encerra o `For`...`Next` loop for e transfere o controle para a instrução que segue o `Next` instrução.  
  
 O `Continue For` instrução transfere o controle imediatamente para a próxima iteração do loop. Para obter mais informações, consulte [continuar instrução](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir ilustra o uso do `Continue For` e `Exit For` instruções.  
  
 [!code-vb[VbVbalrStatements&#115;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Você pode colocar qualquer número de `Exit For` instruções em um `For`...`Next` loop. Quando usado dentro aninhadas `For`...`Next` loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit For`é frequentemente usado após avaliar alguma condição (por exemplo, em um `If`... `Then`... `Else` estrutura). Você talvez queira usar `Exit For` para as seguintes condições:  
  
-   Continuando a iteração é desnecessária ou impossível. Um valor errado ou uma solicitação de encerramento pode criar essa condição.  
  
-   A `Try`... `Catch`... `Finally` instrução captura uma exceção. Você pode usar `Exit For` no final o `Finally` bloco.  
  
-   Você tem um loop infinito, o que é um loop que pode executar um número grande ou mesmo infinito de vezes. Se você detectar tal condição, você pode usar `Exit For` para escapar do loop. Para obter mais informações, consulte [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 Quando um `For`... `Next` loop é iniciado, Visual Basic avalia `start`, `end`, e `step`. Visual Basic avalia esses valores apenas nesse momento e, em seguida, atribui `start` para `counter`. Antes da instrução do bloco é executado, Visual Basic compara `counter` para `end`. Se `counter` já é maior do que o `end` valor (ou menor se `step` é negativo), o `For` loop termina e o controle passa para a instrução que segue o `Next` instrução. Caso contrário, o bloco de instrução é executada.  
  
 Cada vez que o Visual Basic encontra o `Next` instrução, ele é incrementado `counter` por `step` e retorna para o `For` instrução. Novamente, ele compara `counter` para `end`, e novamente ele executa o bloco ou sai do loop, dependendo do resultado. Esse processo continua até `counter` passa `end` ou um `Exit For` declaração é encontrada.  
  
 O loop não para até `counter` passou `end`. Se `counter` é igual a `end`, o loop continua. A comparação que determina se deve executar o bloco for `counter`  <=  `end` se `step` for positivo e `counter`  >=  `end` se `step` for negativo.  
  
 Se você alterar o valor de `counter` enquanto dentro de um loop, seu código pode ser mais difícil de ler e de depuração. Alterar o valor de `start`, `end`, ou `step` não afeta os valores de iteração determinadas quando o loop foi acessado pela primeira vez.  
  
 Se você aninhar loops, o compilador sinaliza um erro se encontra o `Next` declaração de um nível de aninhamento externo antes do `Next` declaração de um nível interno. No entanto, o compilador pode detectar isso sobreposição de erro somente se você especificar `counter` em cada `Next` instrução.  
  
### <a name="step-argument"></a>Argumento de etapa  
 O valor de `step` pode ser positivo ou negativo. Esse parâmetro determina o processamento de loop de acordo com a tabela a seguir:  
  
|**Valor da etapa**|**O loop é executado se**|  
|--------------------|--------------------------|  
|Positivo ou zero|`counter` <= `end`|  
|Negativo|`counter` >= `end`|  
  
 O valor padrão de `step` é 1.  
  
###  <a name="BKMK_Counter"></a>Argumento do contador  
 A tabela a seguir indica se `counter` define uma nova variável local com escopo para todo o `For…Next` loop. Essa decisão depende se `datatype` está presente e se `counter` já está definido.  
  
|É `datatype` presente?|É `counter` já definido?|Resultado (se `counter` define uma nova variável local com escopo para todo o `For...Next` loop)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Não|Sim|Não, porque `counter` já está definido. Se o escopo de `counter` não são locais para o procedimento, ocorre um aviso de tempo de compilação.|  
|Não|Não|Sim. O tipo de dados é inferido a partir do `start`, `end`, e `step` expressões. Para obter informações sobre a inferência de tipo, consulte [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Sim|Sim|Sim, mas somente se existente `counter` variável é definida fora do procedimento. Essa variável permanece separada. Se o escopo de existente `counter` variável é local para o procedimento, ocorre um erro de tempo de compilação.|  
|Sim|Não|Sim.|  
  
 O tipo de dados `counter` determina o tipo da iteração, que deve ser um dos seguintes tipos:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.  
  
-   Uma enumeração que declarar usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   Um `Object`.  
  
-   Um tipo `T` que tem os seguintes operadores, onde `B` é um tipo que pode ser usado em um `Boolean` expressão.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Opcionalmente, você pode especificar o `counter` variável no `Next` instrução. Essa sintaxe melhora a legibilidade do programa, especialmente se você tiver aninhado `For` loops. Você deve especificar a variável que aparece no correspondente `For` instrução.  
  
 O `start`, `end`, e `step` expressões podem ser avaliada como qualquer tipo de dados que amplia para o tipo de `counter`. Se você usar um tipo definido pelo usuário para `counter`, talvez você precise definir o `CType` operador de conversão para converter os tipos de `start`, `end`, ou `step` para o tipo de `counter`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir remove todos os elementos de uma lista genérica. Em vez de um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md), o exemplo mostra uma `For`... `Next` instrução que itera em ordem decrescente. O exemplo usa essa técnica porque o `removeAt` método faz com que elementos após o elemento removido para ter um valor de índice mais baixo.  
  
 [!code-vb[VbVbalrStatements&#114;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir itera por meio de uma enumeração que é declarada usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements&#116;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, os parâmetros da instrução usam uma classe que tenha sobrecargas do operador para o `+`, `-`, `>=`, e `<=` operadores.  
  
 [!code-vb[VbVbalrStatements&#117;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601>   
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
