---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855233"
---
# \<metadata>
<span data-ttu-id="301fb-101">Especifica como os metadados de serviço podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="301fb-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="301fb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="301fb-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="301fb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="301fb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="301fb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="301fb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="301fb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="301fb-105">Attributes</span></span>  
 <span data-ttu-id="301fb-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="301fb-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="301fb-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="301fb-107">Child Elements</span></span>  
  
|<span data-ttu-id="301fb-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="301fb-108">Element</span></span>|<span data-ttu-id="301fb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="301fb-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="301fb-110">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="301fb-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="301fb-111">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="301fb-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="301fb-112">Especifica todos os importadores WSDL que importam metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="301fb-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="301fb-113">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="301fb-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="301fb-114">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="301fb-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="301fb-115">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="301fb-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="301fb-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="301fb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="301fb-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="301fb-117">Element</span></span>|<span data-ttu-id="301fb-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="301fb-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="301fb-119">A seção cliente define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="301fb-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="301fb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="301fb-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="301fb-121">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="301fb-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="301fb-122">Clientes</span><span class="sxs-lookup"><span data-stu-id="301fb-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
