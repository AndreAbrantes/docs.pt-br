---
title: Posicionamento dos assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119967"
---
# <a name="assembly-placement"></a>Posicionamento dos assemblies
Para a maioria dos aplicativos .NET Framework, você localiza assemblies que compõem um aplicativo no diretório do aplicativo, em um subdiretório do diretório do aplicativo ou no cache de assembly global (se o assembly for compartilhado). Você pode substituir onde o Common Language Runtime procura um assembly usando o [ \<elemento codebase>](../configure-apps/file-schema/runtime/codebase-element.md) em um arquivo de configuração. Se o assembly não tiver um nome forte, o local especificado usando o [ \<elemento> codebase](../configure-apps/file-schema/runtime/codebase-element.md) será restrito ao diretório do aplicativo ou a um subdiretório. Se o assembly tiver um nome forte, o [ \<elemento> codebase](../configure-apps/file-schema/runtime/codebase-element.md) poderá especificar qualquer local no computador ou em uma rede.  
  
 Regras similares se aplicam à localização de assemblies durante o trabalho com código não gerenciado ou aplicativos interop COM: se o assembly for compartilhado por vários aplicativos, ele deverá ser instalado no cache de assembly global. Assemblies usados com códigos não gerenciados devem ser exportados como uma biblioteca de tipos e registrados. Assemblies usados pelo interop COM devem ser registrados no catálogo, embora em alguns casos, esse registro ocorra automaticamente.  
  
## <a name="see-also"></a>Confira também

- [Como o runtime localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos](../configure-apps/index.md)
- [Interoperação com código não gerenciado](../interop/index.md)
- [Assemblies no .NET](index.md)
