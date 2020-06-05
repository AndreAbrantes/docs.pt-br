---
title: O construtor '<name>' não pode se chamar
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409797"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="6b5ec-102">O construtor '\<name>' não pode se chamar</span><span class="sxs-lookup"><span data-stu-id="6b5ec-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="6b5ec-103">Um `Sub New` procedimento em uma classe ou estrutura chama a si mesmo.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="6b5ec-104">A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ela é criada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="6b5ec-105">Uma classe ou estrutura pode ter vários construtores, desde que todos tenham diferentes listas de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="6b5ec-106">Um construtor tem permissão para chamar outro construtor para executar sua funcionalidade, além de seu próprio.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="6b5ec-107">Mas não faz sentido para um Construtor chamar a si mesmo e, de fato, resultaria em recursão infinita, se permitido.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="6b5ec-108">**ID do erro:** BC30298</span><span class="sxs-lookup"><span data-stu-id="6b5ec-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b5ec-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6b5ec-109">To correct this error</span></span>  
  
1. <span data-ttu-id="6b5ec-110">Verifique a lista de parâmetros do construtor que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="6b5ec-111">Ele deve ser diferente do construtor que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="6b5ec-112">Se você não pretende chamar um Construtor diferente, remova `Sub New` totalmente a chamada.</span><span class="sxs-lookup"><span data-stu-id="6b5ec-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5ec-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b5ec-113">See also</span></span>

- [<span data-ttu-id="6b5ec-114">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="6b5ec-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
