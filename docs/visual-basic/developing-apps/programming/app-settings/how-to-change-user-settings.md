---
title: "Como alterar configurações do usuário no Visual Basic"
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
- user settings, changing in Visual Basic
- user settings
- My.Settings object, changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: 18
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bfc5e5959d691e6a5f77fcffdb61c99bafa29aac
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Como alterar configurações do usuário no Visual Basic
Você pode alterar uma configuração do usuário atribuindo um novo valor à propriedade da configuração no objeto `My.Settings`.  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade. O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração. O **Escopo** da configuração determina se a propriedade é somente leitura: a propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Embora você possa alterar e salvar os valores das configurações de escopo do usuário em tempo de execução, as configurações de escopo do aplicativo são somente leitura e não podem ser alteradas programaticamente. Você pode alterar as configurações de escopo do aplicativo ao criar o aplicativo usando o **Designer de Projeto** ou editando o arquivo de configuração de aplicativo. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemplo  
 Este exemplo altera o valor da configuração do usuário `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração do usuário `Nickname`, do tipo `String`.  
  
 O aplicativo salva as configurações do usuário quando o aplicativo é desligado. Para salvar as configurações imediatamente, chame o método `My.Settings.Save`. Para obter mais informações, consulte [Como persistir configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Como ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [Como persistir configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Como criar grades de propriedades para configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

