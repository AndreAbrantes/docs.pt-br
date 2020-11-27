---
title: 'Como: Criar serviços Windows'
description: Use o modelo de projeto de serviço do Windows para criar um serviço. Defina a propriedade ServiceName, crie instaladores e substitua os métodos OnStart e OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
ms.openlocfilehash: 9b171fa54cf65a482625c276c26185b12075c753
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270700"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="12268-104">Como: Criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="12268-104">How to: Create Windows Services</span></span>

<span data-ttu-id="12268-105">Ao criar um serviço, você pode usar um modelo de projeto Visual Studio chamado **Serviço Windows**.</span><span class="sxs-lookup"><span data-stu-id="12268-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="12268-106">Esse modelo realiza automaticamente muito do trabalho para você referenciando as classes e namespaces apropriados, configurando a herança de classe base para serviços, e substituindo muitos dos métodos que você provavelmente desejará substituir.</span><span class="sxs-lookup"><span data-stu-id="12268-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="12268-107">O modelo de projeto do serviço Windows não está disponível na edição Express do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12268-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="12268-108">Para criar um serviço funcional, você deve, no mínimo:</span><span class="sxs-lookup"><span data-stu-id="12268-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="12268-109">Definir a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>.</span><span class="sxs-lookup"><span data-stu-id="12268-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="12268-110">Criar os instaladores necessários para seu aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="12268-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="12268-111">Substituir e especificar código para os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> para personalizar as formas nas quais o serviço funciona.</span><span class="sxs-lookup"><span data-stu-id="12268-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="12268-112">Para criar um aplicativo de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="12268-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="12268-113">Crie um projeto de **Serviço Windows**.</span><span class="sxs-lookup"><span data-stu-id="12268-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="12268-114">Para obter instruções de como escrever um serviço sem usar o modelo, confira [Como escrever serviços de forma programática](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="12268-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="12268-115">Na janela **Propriedades**, configure a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="12268-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="12268-116">![Defina a propriedade ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="12268-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="12268-117">O valor da propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> sempre deve corresponder ao nome registrado nas classes do instalador.</span><span class="sxs-lookup"><span data-stu-id="12268-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="12268-118">Se você alterar essa propriedade, também deverá atualizar a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> das classes do instalador.</span><span class="sxs-lookup"><span data-stu-id="12268-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="12268-119">Defina qualquer uma das propriedades a seguir para determinar como seu serviço funcionará.</span><span class="sxs-lookup"><span data-stu-id="12268-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="12268-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="12268-120">Property</span></span>|<span data-ttu-id="12268-121">Setting</span><span class="sxs-lookup"><span data-stu-id="12268-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="12268-122">`True` para indicar que o serviço aceitará solicitações para parar a execução; `false` para impedir que o serviço seja interrompido.</span><span class="sxs-lookup"><span data-stu-id="12268-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="12268-123">`True` para indicar que o serviço deseja receber uma notificação quando o computador no qual ele está for desligado, permitindo que a ele chamar o procedimento <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="12268-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="12268-124">`True` para indicar que o serviço aceitará solicitações para pausar ou continuar executando; `false` para impedir que o serviço seja pausado e retomado.</span><span class="sxs-lookup"><span data-stu-id="12268-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="12268-125">`True` para indicar que o serviço pode manipular notificações de alterações de status de energia do computador; `false` para impedir que o serviço seja notificado sobre alterações.</span><span class="sxs-lookup"><span data-stu-id="12268-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="12268-126">`True` para gravar entradas informativas no log de eventos do aplicativo quando seu serviço executa uma ação; `false` para desabilitar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="12268-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="12268-127">Para obter mais informações, confira [Como registrar informações em log sobre serviços](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="12268-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="12268-128">**Observação:** por padrão, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="12268-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="12268-129">Quando <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> forem definidos como `false`, o **Gerenciador de Controle de Serviço** desabilitará as opções de menu correspondentes para parar, pausar ou continuar o serviço.</span><span class="sxs-lookup"><span data-stu-id="12268-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="12268-130">Acesse o Editor de código e preencha o processamento que você deseja para os procedimentos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="12268-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="12268-131">Substitua quaisquer outros métodos para os quais você deseja definir a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="12268-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="12268-132">Adicionar os instaladores necessários para seu aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="12268-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="12268-133">Para obter mais informações, confira [Como adicionar instaladores no seu aplicativo de serviço](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="12268-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="12268-134">Compile o projeto selecionando **Compilar Solução** no menu **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="12268-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="12268-135">Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="12268-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="12268-136">Instale o serviço.</span><span class="sxs-lookup"><span data-stu-id="12268-136">Install the service.</span></span> <span data-ttu-id="12268-137">Para obter mais informações, confira [Como instalar e desinstalar serviços](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="12268-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12268-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="12268-138">See also</span></span>

- [<span data-ttu-id="12268-139">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="12268-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="12268-140">Como: Escrever serviços de forma programática</span><span class="sxs-lookup"><span data-stu-id="12268-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="12268-141">Como: Adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="12268-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="12268-142">Como: Registrar em log informações sobre serviços</span><span class="sxs-lookup"><span data-stu-id="12268-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="12268-143">Como: Iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="12268-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="12268-144">Como: Especificar o contexto de segurança para serviços</span><span class="sxs-lookup"><span data-stu-id="12268-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="12268-145">Como: instalar e desinstalar serviços</span><span class="sxs-lookup"><span data-stu-id="12268-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="12268-146">Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes</span><span class="sxs-lookup"><span data-stu-id="12268-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
