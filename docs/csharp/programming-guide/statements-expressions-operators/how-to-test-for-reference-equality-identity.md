---
title: Como testar a igualdade de referência (identidade)-guia de programação C#
description: Saiba como testar a igualdade de referência (identidade). Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 1d1a0e5d80ac8d2a689e75acbc6099b92e16f23f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151435"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="0896d-104">Como testar a igualdade de referência (identidade) (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="0896d-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>

<span data-ttu-id="0896d-105">Não é necessário implementar qualquer lógica personalizada para dar suporte a comparações de igualdade de referência em seus tipos.</span><span class="sxs-lookup"><span data-stu-id="0896d-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="0896d-106">Essa funcionalidade é fornecida para todos os tipos pelo método estático <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0896d-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0896d-107">O exemplo a seguir mostra como determinar se duas variáveis têm *igualdade de referência*, que significa que elas se referem ao mesmo objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="0896d-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="0896d-108">O exemplo também mostra por que <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> sempre retorna `false` para tipos de valor e por que você não deve usar <xref:System.Object.ReferenceEquals%2A> para determinar igualdade de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0896d-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0896d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0896d-109">Example</span></span>  

 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="0896d-110">A implementação de `Equals` na classe base universal <xref:System.Object?displayProperty=nameWithType> também realiza uma verificação de igualdade de referência, mas é melhor não usar isso, porque, se uma classe substituir o método, os resultados poderão não ser o que você espera.</span><span class="sxs-lookup"><span data-stu-id="0896d-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="0896d-111">O mesmo é verdadeiro para os operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="0896d-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="0896d-112">Quando eles estiverem operando em tipos de referência, o comportamento padrão de `==` e `!=` é realizar uma verificação de igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="0896d-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="0896d-113">No entanto, as classes derivadas podem sobrecarregar o operador para executar uma verificação de igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="0896d-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="0896d-114">Para minimizar o potencial de erro, será melhor usar sempre <xref:System.Object.ReferenceEquals%2A> quando for necessário determinar se os dois objetos têm igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="0896d-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="0896d-115">Cadeias de caracteres constantes dentro do mesmo assembly sempre são internalizadas pelo runtime.</span><span class="sxs-lookup"><span data-stu-id="0896d-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="0896d-116">Ou seja, apenas uma instância de cada cadeia de caracteres literal única é mantida.</span><span class="sxs-lookup"><span data-stu-id="0896d-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="0896d-117">No entanto, o runtime não garante que cadeias de caracteres criadas em runtime sejam internalizadas nem garante que duas de cadeias de caracteres constantes iguais em diferentes assemblies sejam internalizadas.</span><span class="sxs-lookup"><span data-stu-id="0896d-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0896d-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="0896d-118">See also</span></span>

- [<span data-ttu-id="0896d-119">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="0896d-119">Equality Comparisons</span></span>](./equality-comparisons.md)
