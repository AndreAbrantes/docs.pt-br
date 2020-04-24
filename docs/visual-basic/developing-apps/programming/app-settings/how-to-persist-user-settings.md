---
title: 'Como: persistir configurações do usuário'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329635"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Como persistir configurações de usuário no Visual Basic

Você pode usar o método `My.Settings.Save` para persistir as alterações nas configurações do usuário.  
  
 Normalmente, os aplicativos são projetados para persistir as alterações nas configurações do usuário quando ele é desligado. Isso ocorre porque salvar as configurações pode levar alguns segundos, dependendo de vários fatores.  
  
 Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Embora você possa alterar e salvar os valores das configurações de escopo do usuário em tempo de execução, as configurações de escopo do aplicativo são somente leitura e não podem ser alteradas programaticamente. Você pode alterar as configurações de escopo do aplicativo ao criar o aplicativo, por meio do **Designer de Projeto** ou editando o arquivo de configuração do aplicativo. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemplo  

 Este exemplo altera o valor da configuração de usuário `LastChanged` e salva essa alteração chamando o método `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração do usuário `LastChanged`, do tipo `Date`. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Veja também

- [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Como ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Como alterar configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Como criar grades de propriedades para configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
