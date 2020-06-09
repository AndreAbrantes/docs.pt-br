---
title: Exceções esperadas
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: d8e3c024eb69fe22ec27f3e3697bc4fc7b4ee121
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600523"
---
# <a name="expected-exceptions"></a><span data-ttu-id="0cf8e-102">Exceções esperadas</span><span class="sxs-lookup"><span data-stu-id="0cf8e-102">Expected Exceptions</span></span>
<span data-ttu-id="0cf8e-103">Este exemplo demonstra como capturar exceções esperadas ao usar um cliente digitado.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="0cf8e-104">Este exemplo é baseado no [introdução](getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0cf8e-105">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0cf8e-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cf8e-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0cf8e-107">Este exemplo demonstra como capturar e manipular os dois tipos de exceção esperados que os programas corretos devem tratar: `TimeoutException` e `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="0cf8e-108">As exceções que são geradas de métodos de comunicação em um cliente Windows Communication Foundation (WCF) são esperadas ou inesperadas.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="0cf8e-109">Exceções inesperadas incluem falhas catastróficas `OutOfMemoryException` , como e erros de programação como `ArgumentNullException` ou `InvalidOperationException` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="0cf8e-110">Normalmente, não há uma maneira útil de lidar com erros inesperados, portanto, normalmente você não deve capturá-los ao chamar um método de comunicação do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="0cf8e-111">As exceções esperadas dos métodos de comunicação em um cliente WCF incluem `TimeoutException` , `CommunicationException` e qualquer classe derivada de `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="0cf8e-112">Eles indicam um problema durante a comunicação que pode ser manipulada com segurança anulando o cliente WCF e relatando uma falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="0cf8e-113">Como fatores externos podem causar esses erros em qualquer aplicativo, os aplicativos corretos devem capturar essas exceções e recuperar quando ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="0cf8e-114">Há várias classes derivadas de `CommunicationException` que um cliente pode lançar.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="0cf8e-115">Em alguns casos, os aplicativos também capturam alguns deles para fazer uma manipulação especial, mas permitem que os outros sejam tratados como um `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="0cf8e-116">Isso pode ser feito com a captura do tipo de exceção mais específico primeiro e, em seguida, `CommunicationException` a captura de uma cláusula catch posterior.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="0cf8e-117">O código que chama um método de comunicação do cliente deve capturar `TimeoutException` e `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="0cf8e-118">Uma maneira de lidar com esses erros é anular o cliente e relatar a falha de comunicação.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="0cf8e-119">Se ocorrer uma exceção esperada, o cliente poderá ou não poderá ser usado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="0cf8e-120">Para determinar se o cliente ainda pode ser usado, verifique se a `State` propriedade é `CommunicationState` . Feito.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="0cf8e-121">Se ele ainda estiver aberto, ele ainda será utilizável.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="0cf8e-122">Caso contrário, você deve anular o cliente e liberar todas as referências a ele.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0cf8e-123">Você pode observar que os clientes que têm uma sessão geralmente não podem mais ser usados após uma exceção, e os clientes que não têm uma sessão geralmente ainda podem ser usados após uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="0cf8e-124">No entanto, nenhuma delas é garantida, portanto, se você quiser tentar continuar usando o cliente após uma exceção, seu aplicativo deverá verificar a `State` propriedade para verificar se o cliente ainda está aberto.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="0cf8e-125">Quando você executa o exemplo, as respostas e as exceções da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="0cf8e-126">O processo do cliente executa dois cenários, cada um dos quais tenta chamar `Add` seguido por `Divide` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="0cf8e-127">O primeiro cenário simula um problema de rede anulando o cliente antes de fazer a chamada para `Divide` .</span><span class="sxs-lookup"><span data-stu-id="0cf8e-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="0cf8e-128">O segundo cenário causa uma condição de tempo limite definindo o tempo limite muito curto para que o método seja concluído.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="0cf8e-129">A saída esperada do processo do cliente é:</span><span class="sxs-lookup"><span data-stu-id="0cf8e-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cf8e-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0cf8e-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0cf8e-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf8e-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0cf8e-132">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf8e-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0cf8e-133">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cf8e-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0cf8e-134">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cf8e-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0cf8e-136">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cf8e-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0cf8e-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
