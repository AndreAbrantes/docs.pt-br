---
title: Misturando protocolos confiáveis em cenários federados
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248169"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="60f1a-102">Misturando protocolos confiáveis em cenários federados</span><span class="sxs-lookup"><span data-stu-id="60f1a-102">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="60f1a-103">Pode haver cenários em que os clientes federados se comunicam com um serviço e um serviço de token de segurança (STS) que não têm a mesma versão de confiança.</span><span class="sxs-lookup"><span data-stu-id="60f1a-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="60f1a-104">O serviço WSDL pode conter uma `RequestSecurityTokenTemplate` asserção com WS-Trust elementos que são de versões diferentes do STS.</span><span class="sxs-lookup"><span data-stu-id="60f1a-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="60f1a-105">Nesses casos, um cliente Windows Communication Foundation (WCF) converte os elementos de WS-Trust recebidos do `RequestSecurityTokenTemplate` para corresponder à versão de confiança do STS.</span><span class="sxs-lookup"><span data-stu-id="60f1a-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="60f1a-106">O WCF lida com versões de confiança incompatíveis apenas para associações padrão.</span><span class="sxs-lookup"><span data-stu-id="60f1a-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="60f1a-107">Todos os parâmetros de algoritmo padrão que são reconhecidos pelo WCF fazem parte da associação padrão.</span><span class="sxs-lookup"><span data-stu-id="60f1a-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="60f1a-108">Este tópico descreve o comportamento do WCF com várias configurações de confiança entre o serviço e o STS.</span><span class="sxs-lookup"><span data-stu-id="60f1a-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="60f1a-109">RP fev 2005 e STS fevereiro de 2005</span><span class="sxs-lookup"><span data-stu-id="60f1a-109">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="60f1a-110">O WSDL para a parte confiável (RP) contém os seguintes elementos na `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="60f1a-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="60f1a-111">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="60f1a-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="60f1a-112">O WCF não pode diferenciar os parâmetros de cliente e de serviço; Ele adiciona todos os parâmetros e os envia no `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="60f1a-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="60f1a-113">RP Trust 1,3 e o STS Trust 1,3</span><span class="sxs-lookup"><span data-stu-id="60f1a-113">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="60f1a-114">O WSDL para RP contém os seguintes elementos na `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="60f1a-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="60f1a-115">O arquivo de configuração do cliente contém um `secondaryParameters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="60f1a-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="60f1a-116">O WCF remove `EncryptionAlgorithm` os `CanonicalizationAlgorithm` `KeyWrapAlgorithm` elementos e do elemento de nível superior sob o RST, se eles estiverem presentes dentro do `SecondaryParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="60f1a-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="60f1a-117">O WCF anexa o `SecondaryParameters` elemento ao RST de saída sem modificações.</span><span class="sxs-lookup"><span data-stu-id="60f1a-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="60f1a-118">RP confiável fev 2005 e confiança STS 1,3</span><span class="sxs-lookup"><span data-stu-id="60f1a-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="60f1a-119">O WSDL para RP contém os seguintes elementos na `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="60f1a-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="60f1a-120">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="60f1a-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="60f1a-121">No arquivo de configuração do cliente, o WCF não pode diferenciar os parâmetros do serviço e do cliente.</span><span class="sxs-lookup"><span data-stu-id="60f1a-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="60f1a-122">Portanto, o WCF converte todos os parâmetros em um namespace da versão de confiança 1,3.</span><span class="sxs-lookup"><span data-stu-id="60f1a-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="60f1a-123">O WCF manipula `KeyType` os `KeySize` elementos, e da `TokenType` seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="60f1a-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="60f1a-124">Baixe o WSDL, crie a associação e atribua `KeyType` , `KeySize` e `TokenType` dos parâmetros de RP.</span><span class="sxs-lookup"><span data-stu-id="60f1a-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="60f1a-125">O arquivo de configuração do cliente é gerado.</span><span class="sxs-lookup"><span data-stu-id="60f1a-125">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="60f1a-126">O cliente agora pode alterar qualquer parâmetro no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="60f1a-126">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="60f1a-127">Durante o tempo de execução, o WCF copia todos os parâmetros especificados na `AdditionalTokenParameters` seção do arquivo de configuração do cliente `KeyType` , exceto, `KeySize` e `TokenType` , porque esses parâmetros são contabilizados durante a geração do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="60f1a-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="60f1a-128">RP Trust 1,3 e a confiança STS de fevereiro de 2005</span><span class="sxs-lookup"><span data-stu-id="60f1a-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="60f1a-129">O WSDL para RP contém os seguintes elementos na `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="60f1a-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="60f1a-130">O arquivo de configuração do cliente contém um `secondaryParamters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="60f1a-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="60f1a-131">O WCF copia todos os parâmetros especificados na `SecondaryParameters` seção para o elemento RST de nível superior, mas não os converte para o namespace 2005 WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="60f1a-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
