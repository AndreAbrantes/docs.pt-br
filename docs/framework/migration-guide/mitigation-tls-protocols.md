---
title: 'Mitigação: protocolos TLS'
description: Saiba mais sobre o impacto e a mitigação das alterações do protocolo TLS a partir do .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 492315d43043c83d17eab330e8d589d1cffe7ad2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273861"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="e9380-103">Mitigação: protocolos TLS</span><span class="sxs-lookup"><span data-stu-id="e9380-103">Mitigation: TLS Protocols</span></span>

<span data-ttu-id="e9380-104">A partir do .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> têm permissão para usar um dos três protocolos a seguir: Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="e9380-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e9380-105">Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.</span><span class="sxs-lookup"><span data-stu-id="e9380-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e9380-106">Impacto</span><span class="sxs-lookup"><span data-stu-id="e9380-106">Impact</span></span>  

 <span data-ttu-id="e9380-107">Essa alteração afeta:</span><span class="sxs-lookup"><span data-stu-id="e9380-107">This change affects:</span></span>  
  
- <span data-ttu-id="e9380-108">Qualquer aplicativo que usa o SSL para se comunicar com um servidor HTTPS ou um servidor de soquete usando qualquer um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="e9380-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="e9380-109">Qualquer aplicativo do lado do servidor que não possa ser atualizado para dar suporte ao Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="e9380-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e9380-110">Atenuação</span><span class="sxs-lookup"><span data-stu-id="e9380-110">Mitigation</span></span>  

 <span data-ttu-id="e9380-111">A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="e9380-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e9380-112">Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext> poderá ser usada para recusar esse recurso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="e9380-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="e9380-113">De modo programático, usando um snippet de código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e9380-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="e9380-114">Como o objeto <xref:System.Net.ServicePointManager> foi inicializado apenas uma vez, definir essas configurações de compatibilidade deverá ser a primeira coisa que o aplicativo fará.</span><span class="sxs-lookup"><span data-stu-id="e9380-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="e9380-115">Adicionando a seguinte linha à [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de app.config:</span><span class="sxs-lookup"><span data-stu-id="e9380-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="e9380-116">No entanto, observe que não é recomendável recusar o comportamento padrão, pois isso torna o aplicativo menos seguro.</span><span class="sxs-lookup"><span data-stu-id="e9380-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9380-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9380-117">See also</span></span>

- [<span data-ttu-id="e9380-118">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e9380-118">Application compatibility</span></span>](application-compatibility.md)
