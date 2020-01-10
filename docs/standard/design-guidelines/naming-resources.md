---
title: Recursos de nomenclatura
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709160"
---
# <a name="naming-resources"></a><span data-ttu-id="55de4-102">Recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="55de4-102">Naming Resources</span></span>
<span data-ttu-id="55de4-103">Como os recursos localizáveis podem ser referenciados por meio de determinados objetos como se fossem Propriedades, as diretrizes de nomenclatura para recursos são semelhantes às diretrizes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="55de4-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="55de4-104">**✓ DO** usar PascalCasing em chaves de recurso.</span><span class="sxs-lookup"><span data-stu-id="55de4-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="55de4-105">**✓ DO** fornecer descritivo em vez de identificadores curtos.</span><span class="sxs-lookup"><span data-stu-id="55de4-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="55de4-106">**X DO NOT** usar palavras-chave das linguagens CLR principais.</span><span class="sxs-lookup"><span data-stu-id="55de4-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="55de4-107">**✓ DO** use somente caracteres alfanuméricos e sublinhados em nomes de recursos.</span><span class="sxs-lookup"><span data-stu-id="55de4-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="55de4-108">**✓ DO** usam a seguinte convenção de nomenclatura para os recursos de mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="55de4-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="55de4-109">O identificador de recurso deve ser o nome do tipo de exceção, além de um identificador curto da exceção:</span><span class="sxs-lookup"><span data-stu-id="55de4-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="55de4-110">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="55de4-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="55de4-111">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="55de4-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55de4-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="55de4-112">See also</span></span>

- [<span data-ttu-id="55de4-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="55de4-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="55de4-114">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="55de4-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
