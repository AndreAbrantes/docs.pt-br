---
title: "Assemblies e execução lado a lado | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3b78c82937c78286302adef532c451c24987da39
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="assemblies-and-side-by-side-execution"></a>Assemblies e execução lado a lado
Execução lado a lado é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador. Isso significa que você pode ter várias versões do tempo de execução e várias versões de aplicativos e componentes que usam uma versão do tempo de execução no mesmo computador ao mesmo tempo. A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do tempo de execução um aplicativo usa.  
  
 O suporte para armazenamento lado a lado e execução de diferentes versões do mesmo assembly é uma parte integrante da nomenclatura forte e está integrada à infraestrutura do tempo de execução. Como o número de versão do assembly de nome forte faz parte de sua identidade, o tempo de execução pode armazenar várias versões do mesmo assembly no cache de assembly global e carregar esses módulos em tempo de execução.  
  
 Embora o tempo de execução ofereça a capacidade de criar aplicativos lado a lado, a execução lado a lado não é automática. Para saber mais sobre a criação de aplicativos para execução lado a lado, confira [Diretrizes para criação de componentes para execução lado a lado](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
