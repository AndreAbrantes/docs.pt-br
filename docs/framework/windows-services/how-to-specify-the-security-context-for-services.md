---
title: Como especificar o contexto de segurança para serviços
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: dd2a9c4485e151d4cb1c9d5ae3a95a69fcc416d4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053590"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Como especificar o contexto de segurança para serviços
Por padrão, os serviços são executados em um contexto de segurança diferente do que o usuário que fez logon. Os serviços são executados no contexto da conta padrão do sistema, chamada `LocalSystem`, que oferece a eles privilégios de acesso a recursos do sistema diferentes que os do usuário. Você pode alterar esse comportamento para especificar outra conta de usuário diferente com a qual o serviço deverá ser executado.  
  
 Você define o contexto de segurança manipulando a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o processo no qual o serviço é executado. Essa propriedade permite que você defina o serviço para uma entre quatro tipos de conta:  
  
- `User`, que faz com que o sistema solicite um nome de usuário e uma senha válidos quando o serviço é instalado e executado no contexto de uma conta especificada por um único usuário na rede;  
  
- `LocalService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta credenciais anônimas para qualquer servidor remoto;  
  
- `LocalSystem`, que é executado no contexto de uma conta que fornece privilégios locais abrangentes e apresenta as credenciais do computador para qualquer servidor remoto;  
  
- `NetworkService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta as credenciais do computador para qualquer servidor remoto.  
  
 Para obter mais informações, consulte a enumeração <xref:System.ServiceProcess.ServiceAccount>.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Para especificar o contexto de segurança de um serviço  
  
1. Depois de criar o serviço, adicione os instaladores necessários para ele. Para obter mais informações, confira [Como adicionar instaladores no seu aplicativo de serviço](how-to-add-installers-to-your-service-application.md).  
  
2. No designer, acesse a classe `ProjectInstaller` e clique no instalador do processo de serviço para o serviço com o qual você está trabalhando.  
  
    > [!NOTE]
    > Para cada aplicativo de serviço, há pelo menos dois componentes de instalação na classe `ProjectInstaller` – um que instala os processos para todos os serviços no projeto e um instalador para cada serviço que o aplicativo contém. Nesse caso, você desejará selecionar <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3. Na janela **Propriedades**, defina a <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o valor apropriado.  
  
## <a name="see-also"></a>Confira também

- [Introdução aos aplicativos de serviço do Windows](introduction-to-windows-service-applications.md)
- [Como adicionar instaladores ao aplicativo de serviço](how-to-add-installers-to-your-service-application.md)
- [Como criar Serviços Windows](how-to-create-windows-services.md)
