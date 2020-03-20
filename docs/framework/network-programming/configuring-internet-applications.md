---
title: Configurando aplicativos da Internet
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048626"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="48889-102">Configurando aplicativos da Internet</span><span class="sxs-lookup"><span data-stu-id="48889-102">Configuring Internet Applications</span></span>
<span data-ttu-id="48889-103">O elemento de configuração [ \<system.Net> Element (Configurações de rede)](../configure-apps/file-schema/network/system-net-element-network-settings.md) contém informações de configuração de rede para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="48889-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="48889-104">Usando o [ \<elemento system.Net> Element (Configurações de rede),](../configure-apps/file-schema/network/system-net-element-network-settings.md) você pode definir servidores proxy, definir parâmetros de gerenciamento de conexão e incluir módulos de autenticação e solicitação personalizados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48889-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="48889-105">O [ \<elemento padrãoDo elemento> proxy (Configurações de rede)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) define o servidor proxy retornado pela `GlobalProxySelection` classe.</span><span class="sxs-lookup"><span data-stu-id="48889-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="48889-106">Qualquer <xref:System.Net.HttpWebRequest> que não tenha sua própria propriedade <xref:System.Net.HttpWebRequest.Proxy%2A> definida com um valor específico usa o proxy padrão.</span><span class="sxs-lookup"><span data-stu-id="48889-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="48889-107">Além de definir o endereço proxy, é possível criar uma lista de endereços de servidor que não usará o proxy e indicar que o proxy não deverá ser usado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="48889-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="48889-108">É importante observar que as configurações do Microsoft Internet Explorer são combinadas com as configurações, com o último tendo precedência sobre o primeiro.</span><span class="sxs-lookup"><span data-stu-id="48889-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="48889-109">O exemplo a seguir define o endereço do servidor proxy padrão como `http://proxyserver`, indica que o proxy não deverá ser usado para endereços locais e especifica que todas as solicitações para servidores localizados no domínio contoso.com deverão ignorar o proxy.</span><span class="sxs-lookup"><span data-stu-id="48889-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="48889-110">Use o [ \<elemento connectionManagement> Element (Configurações de rede)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) para configurar o número de conexões persistentes que podem ser feitas a um servidor específico ou a todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="48889-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="48889-111">O exemplo a seguir configura o aplicativo para usar duas conexões persistentes com o servidor `www.contoso.com`, quatro conexões persistentes com o servidor com o endereço IP 192.168.1.2 e uma conexão persistente com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="48889-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="48889-112">Os módulos de autenticação personalizados são configurados com o [ \<elemento AuthenticationModules> Element (Configurações de rede).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="48889-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="48889-113">Os módulos de autenticação personalizados devem implementar a interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="48889-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="48889-114">O exemplo a seguir configura um módulo de autenticação personalizado.</span><span class="sxs-lookup"><span data-stu-id="48889-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="48889-115">Você pode usar o [ \<elemento webRequestModules> Element (Configurações de rede)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) para configurar seu aplicativo para usar módulos específicos de protocolo personalizados para solicitar informações de recursos da Internet.</span><span class="sxs-lookup"><span data-stu-id="48889-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="48889-116">Os módulos especificados devem implementar a interface <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="48889-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="48889-117">É possível substituir os módulos padrão HTTP, HTTPS e de solicitação de arquivo especificando o módulo personalizado no arquivo de configuração, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="48889-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48889-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="48889-118">See also</span></span>

- [<span data-ttu-id="48889-119">Programação de rede no Framework .NET</span><span class="sxs-lookup"><span data-stu-id="48889-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="48889-120">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="48889-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="48889-121">\<system.Net elemento> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="48889-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
