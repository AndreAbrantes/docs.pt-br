---
title: Responder a alterações de esquema de fonte em um aplicativo Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739232"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="8f9ef-102">Como responder a alterações no esquema de fontes em um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f9ef-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="8f9ef-103">Nos sistemas operacionais Windows, um usuário pode alterar as configurações de fonte de todo o sistema para tornar a fonte padrão maior ou menor.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="8f9ef-104">A alteração dessas configurações de fonte é essencial para usuários com deficiência visual, que requerem letras maiores para ler o texto em suas telas.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="8f9ef-105">É possível ajustar seu aplicativo do Windows Forms para reagir a essas alterações aumentando ou diminuindo o tamanho do formulário e todo o texto contido nele sempre que o esquema de fontes for alterado.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="8f9ef-106">Se desejar que seu formulário acomode as alterações em tamanhos de fonte dinamicamente, será possível adicionar código a ele.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="8f9ef-107">Normalmente, a fonte padrão usada pelo Windows Forms é a fonte retornada pela chamada de namespace de <xref:Microsoft.Win32> para `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="8f9ef-108">A fonte retornada por essa chamada muda apenas quando a resolução da tela é alterada.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="8f9ef-109">Conforme mostrado no procedimento a seguir, seu código deve alterar a fonte padrão para <xref:System.Drawing.SystemFonts.IconTitleFont%2A> para responder às alterações no tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="8f9ef-110">Utilizar a fonte da área de trabalho e responder a alterações no esquema de fontes</span><span class="sxs-lookup"><span data-stu-id="8f9ef-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="8f9ef-111">Crie seu formulário e adicione os controles desejados a ele.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="8f9ef-112">Para obter mais informações, consulte [Como criar um aplicativo do Windows Forms na linha de comando](how-to-create-a-windows-forms-application-from-the-command-line.md) e [Controles para Uso no Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8f9ef-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="8f9ef-113">Adicione uma referência ao namespace <xref:Microsoft.Win32> ao seu código.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="8f9ef-114">Adicione o seguinte código ao construtor do formulário para ligar manipuladores de eventos necessários e para alterar a fonte padrão em uso do formulário.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="8f9ef-115">Implemente um manipulador para o evento <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> que faz com que o formulário seja dimensionado automaticamente quando a categoria de <xref:Microsoft.Win32.UserPreferenceCategory.Window> é alterada.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="8f9ef-116">Por fim, implemente um manipulador para o evento <xref:System.Windows.Forms.Form.FormClosing> que desanexa o manipulador de eventos <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="8f9ef-117">Uma falha na inclusão desse código fará com que ocorra vazamento de memória no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="8f9ef-118">Compile e execute o código.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="8f9ef-119">Alterar manualmente o esquema de fontes no Windows XP</span><span class="sxs-lookup"><span data-stu-id="8f9ef-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="8f9ef-120">Enquanto o Aplicativo do Windows Forms está em execução, clique com o botão direito do mouse na área de trabalho do Windows e escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="8f9ef-121">Na caixa de diálogo **Propriedades de Exibição**, clique na guia **Aparência**.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="8f9ef-122">Na caixa de listagem suspensa **Tamanho da Fonte**, selecione um novo tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="8f9ef-123">Você observará que o formulário agora reage às alterações de tempo de execução no esquema de fontes da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="8f9ef-124">Quando o usuário altera entre **Normal**, **Fontes Grandes** e **Fontes Extra Grandes**, o formulário muda a fonte e ajusta a escala corretamente.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f9ef-125">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8f9ef-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="8f9ef-126">O Construtor neste exemplo de código contém uma chamada para `InitializeComponent`, que é definida quando você cria um novo projeto de Windows Forms no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="8f9ef-127">Remova essa linha de código se estiver compilando um aplicativo na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8f9ef-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9ef-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f9ef-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="8f9ef-129">Dimensionamento automático no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f9ef-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
