---
title: Ativação TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 0fa737adbdc7acc51511557877799c89849149bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598652"
---
# <a name="tcp-activation"></a><span data-ttu-id="27ea3-102">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="27ea3-102">TCP Activation</span></span>

<span data-ttu-id="27ea3-103">Este exemplo demonstra a hospedagem de um serviço que usa o WAS (serviços de ativação de processos do Windows) para ativar um serviço que se comunica através do protocolo net. TCP.</span><span class="sxs-lookup"><span data-stu-id="27ea3-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="27ea3-104">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="27ea3-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="27ea3-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="27ea3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27ea3-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="27ea3-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="27ea3-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="27ea3-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="27ea3-108">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="27ea3-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27ea3-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="27ea3-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="27ea3-110">O exemplo consiste em um programa de console do cliente (. exe) e uma biblioteca de serviços (. dll) hospedada em um processo de trabalho ativado pelo WAS.</span><span class="sxs-lookup"><span data-stu-id="27ea3-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="27ea3-111">A atividade do cliente fica visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="27ea3-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="27ea3-112">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="27ea3-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="27ea3-113">O contrato é definido pela `ICalculator` interface, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="27ea3-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="27ea3-114">A implementação do serviço calcula e retorna o resultado apropriado:</span><span class="sxs-lookup"><span data-stu-id="27ea3-114">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="27ea3-115">O exemplo usa uma variante da Associação net. TCP com compartilhamento de porta TCP habilitada e segurança desativada.</span><span class="sxs-lookup"><span data-stu-id="27ea3-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="27ea3-116">Se você quiser usar uma associação TCP segura, altere o modo de segurança do servidor para a configuração desejada e execute novamente svcutil. exe no cliente para gerar um arquivo de configuração de cliente de atualização.</span><span class="sxs-lookup"><span data-stu-id="27ea3-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="27ea3-117">O exemplo a seguir mostra a configuração para o serviço:</span><span class="sxs-lookup"><span data-stu-id="27ea3-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="27ea3-118">O ponto de extremidade do cliente é configurado conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="27ea3-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="27ea3-119">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="27ea3-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="27ea3-120">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="27ea3-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27ea3-121">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="27ea3-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="27ea3-122">Verifique se o IIS 7,0 está instalado.</span><span class="sxs-lookup"><span data-stu-id="27ea3-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="27ea3-123">O IIS 7,0 é necessário para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="27ea3-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="27ea3-124">Certifique-se de ter executado o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27ea3-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="27ea3-125">Além disso, você deve instalar os componentes de ativação não HTTP do WCF:</span><span class="sxs-lookup"><span data-stu-id="27ea3-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="27ea3-126">No menu **Iniciar**, selecione **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="27ea3-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="27ea3-127">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="27ea3-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="27ea3-128">Clique em **Ativar ou desativar componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="27ea3-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="27ea3-129">Expanda o nó **Microsoft .NET Framework 3,0** e verifique o Windows Communication Foundation recurso de **ativação não http** .</span><span class="sxs-lookup"><span data-stu-id="27ea3-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="27ea3-130">Configurar o WAS para dar suporte à ativação de TCP.</span><span class="sxs-lookup"><span data-stu-id="27ea3-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="27ea3-131">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetTcpSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="27ea3-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="27ea3-132">Para dar suporte à ativação net. TCP, o site padrão deve primeiro ser associado a uma porta Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="27ea3-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="27ea3-133">Isso pode ser feito usando o Appcmd. exe, que é instalado com o conjunto de ferramentas de gerenciamento do Serviços de Informações da Internet 7,0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="27ea3-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="27ea3-134">Em um prompt de comando de nível de administrador, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="27ea3-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="27ea3-135">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="27ea3-135">This command is a single line of text.</span></span> <span data-ttu-id="27ea3-136">Esse comando adiciona uma associação de site net. TCP ao site padrão escutando na porta TCP 808 com qualquer nome de host.</span><span class="sxs-lookup"><span data-stu-id="27ea3-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="27ea3-137">Embora todos os aplicativos em um site compartilhem uma associação net. TCP comum, cada aplicativo pode habilitar o suporte a net. TCP individualmente.</span><span class="sxs-lookup"><span data-stu-id="27ea3-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="27ea3-138">Para habilitar net. TCP para o aplicativo/servicemodelsamples, execute o seguinte comando em um prompt de comando de nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="27ea3-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="27ea3-139">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="27ea3-139">This command is a single line of text.</span></span> <span data-ttu-id="27ea3-140">Esse comando permite que o aplicativo/servicemodelsamples seja acessado usando o `http://localhost/servicemodelsamples` e o `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="27ea3-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="27ea3-141">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27ea3-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="27ea3-142">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27ea3-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    <span data-ttu-id="27ea3-143">Remova a associação de site net. TCP que você adicionou para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="27ea3-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="27ea3-144">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="27ea3-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="27ea3-145">Remova net. TCP da lista de protocolos habilitados executando o seguinte comando de um prompt de comando de nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="27ea3-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="27ea3-146">Esse comando deve ser inserido como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="27ea3-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="27ea3-147">Remova a associação de site net. TCP executando o seguinte comando de um prompt de comando de nível de administrador:</span><span class="sxs-lookup"><span data-stu-id="27ea3-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="27ea3-148">Esse comando deve ser digitado como uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="27ea3-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="27ea3-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27ea3-149">See also</span></span>

- <span data-ttu-id="27ea3-150">[Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="27ea3-150">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
