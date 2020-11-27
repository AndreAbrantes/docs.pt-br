---
title: Transporte de integração do MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 032b6886152fb73c382fed1572e8c184a822b44f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248741"
---
# <a name="msmq-integration-transport"></a>Transporte de integração do MSMQ

Este tópico lista todas as exceções geradas pelo transporte de integração do MSMQ.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Essa fábrica armazena as mensagens em buffer, portanto, os tamanhos das mensagens devem estar no intervalo de um valor inteiro.|  
|MsmqByteArrayBodyExpected|Ocorreu uma incompatibilidade entre o formato de serialização especificado e o corpo da mensagem MSMQ. A mensagem não pode ser enviada ou recebida. O formato de serialização ByteArray exige que o corpo da mensagem MSMQ seja do tipo Byte [].|  
|MsmqCannotDeserializeActiveXMessage|Ocorreu um erro de serialização do ActiveX. A mensagem não pode ser enviada ou recebida. O tipo de variante especificado para o corpo não corresponde ao corpo de mensagem do MSMQ real.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|As propriedades da mensagem são incompatíveis. A mensagem não pode ser enviada ou recebida. A propriedade de mensagem BodyType não poderá ser especificada se o formato de serialização ActiveX for usado.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Falha na validação de MsmqIntegrationBinding. Não é possível iniciar o ponto de extremidade de serviço. A associação especificada não oferece suporte à assinatura de método para a operação de serviço especificada no contrato especificado. Corrija a operação de serviço para usar o MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|A serialização do ActiveX falhou porque o formato de serialização não pode ser reconhecido. A mensagem não pode ser enviada ou recebida.|  
|MsmqInvalidTypeSerialization|O tipo de variante não é reconhecido. Falha na serialização do ActiveX. A mensagem não pode ser enviada ou recebida. Não há suporte para o tipo de variante especificado.|  
|MsmqStreamBodyExpected|Incompatibilidade entre o formato de serialização e o conteúdo do corpo. Não é possível enviar ou receber a mensagem. Somente um corpo do tipo Stream pode ser enviado ou recebido usando o modo de serialização de fluxo.|
