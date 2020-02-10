---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 6c125ecd0f6cef10b62e7e451eb37bba1ce89b65
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094833"
---
# <a name="using-performance-counters"></a><span data-ttu-id="cd814-102">Utilizando contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="cd814-102">Using Performance Counters</span></span>
<span data-ttu-id="cd814-103">Este exemplo demonstra como acessar os contadores de desempenho do Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cd814-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="cd814-104">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cd814-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd814-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cd814-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cd814-106">Neste exemplo, o cliente chama os quatro métodos do serviço `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="cd814-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="cd814-107">O cliente continua a fazer isso até que seja interrompido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cd814-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="cd814-108">O serviço permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="cd814-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="cd814-109">Os contadores de desempenho são habilitados na seção diagnóstico do arquivo Web. config para o serviço, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd814-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cd814-110">Essa tarefa também pode ser feita usando a [ferramenta Editor de configuração (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cd814-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="cd814-111">Quando os contadores de desempenho estão habilitados, o conjunto inteiro de contadores de desempenho do WCF é habilitado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="cd814-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="cd814-112">O .NET Framework mantém automaticamente os dados de desempenho em três níveis: `ServiceModelService`, `ServiceModelEndpoint` e `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="cd814-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="cd814-113">Cada um desses níveis tem contadores de desempenho como "chamadas", "chamadas por segundo" e "chamadas de segurança não autorizadas".</span><span class="sxs-lookup"><span data-stu-id="cd814-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd814-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cd814-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cd814-115">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd814-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cd814-116">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd814-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cd814-117">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd814-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="cd814-118">Para exibir dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="cd814-118">To view performance data</span></span>  
  
1. <span data-ttu-id="cd814-119">Inicie a ferramenta Monitor de desempenho clicando em **Iniciar**, **executar...** , insira `perfmon` e clique em OK ou **,** no painel de controle, selecione **Ferramentas administrativas** e clique duas vezes em **desempenho**.</span><span class="sxs-lookup"><span data-stu-id="cd814-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cd814-120">Você não pode adicionar contadores até que o código de exemplo esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="cd814-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="cd814-121">Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Delete.</span><span class="sxs-lookup"><span data-stu-id="cd814-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="cd814-122">Adicione os contadores do WCF clicando com o botão direito do mouse no painel gráfico e selecionando **Adicionar contadores**.</span><span class="sxs-lookup"><span data-stu-id="cd814-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="cd814-123">Na caixa de diálogo **Adicionar contadores** , selecione **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** na caixa de listagem suspensa objeto de desempenho.</span><span class="sxs-lookup"><span data-stu-id="cd814-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="cd814-124">Selecione os contadores que você deseja exibir na lista.</span><span class="sxs-lookup"><span data-stu-id="cd814-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cd814-125">Não haverá nenhum contador de desempenho do WCF para um serviço se não houver nenhum serviço WCF em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="cd814-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="cd814-126">Para usar o editor de configuração para habilitar contadores</span><span class="sxs-lookup"><span data-stu-id="cd814-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="cd814-127">Abra uma instância do SvcConfigEditor. exe.</span><span class="sxs-lookup"><span data-stu-id="cd814-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="cd814-128">No menu arquivo, clique em **abrir** e em **arquivo de configuração...** .</span><span class="sxs-lookup"><span data-stu-id="cd814-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="cd814-129">Navegue até a pasta de serviço do aplicativo de exemplo e abra o arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="cd814-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="cd814-130">Clique em **diagnóstico** na árvore de configuração.</span><span class="sxs-lookup"><span data-stu-id="cd814-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="cd814-131">Alterne o **contador de desempenho** na janela de **diagnóstico** para mostrar ' todos '.</span><span class="sxs-lookup"><span data-stu-id="cd814-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="cd814-132">Salve o arquivo de configuração e saia do editor.</span><span class="sxs-lookup"><span data-stu-id="cd814-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cd814-133">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cd814-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cd814-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cd814-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cd814-135">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="cd814-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd814-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cd814-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="cd814-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd814-137">See also</span></span>

- <span data-ttu-id="cd814-138">[Exemplos de monitoramento do AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cd814-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
