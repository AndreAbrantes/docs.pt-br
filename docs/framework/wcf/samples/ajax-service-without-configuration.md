---
title: Serviço AJAX sem configuração
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: ab3731ab6aeb80e0e46228b8bf702b0fe5c6e6e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575895"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="fa7a1-102">Serviço AJAX sem configuração</span><span class="sxs-lookup"><span data-stu-id="fa7a1-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="fa7a1-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de JavaScript e XML (AJAX) ASP.NET assíncrono (um serviço que você pode acessar usando o código JavaScript de um cliente de navegador da Web) sem usar nenhuma definição de configuração.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="fa7a1-104">O serviço usa uma sintaxe especial no arquivo. svc para habilitar automaticamente um ponto de extremidade AJAX.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="fa7a1-105">O suporte ao AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio do `ScriptManager` controle.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="fa7a1-106">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="fa7a1-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fa7a1-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="fa7a1-108">Este exemplo baseia-se no serviço AJAX usando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="fa7a1-109">Conforme descrito no exemplo [básico de serviço AJAX](basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-109">As described in the [Basic AJAX Service](basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="fa7a1-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> ao serviço.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="fa7a1-111">Se nenhuma alteração de configuração precisar ser feita no ponto de extremidade, a `<system.ServiceModel>` seção poderá ser completamente removida do arquivo Web. config para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="fa7a1-112">O arquivo Web. config contém algumas configurações de ASP.NET, que são usadas pelo ConfigFreeClientPage. aspx.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="fa7a1-113">Se esse não for o caso, todo o arquivo Web. config poderá ser removido.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa7a1-114">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fa7a1-115">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fa7a1-116">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa7a1-117">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fa7a1-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="fa7a1-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fa7a1-119">Certifique-se de executar as instruções de instalação no [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fa7a1-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="fa7a1-120">Crie a solução ConfigFreeAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fa7a1-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="fa7a1-121">Navegue até `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (não abra ConfigFreeClientPage. aspx no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="fa7a1-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="fa7a1-122">Ao executar este exemplo, verifique se a autenticação anônima e a autenticação do Windows não estão habilitadas simultaneamente para a pasta ServiceModelSamples no IIS.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="fa7a1-123">Se esse for o caso, desabilite a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa7a1-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="fa7a1-124">Depois de executar o exemplo, habilite a autenticação do Windows e execute "iisreset".</span><span class="sxs-lookup"><span data-stu-id="fa7a1-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="fa7a1-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa7a1-125">See also</span></span>

- [<span data-ttu-id="fa7a1-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="fa7a1-126">Basic AJAX Service</span></span>](basic-ajax-service.md)
