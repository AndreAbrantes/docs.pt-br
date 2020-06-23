---
title: Como criar um serviço Web HTTP WCF básico
description: Saiba como criar um serviço que expõe um ponto de extremidade da Web no WCF. Os pontos de extremidade da Web enviam dados usando XML ou JSON. Não há envelope SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247098"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="2dddc-105">Como criar um serviço Web HTTP WCF básico</span><span class="sxs-lookup"><span data-stu-id="2dddc-105">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="2dddc-106">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="2dddc-106">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="2dddc-107">Os pontos de extremidade Web enviam dados por XML ou JSON; não há envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="2dddc-107">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="2dddc-108">Este tópico demonstra como expor um ponto de extremidade desse tipo.</span><span class="sxs-lookup"><span data-stu-id="2dddc-108">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="2dddc-109">A única maneira de proteger um ponto de extremidade Web é exibi-lo via HTTPS, usando segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="2dddc-109">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="2dddc-110">Quando a segurança baseada em mensagem é usada, as informações de segurança são geralmente colocadas em cabeçalhos SOAP e, como as mensagens enviadas a pontos de extremidade não SOAP não contêm envelopes SOAP, não há lugar para colocar informações de segurança. Assim, é necessário confiar na segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="2dddc-110">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="2dddc-111">Para criar um ponto de extremidade Web</span><span class="sxs-lookup"><span data-stu-id="2dddc-111">To create a Web endpoint</span></span>

1. <span data-ttu-id="2dddc-112">Defina um contrato de serviço usando uma interface marcada com os atributos <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> e <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2dddc-112">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="2dddc-113">Por padrão, <xref:System.ServiceModel.Web.WebInvokeAttribute> mapeia chamadas POST para a operação.</span><span class="sxs-lookup"><span data-stu-id="2dddc-113">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="2dddc-114">É possível, entretanto, especificar o método HTTP (por exemplo, HEAD, PUT ou DELETE) para mapear a operação especificando um parâmetro "method=".</span><span class="sxs-lookup"><span data-stu-id="2dddc-114">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="2dddc-115"><xref:System.ServiceModel.Web.WebGetAttribute> não tem um parâmetro "method=" e só mapeia chamadas GET para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2dddc-115"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="2dddc-116">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="2dddc-116">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="2dddc-117">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="2dddc-117">To host the service</span></span>

1. <span data-ttu-id="2dddc-118">Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2dddc-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="2dddc-119">Adicione uma classe <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="2dddc-119">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="2dddc-120">Se você não adicionar um ponto de extremidade, <xref:System.ServiceModel.Web.WebServiceHost> criará automaticamente um ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="2dddc-120">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="2dddc-121"><xref:System.ServiceModel.Web.WebServiceHost> também adiciona <xref:System.ServiceModel.Description.WebHttpBehavior> e desabilita a página da ajuda HTTP e a funcionalidade GET da linguagem WSDL para que o ponto de extremidade de metadados não interfira no ponto de extremidade HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="2dddc-121"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="2dddc-122">A adição de um ponto de extremidade não SOAP com uma URL de "" gera um comportamento inesperado quando há uma tentativa de chamar uma operação no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2dddc-122">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="2dddc-123">O motivo disso é que o URI de escuta do ponto de extremidade é o mesmo que o URI da página de ajuda (a página que é exibida quando você navega até o endereço base de um serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="2dddc-123">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="2dddc-124">Você pode executar uma das seguintes ações para evitar que isso ocorra:</span><span class="sxs-lookup"><span data-stu-id="2dddc-124">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="2dddc-125">Especifique sempre um URI que não esteja em branco para um ponto de extremidade não SOAP.</span><span class="sxs-lookup"><span data-stu-id="2dddc-125">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="2dddc-126">Desative a página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="2dddc-126">Turn off the help page.</span></span> <span data-ttu-id="2dddc-127">Isso pode ser feito com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2dddc-127">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="2dddc-128">Abra o host do serviço e aguarde até que o usuário pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="2dddc-128">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="2dddc-129">Este exemplo demonstra como hospedar um serviço estilo Web com um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="2dddc-129">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="2dddc-130">Também é possível hospedar esse tipo de serviço no IIS.</span><span class="sxs-lookup"><span data-stu-id="2dddc-130">You can also host such a service within IIS.</span></span> <span data-ttu-id="2dddc-131">Para fazer isso, especifique a classe <xref:System.ServiceModel.Activation.WebServiceHostFactory> em um arquivo .svc como demonstra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2dddc-131">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="2dddc-132">Para chamar operações de serviço mapeadas para GET no Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="2dddc-132">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="2dddc-133">Abra o Internet Explorer e digite " `http://localhost:8000/EchoWithGet?s=Hello, world!` " e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="2dddc-133">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="2dddc-134">A URL contém o endereço base do serviço ( `http://localhost:8000/` ), o endereço relativo do ponto de extremidade (""), a operação de serviço a ser chamada ("EchoWithGet") e um ponto de interrogação seguido por uma lista de parâmetros nomeados separados por um e comercial (&).</span><span class="sxs-lookup"><span data-stu-id="2dddc-134">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="2dddc-135">Para chamar operações de serviço no código</span><span class="sxs-lookup"><span data-stu-id="2dddc-135">To call service operations in code</span></span>

1. <span data-ttu-id="2dddc-136">Crie uma instância de <xref:System.ServiceModel.ChannelFactory%601> em um bloco `using`.</span><span class="sxs-lookup"><span data-stu-id="2dddc-136">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="2dddc-137">Adicione <xref:System.ServiceModel.Description.WebHttpBehavior> ao ponto de extremidade que <xref:System.ServiceModel.ChannelFactory%601> chama.</span><span class="sxs-lookup"><span data-stu-id="2dddc-137">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="2dddc-138">Crie o canal e chame o serviço.</span><span class="sxs-lookup"><span data-stu-id="2dddc-138">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="2dddc-139">Feche a classe <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2dddc-139">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="2dddc-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2dddc-140">Example</span></span>

<span data-ttu-id="2dddc-141">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="2dddc-141">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="2dddc-142">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2dddc-142">Compiling the code</span></span>

<span data-ttu-id="2dddc-143">Ao compilar Service.cs, faça referência à System.ServiceModel.dll e à System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="2dddc-143">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dddc-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="2dddc-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="2dddc-145">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="2dddc-145">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
