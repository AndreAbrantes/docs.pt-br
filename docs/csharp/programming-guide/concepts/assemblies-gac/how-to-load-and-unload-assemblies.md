---
title: Como carregar e descarregar assemblies (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 8efd5a9ccfedbea401b0c95d443fe8cdb6ea6c32
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a>Como carregar e descarregar assemblies (C#)
Os assemblies referenciados pelo seu programa serão automaticamente carregados e tempo de build, mas também é possível carregar assemblies específicos no domínio do aplicativo atual em tempo de execução. Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados.  
  
 Se você quiser descarregar alguns assemblies, mas não outros, considere criar um novo domínio do aplicativo, executando o código dentro desse domínio e descarregando esse domínio do aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos de carga contidos nas classes <xref:System.AppDomain> e <xref:System.Reflection>. Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Para descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Use o método `Unload` de <xref:System.AppDomain> para descarregar os domínios de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
