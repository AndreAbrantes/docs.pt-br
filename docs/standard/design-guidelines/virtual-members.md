---
title: Membros virtuais
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 22eb71ccfc1b9a3d359b0453e4ff47f3f41827f5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828394"
---
# <a name="virtual-members"></a><span data-ttu-id="7cf3d-102">Membros virtuais</span><span class="sxs-lookup"><span data-stu-id="7cf3d-102">Virtual Members</span></span>
<span data-ttu-id="7cf3d-103">Os membros virtuais podem ser substituídos, alterando assim o comportamento da subclasse.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="7cf3d-104">Eles são bastante semelhantes aos retornos de chamada em termos da extensibilidade que eles fornecem, mas são melhores em termos de desempenho de execução e consumo de memória.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="7cf3d-105">Além disso, os membros virtuais sentem-se mais naturais em cenários que exigem a criação de um tipo especial de um Type (especialização) existente.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="7cf3d-106">Os membros virtuais têm um desempenho melhor do que retornos de chamada e eventos, mas não têm melhor desempenho do que métodos não virtuais.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="7cf3d-107">A principal desvantagem dos membros virtuais é que o comportamento de um membro virtual só pode ser modificado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="7cf3d-108">O comportamento de um retorno de chamada pode ser modificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="7cf3d-109">Membros virtuais, como retornos de chamada (e talvez mais de retornos de chamada), são caros de projetar, testar e manter, pois qualquer chamada para um membro virtual pode ser substituída de maneiras imprevisíveis e pode executar código arbitrário.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="7cf3d-110">Além disso, geralmente é necessário muito mais esforço para definir claramente o contrato de membros virtuais, de modo que o custo de criá-los e documentá-los é maior.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="7cf3d-111">❌ Não torne os membros virtuais, a menos que você tenha um bom motivo para fazer isso e esteja ciente de todos os custos relacionados à criação, ao teste e à manutenção de membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="7cf3d-112">Os membros virtuais são menos tolerante em termos de alterações que podem ser feitas a eles sem a necessidade de perder a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="7cf3d-113">Além disso, eles são mais lentos que os membros não virtuais, principalmente porque as chamadas para membros virtuais não são embutidas.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="7cf3d-114">✔️ Considere limitar a extensibilidade apenas ao que é absolutamente necessário.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="7cf3d-115">✔️ preferir a acessibilidade protegida sobre acessibilidade pública para membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="7cf3d-116">Os membros públicos devem fornecer extensibilidade (se necessário) chamando um membro virtual protegido.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="7cf3d-117">Os membros públicos de uma classe devem fornecer o conjunto certo de funcionalidade para consumidores diretos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="7cf3d-118">Os membros virtuais são projetados para serem substituídos em subclasses e a acessibilidade protegida é uma ótima maneira de definir o escopo de todos os pontos de extensibilidade virtual para onde eles podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="7cf3d-119">*Partes &copy; 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="7cf3d-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7cf3d-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7cf3d-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7cf3d-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="7cf3d-121">See also</span></span>

- [<span data-ttu-id="7cf3d-122">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="7cf3d-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="7cf3d-123">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="7cf3d-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
