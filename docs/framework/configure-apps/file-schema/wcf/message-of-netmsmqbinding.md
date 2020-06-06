---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736752"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="c83ce-102">\<message> de \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="c83ce-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="c83ce-103">Define as configurações de segurança da mensagem SOAP nesta `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="c83ce-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="c83ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c83ce-104">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c83ce-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c83ce-105">Attributes and Elements</span></span>

<span data-ttu-id="c83ce-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c83ce-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c83ce-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c83ce-107">Attributes</span></span>

|<span data-ttu-id="c83ce-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c83ce-108">Attribute</span></span>|<span data-ttu-id="c83ce-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c83ce-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c83ce-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c83ce-110">algorithmSuite</span></span>|<span data-ttu-id="c83ce-111">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves que são usados para obter segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c83ce-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="c83ce-112">O valor padrão é `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="c83ce-112">The default value is `Aes256`.</span></span> <span data-ttu-id="c83ce-113">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="c83ce-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="c83ce-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="c83ce-114">clientCredentialType</span></span>|<span data-ttu-id="c83ce-115">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c83ce-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="c83ce-116">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="c83ce-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c83ce-117">-Nenhum: isso permite que o serviço interaja com clientes anônimos.</span><span class="sxs-lookup"><span data-stu-id="c83ce-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="c83ce-118">Nem o serviço nem o cliente exigem uma credencial.</span><span class="sxs-lookup"><span data-stu-id="c83ce-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="c83ce-119">-Windows: isso permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="c83ce-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="c83ce-120">Isso sempre executa a autenticação baseada em Kerberos.</span><span class="sxs-lookup"><span data-stu-id="c83ce-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="c83ce-121">-UserName: isso permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c83ce-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="c83ce-122">A credencial, nesse caso, precisa ser especificada usando o `clientCredentials` comportamento **cuidado:** Windows Communication Foundation (WCF) não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando senha e usando essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c83ce-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="c83ce-123">Portanto, o WCF impõe que a troca seja protegida ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c83ce-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="c83ce-124">Esse modo requer que o certificado de serviço seja especificado no lado do cliente usando o `clientCredential` comportamento e `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="c83ce-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="c83ce-125">-Certificate: isso permite que o serviço exija que o cliente seja autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="c83ce-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="c83ce-126">Nesse caso, a credencial do cliente precisa ser especificada usando o `clientCredentials` comportamento.</span><span class="sxs-lookup"><span data-stu-id="c83ce-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="c83ce-127">Nesse caso, a credencial de serviço precisa ser especificada usando o `clientCredentials` comportamento, especificando o `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="c83ce-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="c83ce-128">-CardSpace: isso permite que o serviço exija que o cliente seja autenticado usando um CardSpace.</span><span class="sxs-lookup"><span data-stu-id="c83ce-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="c83ce-129">O `serviceCertificate` deve ser provisionado no `clientCredential` comportamento.</span><span class="sxs-lookup"><span data-stu-id="c83ce-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="c83ce-130">O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="c83ce-130">The default value is `Windows`.</span></span> <span data-ttu-id="c83ce-131">Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="c83ce-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c83ce-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c83ce-132">Child Elements</span></span>

<span data-ttu-id="c83ce-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c83ce-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c83ce-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c83ce-134">Parent Elements</span></span>

|<span data-ttu-id="c83ce-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="c83ce-135">Element</span></span>|<span data-ttu-id="c83ce-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="c83ce-136">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="c83ce-137">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="c83ce-137">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c83ce-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="c83ce-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="c83ce-139">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="c83ce-139">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="c83ce-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c83ce-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c83ce-141">Associações</span><span class="sxs-lookup"><span data-stu-id="c83ce-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c83ce-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c83ce-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c83ce-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c83ce-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
