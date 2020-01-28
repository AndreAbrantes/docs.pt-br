---
title: Criar chaves de acesso para controles
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731162"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="91f8f-102">Como: criar chaves de acesso para controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91f8f-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="91f8f-103">Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão.</span><span class="sxs-lookup"><span data-stu-id="91f8f-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="91f8f-104">Com uma chave de acesso, o usuário pode "clicar" em um botão pressionando a tecla Alt em combinação com a chave de acesso predefinida.</span><span class="sxs-lookup"><span data-stu-id="91f8f-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="91f8f-105">Por exemplo, se um botão executar um procedimento para imprimir um formulário e, portanto, sua propriedade `Text` estiver definida como "imprimir", adicionar um e comercial antes da letra "P" faz com que a letra "P" seja sublinhada no texto do botão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91f8f-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="91f8f-106">O usuário pode executar o comando associado ao botão pressionando ALT + P.</span><span class="sxs-lookup"><span data-stu-id="91f8f-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="91f8f-107">Controles que não podem receber foco não podem ter chaves de acesso.</span><span class="sxs-lookup"><span data-stu-id="91f8f-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="91f8f-108">Program</span><span class="sxs-lookup"><span data-stu-id="91f8f-108">Programmatic</span></span>

<span data-ttu-id="91f8f-109">Defina a propriedade `Text` como uma cadeia de caracteres que inclua um e comercial (&) antes da letra que será o atalho.</span><span class="sxs-lookup"><span data-stu-id="91f8f-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> <span data-ttu-id="91f8f-110">Para usar um e comercial em uma legenda sem criar uma chave de acesso, inclua dois e comercial (& &).</span><span class="sxs-lookup"><span data-stu-id="91f8f-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="91f8f-111">Um único e comercial é exibido na legenda e nenhum caractere é sublinhado.</span><span class="sxs-lookup"><span data-stu-id="91f8f-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="91f8f-112">Designer</span><span class="sxs-lookup"><span data-stu-id="91f8f-112">Designer</span></span>

<span data-ttu-id="91f8f-113">Na janela **Propriedades** do Visual Studio, defina a propriedade **Text** como uma cadeia de caracteres que inclua um e comercial (' & ') antes da letra que será a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="91f8f-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="91f8f-114">Por exemplo, para definir a letra "P" como a chave de acesso, insira **& imprimir**.</span><span class="sxs-lookup"><span data-stu-id="91f8f-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="91f8f-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="91f8f-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="91f8f-116">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91f8f-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="91f8f-117">Como definir o texto exibido por um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91f8f-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="91f8f-118">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="91f8f-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
