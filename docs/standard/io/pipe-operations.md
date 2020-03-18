---
title: Operações básicas de pipe no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706550"
---
# <a name="pipe-operations-in-net"></a>Operações básicas de pipe no .NET
Os pipes fornecem um meio de comunicação entre processos. Existem dois tipos de pipes:  
  
- Pipes anônimos.  
  
     Os pipes anônimos fornecem comunicação entre processos em um computador local. Os pipes anônimos exigem menos sobrecarga do que os pipes nomeados mas oferecem serviços limitados. Os pipes anônimos são unidirecionais e não podem ser usados em uma rede. Eles oferecem suporte a apenas uma única instância de servidor. Os pipes anônimos são úteis para a comunicação entre threads ou entre processos pai e filho em que os identificadores de pipe podem ser facilmente passados para o processo filho quando ele é criado.  
  
     No .NET, você implementa pipes anônimos usando as classes <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
     Veja [Como usar pipes anônimos para a comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Pipes nomeados.  
  
     Os pipes nomeados fornecem a comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe. Os pipes nomeados podem ser unidirecionais ou bidirecionais. Eles oferecem suporte à comunicação baseada em mensagens e permitem que vários clientes se conectem simultaneamente ao processo do servidor usando o mesmo nome de pipe. Os pipes nomeados também oferecem suporte à representação, que permite aos processos de conexão usar suas próprias permissões em servidores remotos.  
  
     No .NET, você implementa pipes nomeados usando as classes <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
     Veja [Como usar pipes nomeados para comunicação entre processos na rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Confira também

- [Arquivo e I/O do fluxo](../../../docs/standard/io/index.md)
- [Como usar pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Como usar pipes nomeados para comunicação entre processos em uma rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
