---
title: Estruturas de controle aninhadas
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: 290366d9d9428cefee108ac472fbe7c0eb66d82e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084158"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="f117a-102">Estruturas de controle aninhadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f117a-102">Nested Control Structures (Visual Basic)</span></span>

<span data-ttu-id="f117a-103">Você pode posicionar as instruções de controle dentro de outras instruções de controle, por exemplo, um `If...Then...Else` bloco dentro de um `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="f117a-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="f117a-104">Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="f117a-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="f117a-105">Níveis de aninhamento</span><span class="sxs-lookup"><span data-stu-id="f117a-105">Nesting Levels</span></span>  

 <span data-ttu-id="f117a-106">As estruturas de controle no Visual Basic podem ser aninhadas para quantos níveis você desejar.</span><span class="sxs-lookup"><span data-stu-id="f117a-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="f117a-107">É uma prática comum tornar as estruturas aninhadas mais legíveis recuando o corpo de cada uma.</span><span class="sxs-lookup"><span data-stu-id="f117a-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="f117a-108">O editor de ambiente de desenvolvimento integrado (IDE) faz isso automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f117a-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="f117a-109">No exemplo a seguir, o procedimento `sumRows` adiciona os elementos positivos de cada linha da matriz.</span><span class="sxs-lookup"><span data-stu-id="f117a-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="f117a-110">No exemplo anterior, a primeira `Next` instrução fecha o loop interno `For` e a última `Next` instrução fecha o loop externo `For` .</span><span class="sxs-lookup"><span data-stu-id="f117a-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="f117a-111">Da mesma forma, em instruções aninhadas `If` , as `End If` instruções se aplicam automaticamente à instrução anterior mais próxima `If` .</span><span class="sxs-lookup"><span data-stu-id="f117a-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="f117a-112">`Do`Os loops aninhados funcionam de maneira semelhante, com a `Loop` instrução mais interna correspondente à instrução mais interna `Do` .</span><span class="sxs-lookup"><span data-stu-id="f117a-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f117a-113">Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas.</span><span class="sxs-lookup"><span data-stu-id="f117a-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="f117a-114">Por exemplo, quando você clica `If` em uma `If...Then...Else` construção, todas as instâncias de `If` ,, `Then` `ElseIf` , `Else` e `End If` na construção são realçadas.</span><span class="sxs-lookup"><span data-stu-id="f117a-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="f117a-115">Para mover para a próxima palavra-chave realçada ou anterior, pressione CTRL + SHIFT + seta para baixo ou CTRL + SHIFT + seta para cima.</span><span class="sxs-lookup"><span data-stu-id="f117a-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="f117a-116">Aninhando diferentes tipos de estruturas de controle</span><span class="sxs-lookup"><span data-stu-id="f117a-116">Nesting Different Kinds of Control Structures</span></span>  

 <span data-ttu-id="f117a-117">Você pode aninhar um tipo de estrutura de controle dentro de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="f117a-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="f117a-118">O exemplo a seguir usa um `With` bloco dentro de um `For Each` loop e blocos aninhados `If` dentro do `With` bloco.</span><span class="sxs-lookup"><span data-stu-id="f117a-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="f117a-119">Sobrepondo estruturas de controle</span><span class="sxs-lookup"><span data-stu-id="f117a-119">Overlapping Control Structures</span></span>  

 <span data-ttu-id="f117a-120">Não é possível sobrepor estruturas de controle.</span><span class="sxs-lookup"><span data-stu-id="f117a-120">You cannot overlap control structures.</span></span> <span data-ttu-id="f117a-121">Isso significa que qualquer estrutura aninhada deve estar completamente contida na próxima estrutura mais interna.</span><span class="sxs-lookup"><span data-stu-id="f117a-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="f117a-122">Por exemplo, a organização a seguir é inválida porque o `For` loop termina antes de o `With` bloco interno terminar.</span><span class="sxs-lookup"><span data-stu-id="f117a-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="f117a-124">O compilador Visual Basic detecta essas estruturas de controle sobrepostas e sinaliza um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f117a-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f117a-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="f117a-125">See also</span></span>

- [<span data-ttu-id="f117a-126">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="f117a-126">Control Flow</span></span>](index.md)
- [<span data-ttu-id="f117a-127">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="f117a-127">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="f117a-128">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="f117a-128">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="f117a-129">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="f117a-129">Other Control Structures</span></span>](other-control-structures.md)
