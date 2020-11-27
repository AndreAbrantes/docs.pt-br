---
title: Configurando serviços WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: a5fe0cabb1a6be7f93bf5f4d753e9bb08a39cea3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253330"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="61bdb-102">Configurando serviços WCF</span><span class="sxs-lookup"><span data-stu-id="61bdb-102">Configuring WCF services</span></span>

<span data-ttu-id="61bdb-103">Depois de criar e implementar seu contrato de serviço, você estará pronto para configurar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="61bdb-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="61bdb-104">É aí que você define e personaliza como o serviço é exposto aos clientes, incluindo a especificação do endereço onde ele pode ser encontrado, o transporte e a codificação de mensagens que ele usa para enviar e receber mensagens e o tipo de segurança que ela exige.</span><span class="sxs-lookup"><span data-stu-id="61bdb-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="61bdb-105">A configuração conforme usada aqui inclui todas as formas, imperativamente no código ou usando um arquivo de configuração, no qual você pode definir e personalizar os vários aspectos de um serviço, como especificar seus endereços de ponto de extremidade, os transportes usados e seus esquemas de segurança.</span><span class="sxs-lookup"><span data-stu-id="61bdb-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="61bdb-106">Na prática, escrever a configuração é uma parte importante da programação de aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="61bdb-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61bdb-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="61bdb-107">In This Section</span></span>  

 [<span data-ttu-id="61bdb-108">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="61bdb-108">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="61bdb-109">A partir do .NET Framework 4, o WCF vem com um novo modelo de configuração padrão que simplifica os requisitos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="61bdb-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="61bdb-110">Se você não fornecer nenhuma configuração do WCF para um serviço específico, o tempo de execução configurará automaticamente seu serviço com pontos de extremidade padrão, associações e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="61bdb-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="61bdb-111">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="61bdb-111">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="61bdb-112">Um serviço do Windows Communication Foundation (WCF) é configurável usando a tecnologia de configuração do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61bdb-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="61bdb-113">Normalmente, os elementos XML são adicionados ao arquivo de Web.config para um site Serviços de Informações da Internet (IIS) que hospeda um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="61bdb-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="61bdb-114">Os elementos permitem que você altere os detalhes, como os endereços de ponto de extremidade (os endereços reais usados para se comunicar com o serviço) em uma base de máquina por máquina.</span><span class="sxs-lookup"><span data-stu-id="61bdb-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="61bdb-115">Associações</span><span class="sxs-lookup"><span data-stu-id="61bdb-115">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="61bdb-116">Além disso, o WCF inclui várias configurações comuns fornecidas pelo sistema na forma de associações que permitem selecionar rapidamente os recursos mais básicos de como um cliente e serviço se comunicam, como os transportes, a segurança e as codificações de mensagens usadas.</span><span class="sxs-lookup"><span data-stu-id="61bdb-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="61bdb-117">Pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="61bdb-117">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="61bdb-118">Toda a comunicação com um serviço WCF ocorre por meio dos *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="61bdb-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="61bdb-119">Os pontos de extremidade contêm o contrato, as informações de configuração especificadas nas associações e os endereços que indicam onde encontrar o serviço ou onde obter informações sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="61bdb-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="61bdb-120">Serviços de segurança</span><span class="sxs-lookup"><span data-stu-id="61bdb-120">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="61bdb-121">Usando o WCF e mecanismos de segurança existentes, você pode implementar confidencialidade, integridade, autenticação e autorização em qualquer serviço.</span><span class="sxs-lookup"><span data-stu-id="61bdb-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="61bdb-122">Você também pode auditar as falhas e êxitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="61bdb-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="61bdb-123">Criando serviços interoperáveis de perfil básico de WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="61bdb-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="61bdb-124">Os requisitos para a implantação de um serviço que é interoperável com serviços e clientes em qualquer outra plataforma ou sistema operacional são descritos na especificação WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="61bdb-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="61bdb-125">Referência</span><span class="sxs-lookup"><span data-stu-id="61bdb-125">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="61bdb-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="61bdb-126">Related Sections</span></span>  

 [<span data-ttu-id="61bdb-127">Ciclo de vida de programação básica</span><span class="sxs-lookup"><span data-stu-id="61bdb-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="61bdb-128">Serviços de implantação e projeção</span><span class="sxs-lookup"><span data-stu-id="61bdb-128">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="61bdb-129">Serviços de hospedagem</span><span class="sxs-lookup"><span data-stu-id="61bdb-129">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="61bdb-130">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="61bdb-130">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="61bdb-131">Introdução à extensibilidade</span><span class="sxs-lookup"><span data-stu-id="61bdb-131">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="61bdb-132">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="61bdb-132">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="61bdb-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="61bdb-133">See also</span></span>

- [<span data-ttu-id="61bdb-134">Programação de WCF básica</span><span class="sxs-lookup"><span data-stu-id="61bdb-134">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="61bdb-135">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="61bdb-135">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="61bdb-136">Detalhes do recurso WCF</span><span class="sxs-lookup"><span data-stu-id="61bdb-136">WCF Feature Details</span></span>](./feature-details/index.md)
