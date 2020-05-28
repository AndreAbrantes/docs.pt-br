---
title: Criando aplicativos multicasting usando o transporte UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 40944129ce3b01d8422d5aba4cfbf913c56265ed
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144624"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="0d13b-102">Criando aplicativos multicasting usando o transporte UDP</span><span class="sxs-lookup"><span data-stu-id="0d13b-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="0d13b-103">Os aplicativos de multicast enviam mensagens pequenas para um grande número de destinatários ao mesmo tempo, sem a necessidade de estabelecer conexões ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="0d13b-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="0d13b-104">A ênfase desses aplicativos é a velocidade em relação à confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="0d13b-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="0d13b-105">Em outras palavras, é mais importante enviar dados oportunos do que garantir que qualquer mensagem específica seja realmente recebida.</span><span class="sxs-lookup"><span data-stu-id="0d13b-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="0d13b-106">O WCF agora dá suporte à gravação de aplicativos de multicast usando o <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0d13b-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="0d13b-107">Esse transporte é útil em cenários em que um serviço precisa enviar mensagens pequenas para vários clientes simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="0d13b-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="0d13b-108">Um aplicativo de cotação de ações é um exemplo desse serviço.</span><span class="sxs-lookup"><span data-stu-id="0d13b-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="0d13b-109">Implementando um aplicativo multicast</span><span class="sxs-lookup"><span data-stu-id="0d13b-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="0d13b-110">Para implementar um aplicativo multicast, defina um contrato de serviço e para cada componente de software que precise responder às mensagens multicast, implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d13b-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="0d13b-111">Por exemplo, um aplicativo de cotação de ações pode definir um contrato de serviço:</span><span class="sxs-lookup"><span data-stu-id="0d13b-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="0d13b-112">Cada aplicativo que deseja receber mensagens multicast deve hospedar um serviço que expõe essa interface.</span><span class="sxs-lookup"><span data-stu-id="0d13b-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="0d13b-113">Por exemplo, aqui está um exemplo de código que ilustra como receber mensagens multicast:</span><span class="sxs-lookup"><span data-stu-id="0d13b-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="0d13b-114">O aplicativo especifica o endereço UDP em que todos os serviços serão escutados.</span><span class="sxs-lookup"><span data-stu-id="0d13b-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="0d13b-115">Um novo <xref:System.ServiceModel.ServiceHost> é criado e um ponto de extremidade de serviço é exposto usando o <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0d13b-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="0d13b-116">O <xref:System.ServiceModel.ServiceHost> é então aberto e começará a escutar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="0d13b-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="0d13b-117">Nesse tipo de cenário, ele é o cliente que realmente envia mensagens de multicast.</span><span class="sxs-lookup"><span data-stu-id="0d13b-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="0d13b-118">Cada serviço que está escutando no endereço UDP correto receberá as mensagens de multicast.</span><span class="sxs-lookup"><span data-stu-id="0d13b-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="0d13b-119">Aqui está um exemplo de um cliente que envia mensagens de multicast:</span><span class="sxs-lookup"><span data-stu-id="0d13b-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="0d13b-120">Esse código gera informações de ações e, em seguida, usa o contrato de serviço IStockTicker para enviar mensagens de multicast para serviços de chamada escutando o endereço UDP correto.</span><span class="sxs-lookup"><span data-stu-id="0d13b-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="0d13b-121">UDP e sistema de mensagens confiável</span><span class="sxs-lookup"><span data-stu-id="0d13b-121">UDP and Reliable Messaging</span></span>  
  <span data-ttu-id="0d13b-122">A associação UDP não oferece suporte a mensagens confiáveis devido à natureza leve do protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="0d13b-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="0d13b-123">Se você precisar confirmar que as mensagens são recebidas por um ponto de extremidade remoto, use um transporte que ofereça suporte a mensagens confiáveis como HTTP ou TCP.</span><span class="sxs-lookup"><span data-stu-id="0d13b-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="0d13b-124">Para obter mais informações sobre mensagens confiáveis, consulte <https://go.microsoft.com/fwlink/?LinkId=231830> .</span><span class="sxs-lookup"><span data-stu-id="0d13b-124">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="0d13b-125">Mensagens multicast bidirecionais</span><span class="sxs-lookup"><span data-stu-id="0d13b-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="0d13b-126">Embora as mensagens multicast sejam geralmente unidirecionais, o UdpBinding dá suporte à troca de mensagens de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="0d13b-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="0d13b-127">As mensagens enviadas usando o transporte UDP contêm um endereço de e para.</span><span class="sxs-lookup"><span data-stu-id="0d13b-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="0d13b-128">Deve-se ter cuidado ao usar o endereço de no, pois ele poderia ser alterado de forma mal-intencionada.</span><span class="sxs-lookup"><span data-stu-id="0d13b-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="0d13b-129">O endereço pode ser verificado usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0d13b-129">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="0d13b-130">Esse código verifica o primeiro byte do endereço de para ver se ele contém 0xE0, o que significa que o endereço é um endereço de várias difusões.</span><span class="sxs-lookup"><span data-stu-id="0d13b-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="0d13b-131">Considerações de segurança</span><span class="sxs-lookup"><span data-stu-id="0d13b-131">Security Considerations</span></span>  
 <span data-ttu-id="0d13b-132">Ao escutar mensagens multicast, um pacote ICMP é enviado ao roteador, notificando-o sobre o endereço de multicast.</span><span class="sxs-lookup"><span data-stu-id="0d13b-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="0d13b-133">Qualquer pessoa na sub-rede local que tenha permissões pode escutar esses tipos de pacotes e determinar qual endereço de multicast e porta você está ouvindo.</span><span class="sxs-lookup"><span data-stu-id="0d13b-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="0d13b-134">Não use o endereço IP do remetente para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="0d13b-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="0d13b-135">Essas informações podem ser falsificadas e podem fazer com que um aplicativo envie respostas para o computador errado.</span><span class="sxs-lookup"><span data-stu-id="0d13b-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="0d13b-136">Uma maneira de mitigar essa ameaça é habilitar a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0d13b-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="0d13b-137">No nível da rede, o IPSec (segurança do protocolo Internet) e/ou NAP (proteção de acesso à rede) também pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="0d13b-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
