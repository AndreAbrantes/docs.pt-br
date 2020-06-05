---
title: "'<typename>' é um tipo delegado"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382166"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="c34f3-102">'\<typename>' é um tipo delegado</span><span class="sxs-lookup"><span data-stu-id="c34f3-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="c34f3-103">' \<typename> ' é um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="c34f3-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="c34f3-104">A construção delegate permite apenas uma única expressão AddressOf como uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="c34f3-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="c34f3-105">Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.</span><span class="sxs-lookup"><span data-stu-id="c34f3-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="c34f3-106">Uma `New` cláusula que cria uma instância de uma classe delegate fornece uma lista de argumentos inválida para o construtor delegate.</span><span class="sxs-lookup"><span data-stu-id="c34f3-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="c34f3-107">Você pode fornecer apenas uma única `AddressOf` expressão ao criar uma nova instância de delegado.</span><span class="sxs-lookup"><span data-stu-id="c34f3-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="c34f3-108">Esse erro pode ocorrer se você não passar nenhum argumento para o construtor delegado, se você passar mais de um argumento, ou se você passar um único argumento que não seja uma expressão válida `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="c34f3-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="c34f3-109">**ID do erro:** BC32008</span><span class="sxs-lookup"><span data-stu-id="c34f3-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c34f3-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c34f3-110">To correct this error</span></span>  
  
- <span data-ttu-id="c34f3-111">Use uma única `AddressOf` expressão na lista de argumentos para a classe delegate na `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="c34f3-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34f3-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="c34f3-112">See also</span></span>

- [<span data-ttu-id="c34f3-113">Novo operador</span><span class="sxs-lookup"><span data-stu-id="c34f3-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="c34f3-114">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="c34f3-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="c34f3-115">Delegados</span><span class="sxs-lookup"><span data-stu-id="c34f3-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="c34f3-116">Como invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="c34f3-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
