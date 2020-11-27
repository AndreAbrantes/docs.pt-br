---
title: Configurando aplicativos da Internet
description: Saiba como usar o elemento <system.Net> para configurar aplicativos de Internet no .NET Framework. Este artigo contém código de exemplo.
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
ms.openlocfilehash: 796752ebf6e3cc5c3dac2a20213934f35d31b392
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287456"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="64f1e-104">Configurando aplicativos da Internet</span><span class="sxs-lookup"><span data-stu-id="64f1e-104">Configuring Internet Applications</span></span>

<span data-ttu-id="64f1e-105">O elemento de configuração do [ \<system.Net> elemento (configurações de rede)](../configure-apps/file-schema/network/system-net-element-network-settings.md) contém informações de configuração de rede para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="64f1e-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="64f1e-106">Usando o elemento [ \<system.Net> (configurações de rede) do elemento](../configure-apps/file-schema/network/system-net-element-network-settings.md) , você pode definir servidores proxy, definir parâmetros de gerenciamento de conexão e incluir autenticação personalizada e módulos de solicitação em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64f1e-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="64f1e-107">O elemento [ \<defaultProxy> (configurações de rede) do elemento](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) define o servidor proxy retornado pela `GlobalProxySelection` classe.</span><span class="sxs-lookup"><span data-stu-id="64f1e-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="64f1e-108">Qualquer <xref:System.Net.HttpWebRequest> que não tenha sua própria propriedade <xref:System.Net.HttpWebRequest.Proxy%2A> definida com um valor específico usa o proxy padrão.</span><span class="sxs-lookup"><span data-stu-id="64f1e-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="64f1e-109">Além de definir o endereço proxy, é possível criar uma lista de endereços de servidor que não usará o proxy e indicar que o proxy não deverá ser usado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="64f1e-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="64f1e-110">É importante observar que as configurações do Microsoft Internet Explorer são combinadas com as configurações, com o último tendo precedência sobre o primeiro.</span><span class="sxs-lookup"><span data-stu-id="64f1e-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="64f1e-111">O exemplo a seguir define o endereço do servidor proxy padrão como `http://proxyserver`, indica que o proxy não deverá ser usado para endereços locais e especifica que todas as solicitações para servidores localizados no domínio contoso.com deverão ignorar o proxy.</span><span class="sxs-lookup"><span data-stu-id="64f1e-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="64f1e-112">Use o elemento [ \<connectionManagement> (configurações de rede)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) para configurar o número de conexões persistentes que podem ser feitas a um servidor específico ou a todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="64f1e-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="64f1e-113">O exemplo a seguir configura o aplicativo para usar duas conexões persistentes com o servidor `www.contoso.com`, quatro conexões persistentes com o servidor com o endereço IP 192.168.1.2 e uma conexão persistente com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="64f1e-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="64f1e-114">Os módulos de autenticação personalizada são configurados com o elemento elemento [ \<authenticationModules> (configurações de rede)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) .</span><span class="sxs-lookup"><span data-stu-id="64f1e-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="64f1e-115">Os módulos de autenticação personalizados devem implementar a interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="64f1e-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="64f1e-116">O exemplo a seguir configura um módulo de autenticação personalizado.</span><span class="sxs-lookup"><span data-stu-id="64f1e-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="64f1e-117">Você pode usar o elemento [ \<webRequestModules> (configurações de rede)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) para configurar seu aplicativo para usar módulos personalizados específicos de protocolo para solicitar informações de recursos da Internet.</span><span class="sxs-lookup"><span data-stu-id="64f1e-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="64f1e-118">Os módulos especificados devem implementar a interface <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="64f1e-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="64f1e-119">É possível substituir os módulos padrão HTTP, HTTPS e de solicitação de arquivo especificando o módulo personalizado no arquivo de configuração, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="64f1e-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64f1e-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="64f1e-120">See also</span></span>

- [<span data-ttu-id="64f1e-121">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="64f1e-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="64f1e-122">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="64f1e-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="64f1e-123">\<system.Net> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="64f1e-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
