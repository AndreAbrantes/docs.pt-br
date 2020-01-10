---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716062"
---
# <a name="exception-thrown_v1-etw-event"></a>Evento ETW Exception Thrown_V1
Esse evento captura informações sobre as exceções geradas.  
  
 A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Aviso (2)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Event|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Uma exceção gerenciada é gerada.|  
  
 A tabela a seguir mostra dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Tipo de exceção|win:UnicodeString|Tipo da exceção; por exemplo, `System.NullReferenceException`.|  
|Mensagem de exceção|win:UnicodeString|A mensagem de exceção real.|  
|EIPCodeThrow|win:Pointer|Ponteiro de instrução em que ocorreu a exceção.|  
|ExceptionHR|win:UInt32|Exceção [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException (consulte [Eventos CLR ETW](clr-etw-events.md) na documentação do Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [tratamento de exceções de estado corrompido](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
## <a name="see-also"></a>Veja também

- [Eventos de CLR ETW](clr-etw-events.md)
