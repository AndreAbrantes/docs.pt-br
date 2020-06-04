---
title: Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: b278dcc10a8a4e9e67aacdb16dca2588d2ebd0f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409772"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="5ad65-102">Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos</span><span class="sxs-lookup"><span data-stu-id="5ad65-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="5ad65-103">Não é possível inferir os tipos de dados dos parâmetros de tipo com base nesses argumentos.</span><span class="sxs-lookup"><span data-stu-id="5ad65-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="5ad65-104">A especificação explícita dos tipos de dados pode corrigir esse erro.</span><span class="sxs-lookup"><span data-stu-id="5ad65-104">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="5ad65-105">Esse erro ocorre quando a resolução de sobrecarga falhou.</span><span class="sxs-lookup"><span data-stu-id="5ad65-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="5ad65-106">Ele ocorre como uma mensagem subordinada que declara por que um determinado candidato de sobrecarga foi eliminado.</span><span class="sxs-lookup"><span data-stu-id="5ad65-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="5ad65-107">A mensagem de erro explica que o compilador não pode usar a inferência de tipos para localizar tipos de dados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="5ad65-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="5ad65-108">Ao especificar argumentos não é uma opção (por exemplo, para operadores de consulta em expressões de consulta), a mensagem de erro é exibida sem a segunda sentença.</span><span class="sxs-lookup"><span data-stu-id="5ad65-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="5ad65-109">O código a seguir demonstra o erro.</span><span class="sxs-lookup"><span data-stu-id="5ad65-109">The following code demonstrates the error.</span></span>

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

<span data-ttu-id="5ad65-110">**ID do erro:** BC36647 e BC36644</span><span class="sxs-lookup"><span data-stu-id="5ad65-110">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5ad65-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5ad65-111">To correct this error</span></span>

<span data-ttu-id="5ad65-112">Você pode especificar um tipo de dados para o parâmetro de tipo ou parâmetros em vez de depender da inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="5ad65-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ad65-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ad65-113">See also</span></span>

- [<span data-ttu-id="5ad65-114">Conversão de delegado reduzida</span><span class="sxs-lookup"><span data-stu-id="5ad65-114">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="5ad65-115">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ad65-115">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="5ad65-116">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ad65-116">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
