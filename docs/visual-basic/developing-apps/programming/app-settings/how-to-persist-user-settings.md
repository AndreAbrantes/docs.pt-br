---
title: 'Como: persistir configurações do usuário'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410147"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="1fd92-102">Como persistir configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fd92-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="1fd92-103">Você pode usar o método `My.Settings.Save` para persistir as alterações nas configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fd92-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="1fd92-104">Normalmente, os aplicativos são projetados para persistir as alterações nas configurações do usuário quando ele é desligado.</span><span class="sxs-lookup"><span data-stu-id="1fd92-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="1fd92-105">Isso ocorre porque salvar as configurações pode levar alguns segundos, dependendo de vários fatores.</span><span class="sxs-lookup"><span data-stu-id="1fd92-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="1fd92-106">Para obter mais informações, consulte [Objeto My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="1fd92-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fd92-107">Embora você possa alterar e salvar os valores das configurações de escopo do usuário em tempo de execução, as configurações de escopo do aplicativo são somente leitura e não podem ser alteradas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="1fd92-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="1fd92-108">Você pode alterar as configurações de escopo do aplicativo ao criar o aplicativo, por meio do **Designer de Projeto** ou editando o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fd92-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="1fd92-109">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1fd92-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fd92-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fd92-110">Example</span></span>  

 <span data-ttu-id="1fd92-111">Este exemplo altera o valor da configuração de usuário `LastChanged` e salva essa alteração chamando o método `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="1fd92-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="1fd92-112">Para que esse exemplo funcione, seu aplicativo deve ter uma configuração do usuário `LastChanged`, do tipo `Date`.</span><span class="sxs-lookup"><span data-stu-id="1fd92-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="1fd92-113">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1fd92-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd92-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1fd92-114">See also</span></span>

- [<span data-ttu-id="1fd92-115">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="1fd92-115">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="1fd92-116">Como ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fd92-116">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="1fd92-117">Como alterar configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fd92-117">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="1fd92-118">Como criar grades de propriedades para configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fd92-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="1fd92-119">Gerenciando configurações de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="1fd92-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
