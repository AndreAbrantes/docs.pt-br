---
title: Protobuf tipos aninhados-gRPC para desenvolvedores do WCF
description: Saiba mais sobre tipos de mensagens aninhadas em Protobuf e gRPC e como elas C#são geradas no.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542840"
---
# <a name="protobuf-nested-types"></a>Tipos aninhados de Protobuf

Assim como C# permite que você declare classes dentro de outras classes, o buffer de protocolo (Protobuf) permite aninhar definições de mensagens em outras mensagens. O exemplo a seguir mostra como criar tipos de mensagens aninhadas:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

No código gerado C# , o tipo de `Inner` será declarado em uma classe de `Types` estática aninhada dentro da classe `HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)
