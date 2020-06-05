---
title: Definição do tipo anônimo
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404895"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="9bdab-102">Definição do tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdab-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="9bdab-103">Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.</span><span class="sxs-lookup"><span data-stu-id="9bdab-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="9bdab-104">Código gerado pelo compilador</span><span class="sxs-lookup"><span data-stu-id="9bdab-104">Compiler-Generated Code</span></span>

<span data-ttu-id="9bdab-105">Para a seguinte definição de `product` , o compilador cria uma nova definição de classe que contém propriedades `Name` , `Price` e `OnHand` .</span><span class="sxs-lookup"><span data-stu-id="9bdab-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="9bdab-106">A definição de classe contém definições de propriedade semelhantes às seguintes.</span><span class="sxs-lookup"><span data-stu-id="9bdab-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="9bdab-107">Observe que não há nenhum `Set` método para as propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="9bdab-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="9bdab-108">Os valores das propriedades de chave são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="9bdab-108">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="9bdab-109">Além disso, as definições de tipo anônimo contêm um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9bdab-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="9bdab-110">Os construtores que exigem parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="9bdab-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="9bdab-111">Se uma declaração de tipo anônimo contiver pelo menos uma propriedade de chave, a definição de tipo substituirá três membros herdados de <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> e <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="9bdab-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="9bdab-112">Se nenhuma propriedade de chave for declarada, somente <xref:System.Object.ToString%2A> será substituído.</span><span class="sxs-lookup"><span data-stu-id="9bdab-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="9bdab-113">As substituições fornecem a seguinte funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="9bdab-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="9bdab-114">`Equals`retorna `True` se duas instâncias de tipo anônimo forem a mesma instância ou se atenderem às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="9bdab-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="9bdab-115">Eles têm o mesmo número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="9bdab-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="9bdab-116">As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos tipos inferidos.</span><span class="sxs-lookup"><span data-stu-id="9bdab-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="9bdab-117">Comparações de nome não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9bdab-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="9bdab-118">Pelo menos uma das propriedades é uma propriedade de chave e a `Key` palavra-chave é aplicada às mesmas propriedades.</span><span class="sxs-lookup"><span data-stu-id="9bdab-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="9bdab-119">A comparação de cada par correspondente de propriedades de chave retorna `True` .</span><span class="sxs-lookup"><span data-stu-id="9bdab-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="9bdab-120">Por exemplo, nos exemplos a seguir, `Equals` retorna `True` apenas para `employee01` e `employee08` .</span><span class="sxs-lookup"><span data-stu-id="9bdab-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="9bdab-121">O comentário antes de cada linha especifica o motivo pelo qual a nova instância não corresponde `employee01` .</span><span class="sxs-lookup"><span data-stu-id="9bdab-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="9bdab-122">`GetHashcode`fornece um algoritmo GetHashCode adequadamente exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9bdab-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="9bdab-123">O algoritmo usa apenas as propriedades de chave para calcular o código hash.</span><span class="sxs-lookup"><span data-stu-id="9bdab-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="9bdab-124">`ToString`Retorna uma cadeia de caracteres de valores de propriedade concatenados, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bdab-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="9bdab-125">As propriedades Key e non-key são incluídas.</span><span class="sxs-lookup"><span data-stu-id="9bdab-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="9bdab-126">As propriedades nomeadas explicitamente de um tipo anônimo não podem entrar em conflito com esses métodos gerados.</span><span class="sxs-lookup"><span data-stu-id="9bdab-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="9bdab-127">Ou seja, você não pode usar `.Equals` , `.GetHashCode` ou `.ToString` para nomear uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="9bdab-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="9bdab-128">As definições de tipo anônimo que incluem pelo menos uma propriedade de chave também implementam a <xref:System.IEquatable%601?displayProperty=nameWithType> interface, em que `T` é o tipo do tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="9bdab-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="9bdab-129">Declarações de tipo anônimo criam o mesmo tipo anônimo somente se eles ocorrerem no mesmo assembly, suas propriedades têm os mesmos nomes e os mesmos tipos inferidos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="9bdab-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bdab-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bdab-130">See also</span></span>

- [<span data-ttu-id="9bdab-131">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="9bdab-131">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="9bdab-132">Como inferir nomes e tipos de propriedade na declaração de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="9bdab-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
