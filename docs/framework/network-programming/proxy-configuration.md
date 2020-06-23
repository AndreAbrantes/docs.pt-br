---
title: Configuração de proxy
description: Saiba mais sobre como configurar servidores proxy adaptáveis e estáticos. A configuração de proxy controla como um servidor proxy trata as solicitações do cliente para recursos.
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 4d62f5736e9aa469be49d101e85851bc01b7c159
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141599"
---
# <a name="proxy-configuration"></a><span data-ttu-id="71f68-104">Configuração de proxy</span><span class="sxs-lookup"><span data-stu-id="71f68-104">Proxy Configuration</span></span>
<span data-ttu-id="71f68-105">Um servidor proxy manipula as solicitações de clientes para recursos.</span><span class="sxs-lookup"><span data-stu-id="71f68-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="71f68-106">Um proxy pode retornar um recurso solicitado do seu cache ou encaminhar a solicitação para o servidor na qual o recurso reside.</span><span class="sxs-lookup"><span data-stu-id="71f68-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="71f68-107">Proxies podem melhorar o desempenho da rede, reduzindo o número de solicitações enviadas a servidores remotos.</span><span class="sxs-lookup"><span data-stu-id="71f68-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="71f68-108">Proxies também podem ser usados para restringir o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="71f68-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="71f68-109">Proxies adaptáveis</span><span class="sxs-lookup"><span data-stu-id="71f68-109">Adaptive Proxies</span></span>  
 <span data-ttu-id="71f68-110">No .NET Framework, os proxies existem em duas variedades: adaptáveis e estáticos.</span><span class="sxs-lookup"><span data-stu-id="71f68-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="71f68-111">Proxies adaptáveis ajustam suas configurações quando as configurações de rede são alteradas.</span><span class="sxs-lookup"><span data-stu-id="71f68-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="71f68-112">Por exemplo, se um usuário de laptop inicia uma conexão de rede dial-up, um proxy adaptável reconheceria essa alteração, descobrir e executaria seu novo script de configuração e ajustaria suas configurações adequadamente.</span><span class="sxs-lookup"><span data-stu-id="71f68-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="71f68-113">Proxies adaptáveis são configurados por um script de configuração (consulte [Detecção automática de proxy](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="71f68-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="71f68-114">O script gera um conjunto de protocolos de aplicativo e um proxy para cada protocolo.</span><span class="sxs-lookup"><span data-stu-id="71f68-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="71f68-115">Alterações no ambiente de rede podem exigir que o sistema use um novo conjunto de proxies.</span><span class="sxs-lookup"><span data-stu-id="71f68-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="71f68-116">Se uma conexão de rede ficar inoperante ou uma nova conexão de rede for inicializada, o sistema deve descobrir a origem correta do script de configuração no novo ambiente e executar o novo script.</span><span class="sxs-lookup"><span data-stu-id="71f68-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="71f68-117">Você pode usar o `usesystemdefault` atributo do [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) elemento em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="71f68-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="71f68-118">O atributo `usesystemdefault` controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lidas das configurações de proxy do Internet Explorer para o usuário.</span><span class="sxs-lookup"><span data-stu-id="71f68-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="71f68-119">Se esse valor for definido como `true`, as configurações de proxy estático do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="71f68-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="71f68-120">Se esse valor for `false` ou não estiver definido, as configurações de proxy estático poderão ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="71f68-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="71f68-121">Esse valor também deve ser definido como `false` ou não estar definido para que proxies adaptáveis sejam habilitados.</span><span class="sxs-lookup"><span data-stu-id="71f68-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="71f68-122">O exemplo a seguir mostra uma configuração de proxy adaptável típica.</span><span class="sxs-lookup"><span data-stu-id="71f68-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="71f68-123">Proxies estáticos</span><span class="sxs-lookup"><span data-stu-id="71f68-123">Static Proxies</span></span>  
 <span data-ttu-id="71f68-124">Proxies estáticos geralmente são configurados explicitamente por um aplicativo ou quando um arquivo de configuração é invocado por um aplicativo ou pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="71f68-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="71f68-125">Proxies estáticos são úteis em redes em que a topologia é alterada com frequência, como um computador desktop conectado a uma rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="71f68-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="71f68-126">Várias opções de controlam como um proxy estático funciona.</span><span class="sxs-lookup"><span data-stu-id="71f68-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="71f68-127">Você pode especificar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="71f68-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="71f68-128">O endereço do proxy.</span><span class="sxs-lookup"><span data-stu-id="71f68-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="71f68-129">Se o proxy deve ou não ser ignorado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="71f68-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="71f68-130">Se o proxy deve ou não ser ignorado para um conjunto de endereços.</span><span class="sxs-lookup"><span data-stu-id="71f68-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="71f68-131">A tabela a seguir mostra as opções de configuração para um proxy estático.</span><span class="sxs-lookup"><span data-stu-id="71f68-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="71f68-132">Definição do arquivo de configuração, propriedade ou atributo</span><span class="sxs-lookup"><span data-stu-id="71f68-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="71f68-133">Description</span><span class="sxs-lookup"><span data-stu-id="71f68-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="71f68-134">`proxyaddress` ou <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="71f68-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="71f68-135">O endereço do proxy a ser usado.</span><span class="sxs-lookup"><span data-stu-id="71f68-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="71f68-136">`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="71f68-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="71f68-137">Controla se o proxy é ignorado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="71f68-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="71f68-138">`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="71f68-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="71f68-139">Descreve, com expressões regulares, um conjunto de endereços que ignora o proxy.</span><span class="sxs-lookup"><span data-stu-id="71f68-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="71f68-140">Controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lido das configurações de proxy do Internet Explorer para o usuário.</span><span class="sxs-lookup"><span data-stu-id="71f68-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="71f68-141">Se esse valor for definido como `true`, então as configurações de proxy estático do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="71f68-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="71f68-142">No .NET Framework 2.0, quando esse valor é definido como `true`, as configurações de proxy do Internet Explorer não são substituídas por outras configurações de proxy no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="71f68-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="71f68-143">No .NET Framework 1.1, as configurações de proxy do Internet Explorer podem ser substituídas por outras configurações de proxy no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="71f68-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="71f68-144">Se esse valor for `false` ou não estiver definido, então as configurações de proxy estático poderão ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="71f68-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="71f68-145">Esse valor também deve ser definido como `false` ou não estar definido para que proxies adaptáveis sejam habilitados.</span><span class="sxs-lookup"><span data-stu-id="71f68-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="71f68-146">O exemplo a seguir mostra uma configuração de proxy estático típica.</span><span class="sxs-lookup"><span data-stu-id="71f68-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71f68-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="71f68-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="71f68-148">Detecção automática de proxy</span><span class="sxs-lookup"><span data-stu-id="71f68-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
