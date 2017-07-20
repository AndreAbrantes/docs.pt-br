---
title: Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 314d62ae0699e63aab2dff25cce2ce37552e2a20
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic)
Este exemplo usa a função `Shell` para iniciar o aplicativo Calculadora e, em seguida, multiplica dois números enviando pressionamentos de tecla usando o método `My.Computer.Keyboard.SendKeys`.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Uma exceção <xref:System.ArgumentException> será gerada se um aplicativo com o identificador do processo solicitado não for localizado.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A chamada para a função `Shell` exige confiança total (classe <xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
