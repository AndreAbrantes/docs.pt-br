---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804450"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret não é permitido em uma região try

|   |   |
|---|---|
|Detalhes|Ao contrário do compilador Just-In-Time JIT64, o RyuJIT (usado no .NET Framework 4.6) não permite que uma instrução IL ret em uma região try. Retornar de uma região try não é permitido pela especificação ECMA-335, e nenhum compilador gerenciado conhecido gera tal IL. No entanto, o compilador JIT64 executará essa IL se ela for gerada usando emissão de reflexo.|
|Sugestão|Se um aplicativo estiver gerando uma IL que inclua um opcode ret em uma região try, o aplicativo poderá ser direcionado ao .NET Framework 4.5 para usar o JIT antigo e evitar essa interrupção. Como alternativa, a IL gerada pode ser atualizado para retornar após a região try.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Type|Redirecionando|
