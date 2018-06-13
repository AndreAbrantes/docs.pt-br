---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475280"
---
# <a name="msmq"></a><span data-ttu-id="673bc-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="673bc-102">MSMQ</span></span>
<span data-ttu-id="673bc-103">Em um aplicativo do MSMQ, nenhuma atividade adicional é transferida do canal em fila MSMQ e MSMQ no canal em fila.</span><span class="sxs-lookup"><span data-stu-id="673bc-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="673bc-104">Além disso, a ID de mensagem do MSMQ e a ID de mensagem SOAP (junto com a ID da atividade, se houver) são rastreadas como parte de rastreamentos de canal em fila em uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="673bc-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="673bc-105">ID de mensagem do MSMQ e a ID de mensagem SOAP (juntamente com a atividade de ID, se existe) são rastreadas como parte de rastreamentos de canal em fila em uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="673bc-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="673bc-106">As transferências necessárias na operação de recebimento são executadas da mesma forma para qualquer outro transporte (receber bytes de mensagem de processo -> -> operação).</span><span class="sxs-lookup"><span data-stu-id="673bc-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
