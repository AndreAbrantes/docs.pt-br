---
title: Nomes de Assemblies e DLLs
description: Conheça as diretrizes para nomear assemblies e DLLs (bibliotecas de vínculo dinâmico). Um assembly pode abranger um ou mais arquivos, mas geralmente mapeia um para um com uma DLL.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 95a90ff66ffc9f2a5a3202d6877b1cc19149ff35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706522"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="77612-104">Nomes de Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="77612-104">Names of Assemblies and DLLs</span></span>

<span data-ttu-id="77612-105">Um assembly é a unidade de implantação e identidade para programas de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="77612-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="77612-106">Embora assemblies possam abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL.</span><span class="sxs-lookup"><span data-stu-id="77612-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="77612-107">Portanto, esta seção descreve apenas as convenções de nomenclatura de DLL, que podem ser mapeadas para convenções de nomenclatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="77612-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="77612-108">✔️ escolher nomes para suas DLLs de assembly que sugerem grandes partes de funcionalidade, como System. Data.</span><span class="sxs-lookup"><span data-stu-id="77612-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="77612-109">Nomes de assembly e DLL não precisam corresponder a nomes de namespace, mas é razoável seguir o nome do namespace ao nomear assemblies.</span><span class="sxs-lookup"><span data-stu-id="77612-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="77612-110">Uma boa regra prática é nomear a DLL com base no prefixo comum dos namespaces contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="77612-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="77612-111">Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature` , pode ser chamado `MyCompany.MyTechnology.dll` .</span><span class="sxs-lookup"><span data-stu-id="77612-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="77612-112">✔️ Considere nomear DLLs de acordo com o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="77612-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="77612-113">onde `<Component>` contém uma ou mais cláusulas separadas por ponto.</span><span class="sxs-lookup"><span data-stu-id="77612-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="77612-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="77612-114">For example:</span></span>

 <span data-ttu-id="77612-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="77612-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="77612-116">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="77612-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="77612-117">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="77612-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="77612-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="77612-118">See also</span></span>

- [<span data-ttu-id="77612-119">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="77612-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="77612-120">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="77612-120">Naming Guidelines</span></span>](naming-guidelines.md)
