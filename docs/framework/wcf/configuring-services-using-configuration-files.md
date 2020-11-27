---
title: Configurando serviços usando arquivos de configuração
description: Saiba como um arquivo de configuração para um serviço WCF oferece a flexibilidade de fornecer dados de comportamento de ponto de extremidade e serviço durante a implantação.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 25a6891564054878e7bdf7f43d431547ea1dee6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253343"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="49c1a-103">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="49c1a-103">Configuring Services Using Configuration Files</span></span>

<span data-ttu-id="49c1a-104">Configurar um serviço de Windows Communication Foundation (WCF) com um arquivo de configuração oferece a flexibilidade de fornecer dados de comportamento de ponto de extremidade e serviço no ponto de implantação, em vez de em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="49c1a-104">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="49c1a-105">Este tópico descreve as principais técnicas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="49c1a-105">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="49c1a-106">Um serviço WCF é configurável usando a tecnologia de configuração .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49c1a-106">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="49c1a-107">Normalmente, os elementos XML são adicionados ao arquivo de Web.config para um site Serviços de Informações da Internet (IIS) que hospeda um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="49c1a-107">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="49c1a-108">Os elementos permitem que você altere detalhes, como os endereços de ponto de extremidade (endereços reais usados para comunicação com o serviço) de cada computador.</span><span class="sxs-lookup"><span data-stu-id="49c1a-108">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="49c1a-109">Além disso, o WCF inclui vários elementos fornecidos pelo sistema que permitem que você selecione rapidamente os recursos mais básicos para um serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-109">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="49c1a-110">A partir do .NET Framework 4, o WCF vem com um novo modelo de configuração padrão que simplifica os requisitos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="49c1a-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="49c1a-111">Se você não fornecer nenhuma configuração WCF para um serviço específico, o tempo de execução configurará automaticamente seu serviço com alguns pontos de extremidade padrão e Associação/comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="49c1a-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="49c1a-112">Na prática, escrever a configuração é uma parte importante da programação de aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="49c1a-112">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="49c1a-113">Para obter mais informações, consulte [Configurando associações para serviços](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="49c1a-113">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="49c1a-114">Para obter uma lista dos elementos usados com mais frequência, consulte [associações fornecidas pelo sistema](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="49c1a-114">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="49c1a-115">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="49c1a-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="49c1a-116">Ao implantar os cenários lado a lado onde duas versões diferentes de um serviço são implantadas, é necessário especificar nomes parciais de assemblies referenciados em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="49c1a-116">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="49c1a-117">Isso ocorre porque o arquivo de configuração é compartilhado entre todas as versões de um serviço e pode estar em execução em versões diferentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49c1a-117">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="49c1a-118">System.Configuration: Web.config e App.config</span><span class="sxs-lookup"><span data-stu-id="49c1a-118">System.Configuration: Web.config and App.config</span></span>  

 <span data-ttu-id="49c1a-119">O WCF usa o sistema de configuração System.Configuração do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49c1a-119">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="49c1a-120">Ao configurar um serviço no Visual Studio, use um arquivo de Web.config ou um arquivo de App.config para especificar as configurações.</span><span class="sxs-lookup"><span data-stu-id="49c1a-120">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="49c1a-121">A escolha do nome do arquivo de configuração é determinada pelo ambiente de hospedagem que você escolhe para o serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-121">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="49c1a-122">Se você estiver usando o IIS para hospedar o serviço, use um arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-122">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="49c1a-123">Se você estiver usando qualquer outro ambiente de hospedagem, use um arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-123">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="49c1a-124">No Visual Studio, o arquivo chamado App.config é usado para criar o arquivo de configuração final.</span><span class="sxs-lookup"><span data-stu-id="49c1a-124">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="49c1a-125">O nome final realmente usado para a configuração depende do nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="49c1a-125">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="49c1a-126">Por exemplo, um assembly denominado "Cohowinery.exe" tem um nome de arquivo de configuração final de "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="49c1a-126">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="49c1a-127">Entretanto, você precisa modificar somente o arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-127">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="49c1a-128">As alterações feitas nesse arquivo são automaticamente feitas no arquivo de configuração final do aplicativo em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="49c1a-128">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="49c1a-129">Ao usar um arquivo App.config, o sistema de configuração mescla o arquivo App.config com o conteúdo do arquivo Machine.config quando o aplicativo é iniciado e a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="49c1a-129">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="49c1a-130">Esse mecanismo permite que as configurações de todo o computador sejam definidas no arquivo Machine.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-130">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="49c1a-131">O arquivo App.config pode ser usado para substituir as configurações do arquivo Machine.config. Você também pode bloquear as configurações no arquivo Machine.config para que sejam usadas.</span><span class="sxs-lookup"><span data-stu-id="49c1a-131">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="49c1a-132">No caso do Web.config, o sistema de configuração mescla os arquivos Web.config em todos os diretórios que levam ao diretório do aplicativo na configuração que é aplicada.</span><span class="sxs-lookup"><span data-stu-id="49c1a-132">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="49c1a-133">Para obter mais informações sobre a configuração e as prioridades de configuração, consulte os tópicos no <xref:System.Configuration> namespace.</span><span class="sxs-lookup"><span data-stu-id="49c1a-133">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="49c1a-134">Seções principais do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="49c1a-134">Major Sections of the Configuration File</span></span>  

 <span data-ttu-id="49c1a-135">As seções principais do arquivo de configuração incluem os seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="49c1a-135">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="49c1a-136">As seções de associações e de comportamentos são opcionais e são incluídas apenas se necessário.</span><span class="sxs-lookup"><span data-stu-id="49c1a-136">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="49c1a-137">O \<services> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-137">The \<services> Element</span></span>  

 <span data-ttu-id="49c1a-138">O elemento `services` contém as especificações de todos os serviços que o aplicativo hospeda.</span><span class="sxs-lookup"><span data-stu-id="49c1a-138">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="49c1a-139">Começando com o modelo de configuração simplificado no .NET Framework 4, esta seção é opcional.</span><span class="sxs-lookup"><span data-stu-id="49c1a-139">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="49c1a-140">O \<service> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-140">The \<service> Element</span></span>  

 <span data-ttu-id="49c1a-141">Cada serviço tem os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="49c1a-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="49c1a-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-142">`name`.</span></span> <span data-ttu-id="49c1a-143">Especifica o tipo que fornece uma implementação de um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="49c1a-144">É um nome totalmente qualificado que consiste no namespace, em um ponto e no nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="49c1a-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="49c1a-145">Por exemplo, `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="49c1a-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="49c1a-147">Especifica o nome de um dos elementos `behavior` localizados no elemento `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="49c1a-148">O comportamento especificado governa as ações, como, por exemplo, se o serviço permite representação.</span><span class="sxs-lookup"><span data-stu-id="49c1a-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="49c1a-149">Se seu valor for o nome vazio ou se nenhum `behaviorConfiguration` for fornecido, o conjunto padrão de comportamentos de serviço será adicionado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="49c1a-150">O \<endpoint> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-150">The \<endpoint> Element</span></span>  

 <span data-ttu-id="49c1a-151">Cada ponto de extremidade requer um endereço, uma associação e um contrato, que são representados pelos seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="49c1a-151">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="49c1a-152">`address`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-152">`address`.</span></span> <span data-ttu-id="49c1a-153">Especifica o URI (Uniform Resource Identifier) do serviço, que pode ser um endereço absoluto ou um endereço fornecido em relação ao endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-153">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="49c1a-154">Se definido como uma cadeia de caracteres vazia, indicará que o ponto de extremidade está disponível no endereço básico especificado ao criar <xref:System.ServiceModel.ServiceHost> do serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-154">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="49c1a-155">`binding`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-155">`binding`.</span></span> <span data-ttu-id="49c1a-156">Normalmente especifica uma associação fornecida pelo sistema, como <xref:System.ServiceModel.WSHttpBinding>, mas também pode especificar uma associação definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="49c1a-156">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="49c1a-157">A associação especificada determina o tipo de transporte, de segurança e de codificação usado, e se sessões confiáveis, transações ou streaming são suportados ou se estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="49c1a-157">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="49c1a-158">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-158">`bindingConfiguration`.</span></span> <span data-ttu-id="49c1a-159">Se os valores padrão de uma associação precisarem ser modificados, isso poderá ser feito configurando o elemento `binding` apropriado no elemento `bindings`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-159">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="49c1a-160">Esse atributo deve receber o mesmo valor que o atributo `name` do elemento `binding` que é usado para alterar os padrões.</span><span class="sxs-lookup"><span data-stu-id="49c1a-160">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="49c1a-161">Se nenhum nome for fornecido, ou se nenhum `bindingConfiguration` estiver especificado na associação, a associação padrão do tipo de associação será usada no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="49c1a-161">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="49c1a-162">`contract`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-162">`contract`.</span></span> <span data-ttu-id="49c1a-163">Especifica a interface que define o contrato.</span><span class="sxs-lookup"><span data-stu-id="49c1a-163">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="49c1a-164">Essa é a interface implementada no tipo CLR (Common Language Runtime) especificado pelo atributo `name` do elemento `service`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-164">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="49c1a-165">O \<bindings> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-165">The \<bindings> Element</span></span>  

 <span data-ttu-id="49c1a-166">O elemento `bindings` contém as especificações de todas as associações que podem ser usadas por qualquer ponto de extremidade definido em qualquer serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-166">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="49c1a-167">O \<binding> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-167">The \<binding> Element</span></span>  

 <span data-ttu-id="49c1a-168">Os `binding` elementos contidos no `bindings` elemento podem ser uma das associações fornecidas pelo sistema (consulte [associações fornecidas pelo sistema](system-provided-bindings.md)) ou uma associação personalizada (consulte [associações personalizadas](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="49c1a-168">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="49c1a-169">O elemento `binding` tem um atributo `name` que correlaciona a associação ao ponto de extremidade especificado no atributo `bindingConfiguration` do elemento `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-169">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="49c1a-170">Se nenhum nome for especificado, a associação corresponderá ao padrão desse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="49c1a-170">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="49c1a-171">Para obter mais informações sobre como configurar serviços e clientes, consulte [Configurando serviços WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="49c1a-171">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="49c1a-172">O \<behaviors> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-172">The \<behaviors> Element</span></span>  

 <span data-ttu-id="49c1a-173">Esse é um elemento contêiner dos elementos `behavior` que definem os comportamentos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-173">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="49c1a-174">O \<behavior> elemento</span><span class="sxs-lookup"><span data-stu-id="49c1a-174">The \<behavior> Element</span></span>  

 <span data-ttu-id="49c1a-175">Cada `behavior` elemento é identificado por um `name` atributo e fornece um comportamento fornecido pelo sistema, como <`throttling`> ou um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="49c1a-175">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="49c1a-176">Se nenhum nome for fornecido, esse elemento de comportamento corresponderá ao comportamento padrão do serviço ou do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="49c1a-176">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="49c1a-177">Como usar as configurações de associação e de comportamento</span><span class="sxs-lookup"><span data-stu-id="49c1a-177">How to Use Binding and Behavior Configurations</span></span>  

 <span data-ttu-id="49c1a-178">O WCF facilita o compartilhamento de configurações entre pontos de extremidade usando um sistema de referência na configuração.</span><span class="sxs-lookup"><span data-stu-id="49c1a-178">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="49c1a-179">Em vez de atribuir valores de configuração diretamente a um ponto de extremidade, os valores da configuração relacionados à associação são agrupados em elementos `bindingConfiguration` na seção `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-179">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="49c1a-180">A configuração de uma associação é um grupo nomeado de configurações em uma associação.</span><span class="sxs-lookup"><span data-stu-id="49c1a-180">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="49c1a-181">Os pontos de extremidade podem fazer referência a `bindingConfiguration` por nome.</span><span class="sxs-lookup"><span data-stu-id="49c1a-181">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="49c1a-182">O `name` de `bindingConfiguration` é definido no elemento `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="49c1a-182">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="49c1a-183">O `name` deve ser uma cadeia de caracteres exclusiva dentro do escopo do tipo de associação — nesse caso, o [<BasicHttpBinding \> ](../configure-apps/file-schema/wcf/basichttpbinding.md)ou um valor vazio para se referir à associação padrão.</span><span class="sxs-lookup"><span data-stu-id="49c1a-183">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="49c1a-184">O ponto de extremidade vincula-se à configuração definindo o atributo `bindingConfiguration` para essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="49c1a-184">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="49c1a-185">Um `behaviorConfiguration` é implementado da mesma forma, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="49c1a-185">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="49c1a-186">Observe que o conjunto padrão de comportamentos de serviço é adicionado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="49c1a-186">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="49c1a-187">Esse sistema permite que os pontos de extremidade compartilhem configurações comuns sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="49c1a-187">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="49c1a-188">Se o escopo de todo o computador for necessário, crie a configuração de associação ou comportamento no Machine.config. As definições de configuração estão disponíveis em todos os arquivos de App.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-188">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="49c1a-189">A [ferramenta do editor de configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) facilita a criação de configurações.</span><span class="sxs-lookup"><span data-stu-id="49c1a-189">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="49c1a-190">Mesclagem de comportamentos</span><span class="sxs-lookup"><span data-stu-id="49c1a-190">Behavior Merge</span></span>  

 <span data-ttu-id="49c1a-191">O recurso de mesclagem de comportamentos facilita o gerenciamento dos comportamentos quando você deseja que um conjunto de comportamentos comuns sejam usados de maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="49c1a-191">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="49c1a-192">Esse recurso permite que você especifique comportamentos em diferentes níveis da hierarquia de configuração e faça com que os serviços herdem comportamentos de vários níveis da hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="49c1a-192">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="49c1a-193">Para ilustrar como isso funciona, suponha que você tenha o seguinte layout de diretório virtual no IIS:</span><span class="sxs-lookup"><span data-stu-id="49c1a-193">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="49c1a-194">E seu `~\Web.config` arquivo tem o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="49c1a-194">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="49c1a-195">E você tem um Web.config filho localizado em ~\Child\Web.config com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="49c1a-195">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="49c1a-196">O serviço localizado em ~\Child\Service.svc se comportará como se tivesse os comportamentos de serviceDebug e de serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="49c1a-196">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="49c1a-197">O serviço localizado em ~ \ Service.svc só terá o comportamento de serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="49c1a-197">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="49c1a-198">O que acontece é que as duas coleções de comportamentos com o mesmo nome (neste caso a cadeia de caracteres vazia) são mescladas.</span><span class="sxs-lookup"><span data-stu-id="49c1a-198">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="49c1a-199">Você também pode limpar as coleções de comportamento usando a \<clear> marca e removeu comportamentos individuais da coleção usando a \<remove> marca.</span><span class="sxs-lookup"><span data-stu-id="49c1a-199">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="49c1a-200">Por exemplo, as duas configurações a seguir resultam no serviço filho que tem apenas o comportamento de serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="49c1a-200">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="49c1a-201">A mesclagem de comportamentos é feita para coleções de comportamentos sem nome, conforme mostrado acima, e também para coleções de comportamentos nomeadas.</span><span class="sxs-lookup"><span data-stu-id="49c1a-201">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="49c1a-202">A mesclagem de comportamento funciona no ambiente de hospedagem do IIS, no qual Web.config arquivos são mesclados hierarquicamente com o arquivo de Web.config raiz e machine.config. Mas ele também funciona no ambiente de aplicativo, onde machine.config pode mesclar com o arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="49c1a-202">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="49c1a-203">A mesclagem de comportamentos se aplica aos comportamentos de ponto de extremidade e aos comportamentos de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="49c1a-203">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="49c1a-204">Se uma coleção de comportamentos filho contiver um comportamento que já esteja presente na coleção de comportamentos pai, o comportamento filho substituirá o pai.</span><span class="sxs-lookup"><span data-stu-id="49c1a-204">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="49c1a-205">Portanto, se uma coleção de comportamentos pai tivesse sido `<serviceMetadata httpGetEnabled="False" />` e uma coleção de comportamentos filho tivesse `<serviceMetadata httpGetEnabled="True" />` , o comportamento filho substituiria o comportamento pai na coleção de comportamentos e HttpGetEnabled seria "true".</span><span class="sxs-lookup"><span data-stu-id="49c1a-205">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c1a-206">Veja também</span><span class="sxs-lookup"><span data-stu-id="49c1a-206">See also</span></span>

- [<span data-ttu-id="49c1a-207">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="49c1a-207">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="49c1a-208">Configurando serviços WCF</span><span class="sxs-lookup"><span data-stu-id="49c1a-208">Configuring WCF services</span></span>](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
