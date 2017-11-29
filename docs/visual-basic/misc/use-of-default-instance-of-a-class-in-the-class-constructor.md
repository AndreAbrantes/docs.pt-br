---
title: "Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a0c54c6e62f9bdc7fe510500a486461d26636d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="98b3b-102">Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita</span><span class="sxs-lookup"><span data-stu-id="98b3b-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="98b3b-103">Uma instância padrão de uma classe foi usada no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="98b3b-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="98b3b-104">Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="98b3b-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98b3b-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="98b3b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="98b3b-106">Remova a instância padrão do construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="98b3b-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b3b-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98b3b-107">See Also</span></span>  
 [<span data-ttu-id="98b3b-108">Construtores</span><span class="sxs-lookup"><span data-stu-id="98b3b-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
