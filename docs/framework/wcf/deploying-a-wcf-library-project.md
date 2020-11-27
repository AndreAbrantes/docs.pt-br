---
title: Implantando um projeto de biblioteca do WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: e3a90f03639a888b4528a1962a24b7adc5d43c58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260884"
---
# <a name="deploying-a-wcf-library-project"></a>Implantando um projeto de biblioteca do WCF

Este tópico descreve como você pode implantar um projeto de biblioteca de serviços do Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Implantando uma biblioteca de serviços WCF  

 Uma biblioteca de serviços WCF é uma DLL (biblioteca de vínculo dinâmico). Como tal, ele não pode ser executado por conta própria. Ele precisa ser implantado em um ambiente de hospedagem. Para obter mais informações sobre esse processo, consulte [hospedando e consumindo serviços WCF](/previous-versions/dotnet/articles/bb332338(v=msdn.10)).  
  
 Uma biblioteca de serviços WCF pode ser implantada como qualquer outro serviço WCF. No entanto, esteja ciente de que .NET Framework não oferece suporte à configuração para DLLs. <xref:System.Configuration> dá suporte a um arquivo de configuração por domínio. O projeto da biblioteca de serviços WCF alivia essa limitação fornecendo um arquivo App.config para a biblioteca durante o desenvolvimento. No entanto, o arquivo de App.config não é reconhecido após a implantação.  
  
 Você precisa mover o código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem. Para hospedagem interna, você deve copiar o conteúdo do arquivo de App.config para o arquivo de App.config do executável de hospedagem. Se você usar o IIS para hospedar seu serviço, deverá copiar o conteúdo do arquivo de App.config para o arquivo de Web.config do diretório virtual.
