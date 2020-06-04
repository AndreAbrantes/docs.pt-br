---
title: Me, My, MyBase e MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: b4470e5c178c0f66dc33956ea0131d4eabc51d46
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397461"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="c98b2-102">Me, My, MyBase e MyClass no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c98b2-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="c98b2-103">`Me`, `My` , `MyBase` e `MyClass` em Visual Basic têm nomes semelhantes, mas finalidades diferentes.</span><span class="sxs-lookup"><span data-stu-id="c98b2-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="c98b2-104">Este tópico descreve cada uma dessas entidades para diferenciá-las.</span><span class="sxs-lookup"><span data-stu-id="c98b2-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="c98b2-105">Eu</span><span class="sxs-lookup"><span data-stu-id="c98b2-105">Me</span></span>  
 <span data-ttu-id="c98b2-106">A `Me` palavra-chave fornece uma maneira de se referir à instância específica de uma classe ou estrutura na qual o código está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="c98b2-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="c98b2-107">`Me`comporta-se como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="c98b2-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="c98b2-108">O uso do `Me` é particularmente útil para passar informações sobre a instância em execução no momento de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="c98b2-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="c98b2-109">Por exemplo, suponha que você tenha o procedimento a seguir em um módulo.</span><span class="sxs-lookup"><span data-stu-id="c98b2-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="c98b2-110">Você pode chamar esse procedimento e passar a instância atual da <xref:System.Windows.Forms.Form> classe como um argumento usando a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="c98b2-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="c98b2-111">Meu</span><span class="sxs-lookup"><span data-stu-id="c98b2-111">My</span></span>  
 <span data-ttu-id="c98b2-112">O `My` recurso fornece acesso fácil e intuitivo a várias classes de .NET Framework, permitindo que o usuário Visual Basic interaja com o computador, o aplicativo, as configurações, os recursos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c98b2-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="c98b2-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="c98b2-113">MyBase</span></span>  
 <span data-ttu-id="c98b2-114">A `MyBase` palavra-chave se comporta como uma variável de objeto referindo-se à classe base da instância atual de uma classe.</span><span class="sxs-lookup"><span data-stu-id="c98b2-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="c98b2-115">`MyBase`normalmente é usado para acessar membros da classe base que são substituídos ou sombreados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c98b2-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="c98b2-116">`MyBase.New`é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c98b2-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="c98b2-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="c98b2-117">MyClass</span></span>  
 <span data-ttu-id="c98b2-118">A `MyClass` palavra-chave se comporta como uma variável de objeto referindo-se à instância atual de uma classe como implementada originalmente.</span><span class="sxs-lookup"><span data-stu-id="c98b2-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="c98b2-119">`MyClass`é semelhante a `Me` , mas todas as chamadas de método nela são tratadas como se o método estivesse `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="c98b2-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98b2-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="c98b2-120">See also</span></span>

- [<span data-ttu-id="c98b2-121">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="c98b2-121">Inheritance Basics</span></span>](../language-features/objects-and-classes/inheritance-basics.md)
