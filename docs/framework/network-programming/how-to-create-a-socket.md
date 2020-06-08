---
title: Como criar um soquete
description: Saiba como inicializar um soquete para se comunicar com dispositivos remotos. Use a classe Socket para especificar a família de endereços, o tipo de soquete e o tipo de protocolo.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502542"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="c2e85-104">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="c2e85-104">How to: Create a Socket</span></span>
<span data-ttu-id="c2e85-105">Antes de poder usar um soquete para se comunicar com dispositivos remotos, o soquete deve ser inicializado com as informações de protocolo e endereço de rede.</span><span class="sxs-lookup"><span data-stu-id="c2e85-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="c2e85-106">O construtor da classe <xref:System.Net.Sockets.Socket> tem parâmetros que especificam a família de endereços, o tipo de soquete e o tipo de protocolo usado pelo soquete para fazer conexões.</span><span class="sxs-lookup"><span data-stu-id="c2e85-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2e85-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2e85-107">Example</span></span>  
 <span data-ttu-id="c2e85-108">O exemplo a seguir cria um Socket que pode ser usado para se comunicar em uma rede baseada em TCP/IP, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="c2e85-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="c2e85-109">Para usar o UDP em vez do TCP, altere o tipo de protocolo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="c2e85-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="c2e85-110">A enumeração <xref:System.Net.Sockets.AddressFamily> especifica as famílias de endereços padrão usadas pela classe **Socket** para resolver endereços de rede (por exemplo, o membro **AddressFamily.InterNetwork** especifica a família de endereços IP versão 4).</span><span class="sxs-lookup"><span data-stu-id="c2e85-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="c2e85-111">A enumeração <xref:System.Net.Sockets.SocketType> especifica o tipo de soquete (por exemplo, o membro **SocketType.Stream** indica um soquete padrão para envio e recebimento de dados com o controle de fluxo).</span><span class="sxs-lookup"><span data-stu-id="c2e85-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="c2e85-112">A enumeração <xref:System.Net.Sockets.ProtocolType> especifica o protocolo de rede a ser usado ao se comunicar no **Socket** (por exemplo, **ProtocolType.Tcp** indica que o soquete usa TCP; **ProtocolType.Udp** indica que o soquete usa UDP).</span><span class="sxs-lookup"><span data-stu-id="c2e85-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="c2e85-113">Depois que um **Socket** for criado, ele poderá iniciar uma conexão com um ponto de extremidade remoto ou receber conexões de dispositivos remotos.</span><span class="sxs-lookup"><span data-stu-id="c2e85-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e85-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2e85-114">See also</span></span>

- [<span data-ttu-id="c2e85-115">Usando soquetes do cliente</span><span class="sxs-lookup"><span data-stu-id="c2e85-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="c2e85-116">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="c2e85-116">Listening with Sockets</span></span>](listening-with-sockets.md)
