---
title: Configurando o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 854cd7d26e26ee340d577b1bfd890f750e581a38
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284141"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="34aa5-102">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="34aa5-102">Configuring the Net.TCP Port Sharing Service</span></span>

<span data-ttu-id="34aa5-103">Os serviços de hospedagem interna que usam o transporte net. TCP podem controlar várias configurações avançadas, como `ListenBacklog` e `MaxPendingAccepts` , que regem o comportamento do soquete TCP subjacente usado para comunicação de rede.</span><span class="sxs-lookup"><span data-stu-id="34aa5-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="34aa5-104">No entanto, essas configurações para cada soquete se aplicam apenas no nível de associação se a associação de transporte tiver desabilitado o compartilhamento de porta, que está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="34aa5-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="34aa5-105">Quando uma associação net. TCP habilita o compartilhamento de porta (por configuração `portSharingEnabled =true` no elemento de associação de transporte), ele permite implicitamente um processo externo (ou seja, o SMSvcHost.exe, que hospeda o serviço de compartilhamento de porta Net. TCP) para gerenciar o soquete TCP em seu nome.</span><span class="sxs-lookup"><span data-stu-id="34aa5-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="34aa5-106">Por exemplo, ao usar TCP, especifique:</span><span class="sxs-lookup"><span data-stu-id="34aa5-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="34aa5-107">Quando configurado dessa forma, todas as configurações de soquete especificadas no elemento de associação de transporte do serviço são ignoradas em favor das configurações de soquete especificadas por SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="34aa5-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="34aa5-108">Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SmSvcHost.exe.config e coloque-o no mesmo diretório físico que o SMSvcHost.exe executável (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="34aa5-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="34aa5-109">O exemplo a seguir ilustra um SMSvcHost.exe.config de exemplo, com as configurações padrão para todos os valores configuráveis declarados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="34aa5-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="34aa5-110">Quando modificar SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="34aa5-110">When to Modify SMSvcHost.exe.config</span></span>  

 <span data-ttu-id="34aa5-111">Em geral, deve-se ter cuidado ao modificar o conteúdo do arquivo de SMSvcHost.exe.config, pois as definições de configuração especificadas nesse arquivo afetam todos os serviços em um computador que usa o serviço de compartilhamento de porta Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="34aa5-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="34aa5-112">Isso inclui aplicativos no Windows Vista que usam os recursos de ativação TCP do WAS (serviço de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="34aa5-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="34aa5-113">No entanto, às vezes, talvez seja necessário alterar a configuração padrão para o serviço de compartilhamento de porta Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="34aa5-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="34aa5-114">Por exemplo, o valor padrão para `maxPendingAccepts` é 4 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="34aa5-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="34aa5-115">Os servidores que hospedam um grande número de serviços que usam o compartilhamento de porta podem aumentar esse valor para obter a taxa de transferência máxima.</span><span class="sxs-lookup"><span data-stu-id="34aa5-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="34aa5-116">O valor padrão para `maxPendingConnections` é 100.</span><span class="sxs-lookup"><span data-stu-id="34aa5-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="34aa5-117">Você deve considerar aumentar esse valor também se houver vários clientes simultâneos chamando o serviço e o serviço estiver removendo conexões de cliente.</span><span class="sxs-lookup"><span data-stu-id="34aa5-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="34aa5-118">SMSvcHost.exe.config também contém informações sobre as identidades de processo que podem fazer uso do serviço de compartilhamento de porta.</span><span class="sxs-lookup"><span data-stu-id="34aa5-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="34aa5-119">Quando um processo se conecta ao serviço de compartilhamento de porta para fazer uso de uma porta TCP compartilhada, a identidade do processo de conexão é verificada em uma lista de identidades que têm permissão para usar o serviço de compartilhamento de porta.</span><span class="sxs-lookup"><span data-stu-id="34aa5-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="34aa5-120">Essas identidades são especificadas como identificadores de segurança (SIDs) na \<allowAccounts> seção do arquivo de SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="34aa5-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="34aa5-121">Por padrão, a permissão para usar o serviço de compartilhamento de porta é concedida a contas de sistema (LocalService, LocalSystem e NetworkService), bem como a membros do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="34aa5-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="34aa5-122">Os aplicativos que permitem que um processo em execução como outra identidade (por exemplo, uma identidade de usuário) se conectem ao serviço de compartilhamento de porta devem adicionar explicitamente o SID apropriado ao SMSvcHost.exe.config (essas alterações não são aplicadas até que o processo de SMSvc.exe seja reiniciado).</span><span class="sxs-lookup"><span data-stu-id="34aa5-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34aa5-123">Em sistemas Windows Vista com UAC (controle de conta de usuário) habilitado, os usuários locais exigem permissões elevadas, mesmo que sua conta seja membro do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="34aa5-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="34aa5-124">Para permitir que esses usuários façam uso do serviço de compartilhamento de porta sem elevação, o SID do usuário (ou o SID de um grupo no qual o usuário é membro) deve ser adicionado explicitamente à \<allowAccounts> seção de SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="34aa5-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="34aa5-125">O arquivo de SMSvcHost.exe.config padrão especifica um personalizado `etwProviderId` para impedir que SMSvcHost.exe rastreamento interfira com rastreamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="34aa5-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34aa5-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="34aa5-126">See also</span></span>

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
