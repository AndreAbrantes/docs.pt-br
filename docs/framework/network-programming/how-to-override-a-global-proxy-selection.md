---
title: Como substituir uma seleção de proxy global
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048268"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Como substituir uma seleção de proxy global
Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Uma [ `using` diretiva](../../csharp/language-reference/keywords/using-directive.md) para o **System.Net** namespace.  
  
## <a name="see-also"></a>Confira também

- [Usando protocolos de aplicativo](using-application-protocols.md)
- [Acessando a Internet através de um proxy](accessing-the-internet-through-a-proxy.md)
