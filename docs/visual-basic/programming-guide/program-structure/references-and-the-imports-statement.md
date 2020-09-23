---
title: Referências e a instrução Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097898"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="c4393-102">Referências e a instrução Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4393-102">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="c4393-103">Você pode disponibilizar objetos externos para seu projeto escolhendo o comando **Adicionar referência** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="c4393-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="c4393-104">Referências no Visual Basic podem apontar para assemblies, que são como bibliotecas de tipos, mas contêm mais informações.</span><span class="sxs-lookup"><span data-stu-id="c4393-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="c4393-105">A instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c4393-105">The Imports Statement</span></span>  

 <span data-ttu-id="c4393-106">Os assemblies incluem um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="c4393-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="c4393-107">Quando você adiciona uma referência a um assembly, também pode adicionar uma `Imports` instrução a um módulo que controla a visibilidade dos namespaces desse assembly dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="c4393-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="c4393-108">A `Imports` instrução fornece um contexto de escopo que permite que você use apenas a parte do namespace necessário para fornecer uma referência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c4393-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="c4393-109">A `Imports` instrução tem a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="c4393-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="c4393-110">`Aliasname` refere-se a um nome curto que você pode usar no código para se referir a um namespace importado.</span><span class="sxs-lookup"><span data-stu-id="c4393-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="c4393-111">`Namespace` o é um namespace disponível por meio de uma referência de projeto, por meio de uma definição dentro do projeto ou por meio de uma `Imports` instrução anterior.</span><span class="sxs-lookup"><span data-stu-id="c4393-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="c4393-112">Um módulo pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="c4393-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="c4393-113">Eles devem aparecer depois `Option` de qualquer instrução, se presente, mas antes de qualquer outro código.</span><span class="sxs-lookup"><span data-stu-id="c4393-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4393-114">Não confunda referências de projeto com a `Imports` instrução ou a `Declare` instrução.</span><span class="sxs-lookup"><span data-stu-id="c4393-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="c4393-115">Referências de projeto tornam objetos externos, como objetos em assemblies, disponíveis para projetos Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4393-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="c4393-116">A `Imports` instrução é usada para simplificar o acesso a referências de projeto, mas não fornece acesso a esses objetos.</span><span class="sxs-lookup"><span data-stu-id="c4393-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="c4393-117">A `Declare` instrução é usada para declarar uma referência a um procedimento externo em uma dll (biblioteca de vínculo dinâmico).</span><span class="sxs-lookup"><span data-stu-id="c4393-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="c4393-118">Usando aliases com a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c4393-118">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="c4393-119">A `Imports` instrução facilita o acesso a métodos de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências.</span><span class="sxs-lookup"><span data-stu-id="c4393-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="c4393-120">Os aliases permitem que você atribua um nome mais amigável a apenas uma parte de um namespace.</span><span class="sxs-lookup"><span data-stu-id="c4393-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="c4393-121">Por exemplo, a sequência de retorno de carro/alimentação de linha que faz com que uma única parte do texto seja exibida em várias linhas faz parte do <xref:Microsoft.VisualBasic.ControlChars> módulo no <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="c4393-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c4393-122">Para usar essa constante em um programa sem um alias, você precisaria digitar o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c4393-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c4393-123">`Imports` as instruções sempre devem ser as primeiras linhas imediatamente após qualquer `Option` instrução em um módulo.</span><span class="sxs-lookup"><span data-stu-id="c4393-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="c4393-124">O fragmento de código a seguir mostra como importar e atribuir um alias ao <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> módulo:</span><span class="sxs-lookup"><span data-stu-id="c4393-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c4393-125">Referências futuras para esse namespace podem ser consideravelmente mais curtas:</span><span class="sxs-lookup"><span data-stu-id="c4393-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c4393-126">Se uma `Imports` instrução não incluir um nome de alias, os elementos definidos no namespace importado poderão ser usados no módulo sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="c4393-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="c4393-127">Se o nome do alias for especificado, ele deverá ser usado como um qualificador para nomes contidos nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="c4393-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4393-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4393-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="c4393-129">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4393-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="c4393-130">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="c4393-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c4393-131">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="c4393-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
