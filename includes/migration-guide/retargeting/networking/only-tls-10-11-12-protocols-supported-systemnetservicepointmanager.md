---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615595"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="5536e-101">Somente os protocolos Tls 1.0, 1.1 e 1.2 são compatíveis com System.Net.ServicePointManager e System.Net.Security.SslStream</span><span class="sxs-lookup"><span data-stu-id="5536e-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="5536e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5536e-102">Details</span></span>

<span data-ttu-id="5536e-103">A partir do .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager> e <xref:System.Net.Security.SslStream> têm permissão para usar somente um dos três protocolos a seguir: Tls1.0, Tls1.1 ou Tls1.2.</span><span class="sxs-lookup"><span data-stu-id="5536e-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="5536e-104">Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.</span><span class="sxs-lookup"><span data-stu-id="5536e-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5536e-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5536e-105">Suggestion</span></span>

<span data-ttu-id="5536e-106">A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls1.2.</span><span class="sxs-lookup"><span data-stu-id="5536e-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="5536e-107">Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext?displayProperty=fullName> poderá ser usada para recusar esse recurso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="5536e-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="5536e-108">Configurar de forma programática as opções de compatibilidade na instância <xref:System.AppContext?displayProperty=fullName>, conforme explicado [aqui](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="5536e-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="5536e-109">Adicionando a seguinte linha na seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="5536e-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="5536e-110">Name</span><span class="sxs-lookup"><span data-stu-id="5536e-110">Name</span></span>    | <span data-ttu-id="5536e-111">Valor</span><span class="sxs-lookup"><span data-stu-id="5536e-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5536e-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="5536e-112">Scope</span></span>   | <span data-ttu-id="5536e-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="5536e-113">Minor</span></span>       |
| <span data-ttu-id="5536e-114">Versão</span><span class="sxs-lookup"><span data-stu-id="5536e-114">Version</span></span> | <span data-ttu-id="5536e-115">4.6</span><span class="sxs-lookup"><span data-stu-id="5536e-115">4.6</span></span>         |
| <span data-ttu-id="5536e-116">Type</span><span class="sxs-lookup"><span data-stu-id="5536e-116">Type</span></span>    | <span data-ttu-id="5536e-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="5536e-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5536e-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5536e-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
