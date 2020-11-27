---
title: WebContentTypeMapper Sample
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 550e763d30a7fa503f6500dcaa8f9b77ea499bca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283257"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="a1540-102">WebContentTypeMapper Sample</span><span class="sxs-lookup"><span data-stu-id="a1540-102">WebContentTypeMapper Sample</span></span>

<span data-ttu-id="a1540-103">Este exemplo demonstra como mapear novos tipos de conteúdo para Windows Communication Foundation (WCF) formatos de corpo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a1540-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="a1540-104">O <xref:System.ServiceModel.Description.WebHttpEndpoint> elemento conecta o codificador de mensagem da Web, que permite que o WCF receba mensagens binárias JSON, XML ou RAW no mesmo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a1540-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="a1540-105">O codificador determina o formato do corpo da mensagem observando o tipo de conteúdo HTTP da solicitação.</span><span class="sxs-lookup"><span data-stu-id="a1540-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="a1540-106">Este exemplo apresenta a <xref:System.ServiceModel.Channels.WebContentTypeMapper> classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.</span><span class="sxs-lookup"><span data-stu-id="a1540-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="a1540-107">O WCF fornece um conjunto de mapeamentos padrão para tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a1540-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="a1540-108">Por exemplo, `application/json` mapeia para JSON e `text/xml` MAPEIA para XML.</span><span class="sxs-lookup"><span data-stu-id="a1540-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="a1540-109">Qualquer tipo de conteúdo que não esteja mapeado para JSON ou XML é mapeado para o formato binário bruto.</span><span class="sxs-lookup"><span data-stu-id="a1540-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="a1540-110">Em alguns cenários (por exemplo, APIs de estilo push), o desenvolvedor do serviço não controla o tipo de conteúdo retornado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a1540-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="a1540-111">Por exemplo, os clientes podem retornar JSON como `text/javascript` em vez de `application/json` .</span><span class="sxs-lookup"><span data-stu-id="a1540-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="a1540-112">Nesse caso, o desenvolvedor do serviço deve fornecer um tipo derivado de <xref:System.ServiceModel.Channels.WebContentTypeMapper> para tratar o tipo de conteúdo fornecido corretamente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a1540-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a1540-113">O tipo deve substituir o <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> método.</span><span class="sxs-lookup"><span data-stu-id="a1540-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="a1540-114">O método deve avaliar o `contentType` argumento e retornar um dos seguintes valores: <xref:System.ServiceModel.Channels.WebContentFormat.Json> , <xref:System.ServiceModel.Channels.WebContentFormat.Xml> , <xref:System.ServiceModel.Channels.WebContentFormat.Raw> ou <xref:System.ServiceModel.Channels.WebContentFormat.Default> .</span><span class="sxs-lookup"><span data-stu-id="a1540-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="a1540-115">Retornando <xref:System.ServiceModel.Channels.WebContentFormat.Default> adiamentos para os mapeamentos de codificador de mensagem da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="a1540-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="a1540-116">No código de exemplo anterior, o `text/javascript` tipo de conteúdo é mapeado para JSON e todos os outros mapeamentos permanecem inalterados.</span><span class="sxs-lookup"><span data-stu-id="a1540-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="a1540-117">Para usar a `JsonContentTypeMapper` classe, use o seguinte no seu Web.config:</span><span class="sxs-lookup"><span data-stu-id="a1540-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a1540-118">Para verificar o requisito para usar o JsonContentTypeMapper, remova o atributo contentTypeMapper do arquivo de configuração acima.</span><span class="sxs-lookup"><span data-stu-id="a1540-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="a1540-119">Falha ao carregar a página do cliente ao tentar usar o `text/javascript` para enviar conteúdo JSON.</span><span class="sxs-lookup"><span data-stu-id="a1540-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1540-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a1540-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a1540-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1540-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a1540-122">Crie a solução WebContentTypeMapperSample. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1540-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a1540-123">Navegue até `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (não abra JCTMClientPage.htm no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="a1540-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1540-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a1540-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1540-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a1540-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a1540-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a1540-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1540-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a1540-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
