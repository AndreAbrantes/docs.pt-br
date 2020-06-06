---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855140"
---
# \<serviceActivations>

<span data-ttu-id="693fb-101">Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="693fb-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="693fb-102">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="693fb-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="693fb-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="693fb-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="693fb-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="693fb-104">Attributes and Elements</span></span>

<span data-ttu-id="693fb-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="693fb-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="693fb-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="693fb-106">Attributes</span></span>

<span data-ttu-id="693fb-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="693fb-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="693fb-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="693fb-108">Child Elements</span></span>

|<span data-ttu-id="693fb-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="693fb-109">Element</span></span>|<span data-ttu-id="693fb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="693fb-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="693fb-111">Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="693fb-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="693fb-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="693fb-112">Parent Elements</span></span>

|<span data-ttu-id="693fb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="693fb-113">Element</span></span>|<span data-ttu-id="693fb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="693fb-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="693fb-115">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="693fb-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="693fb-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="693fb-116">Remarks</span></span>

<span data-ttu-id="693fb-117">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="693fb-117">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="693fb-118">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="693fb-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="693fb-119">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="693fb-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="693fb-120">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="693fb-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="693fb-121">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="693fb-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="693fb-122">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="693fb-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="693fb-123">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="693fb-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="693fb-124">Ele requer extensões em relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="693fb-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="693fb-125">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="693fb-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="693fb-126">Após o conflito, a `<serviceActivations>` seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="693fb-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="693fb-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="693fb-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
