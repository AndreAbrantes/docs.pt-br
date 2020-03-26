---
title: Novidades na acessibilidade do .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4243599f44749e7b38ebe78ca88b8ec2a9390650
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249715"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="26475-102">Novidades na acessibilidade do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="26475-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="26475-103">O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários.</span><span class="sxs-lookup"><span data-stu-id="26475-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="26475-104">As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa.</span><span class="sxs-lookup"><span data-stu-id="26475-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="26475-105">A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis.</span><span class="sxs-lookup"><span data-stu-id="26475-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="26475-106">Opções de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="26475-106">Accessibility switches</span></span>

<span data-ttu-id="26475-107">Configure seu aplicativo para aceitar os recursos de acessibilidade se ele for direcionado ao .NET Framework 4.7 ou a uma versão anterior, mas estiver em execução no .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="26475-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="26475-108">Além disso, configure seu aplicativo para usar recursos herdados (e não aproveitar os recursos de acessibilidade) se ele for direcionado ao .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="26475-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="26475-109">Cada versão do .NET Framework que inclui recursos de acessibilidade tem um switch [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) de acessibilidade [`<runtime>`](../configure-apps/file-schema/runtime/index.md) específico da versão, que você adiciona ao elemento na seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26475-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="26475-110">Estas são as opções compatíveis:</span><span class="sxs-lookup"><span data-stu-id="26475-110">The following are the supported switches:</span></span>

|<span data-ttu-id="26475-111">Versão</span><span class="sxs-lookup"><span data-stu-id="26475-111">Version</span></span>|<span data-ttu-id="26475-112">Opção</span><span class="sxs-lookup"><span data-stu-id="26475-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="26475-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="26475-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="26475-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="26475-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="26475-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="26475-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="26475-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="26475-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="26475-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="26475-117">.NET Framework 4.8</span></span>|<span data-ttu-id="26475-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="26475-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="26475-119">Aproveitando as vantagens das melhorias de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="26475-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="26475-120">As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados ao .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="26475-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="26475-121">Além disso, os aplicativos que visam uma versão anterior do .NET Framework, mas estão sendo executados no .NET Framework 4.7.1 ou posterior, podem [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) optar [`<runtime>`](../configure-apps/file-schema/runtime/index.md) por comportamentos de acessibilidade legados (e, assim, aproveitar as melhorias de acessibilidade) adicionando switches ao elemento na seção do arquivo de configuração do aplicativo e definindo seu valor para `false`.</span><span class="sxs-lookup"><span data-stu-id="26475-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="26475-122">O seguinte exemplo mostra como aceitar as melhorias de acessibilidade introduzidas no .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="26475-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="26475-123">Se você optar por aceitar os recursos de acessibilidade em uma versão posterior do .NET Framework, deverá também aceitar explicitamente os recursos de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26475-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="26475-124">Configurar seu aplicativo para aproveitar as melhorias de acessibilidade no .NET Framework 4.7.1 e 4.7.2 requer o seguinte [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento:</span><span class="sxs-lookup"><span data-stu-id="26475-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="26475-125">Configurar seu aplicativo para aproveitar as melhorias de acessibilidade no .NET Framework 4.7.1, 4.7.2 e 4.8 requer o seguinte [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento:</span><span class="sxs-lookup"><span data-stu-id="26475-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="26475-126">Restaurando o comportamento herdado</span><span class="sxs-lookup"><span data-stu-id="26475-126">Restoring legacy behavior</span></span>

<span data-ttu-id="26475-127">Os aplicativos que têm como alvo as versões do .NET Framework a partir [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do 4.7.1 podem desativar os recursos de acessibilidade adicionando switches ao elemento na [`<runtime>`](../configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração do aplicativo e definindo seu valor para `true`.</span><span class="sxs-lookup"><span data-stu-id="26475-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="26475-128">Por exemplo, a seguinte configuração recusa os recursos de acessibilidade introduzidos no .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="26475-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="26475-129">Novidades na acessibilidade do .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="26475-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="26475-130">O .NET Framework 4.8 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="26475-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="26475-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="26475-132">Fundação de Apresentação do Windows (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="26475-133">Designer de fluxo de trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="26475-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="26475-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-134">Windows Forms</span></span>

<span data-ttu-id="26475-135">No .NET Framework 4.8, o Windows Forms adiciona suporte ao LiveRegions e Eventos de Notificação para muitos controles usados.</span><span class="sxs-lookup"><span data-stu-id="26475-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="26475-136">Ele também adiciona suporte para Dicas de Ferramentas quando um usuário navega para um controle usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="26475-137">**Suporte para UIA LiveRegions em rótulos e StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="26475-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="26475-138">UIA LiveRegions permitem que os desenvolvedores de aplicativos notifiquem os leitores de tela de uma alteração de texto em um controle que está localizado longe do local em que o usuário está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="26475-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="26475-139">Isso é útil, por exemplo, para um controle <xref:System.Windows.Forms.StatusStrip> que mostra um status de conexão.</span><span class="sxs-lookup"><span data-stu-id="26475-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="26475-140">Se a conexão cair e o status mudar, o desenvolvedor deverá notificar o leitor de tela.</span><span class="sxs-lookup"><span data-stu-id="26475-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="26475-141">A partir do .NET Framework 4.8, o Windows Forms implementa UIA LiveRegions nos controles <xref:System.Windows.Forms.Label> e <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="26475-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="26475-142">Por exemplo, o seguinte código usa o para LiveRegion em um controle <xref:System.Windows.Forms.Label> chamado `label1`:</span><span class="sxs-lookup"><span data-stu-id="26475-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="26475-143">O narrador anuncia “Pronto” independentemente de onde o usuário esteja interagindo com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26475-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="26475-144">Você também pode implementar seu <xref:System.Windows.Forms.UserControl> como uma LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="26475-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="26475-145">**Eventos de notificação de UIA**</span><span class="sxs-lookup"><span data-stu-id="26475-145">**UIA notification events**</span></span>

<span data-ttu-id="26475-146">O evento de notificação de UIA, apresentado no Windows 10 Fall Creators Update, permite que seu aplicativo gere um evento UIA, que leva o Narrador a simplesmente fazer um anúncio com base no texto que você forneceu com o evento, sem a necessidade de ter um controle correspondente na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="26475-147">Em alguns cenários, isso é uma maneira direta de melhorar consideravelmente a acessibilidade de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26475-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="26475-148">Também pode ser útil para notificar sobre o progresso de algum processo que pode levar muito tempo.</span><span class="sxs-lookup"><span data-stu-id="26475-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="26475-149">Para obter mais informações sobre eventos de Notificação de UIA, consulte [Seu aplicativo da área de trabalho pode utilizar o novo evento de Notificação de UIA?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="26475-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="26475-150">O exemplo a seguir gera o [Evento de notificação](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="26475-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="26475-151">**Dicas de ferramentas sobre o acesso ao teclado**</span><span class="sxs-lookup"><span data-stu-id="26475-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="26475-152">Em aplicativos destinados ao .NET Framework 4.7.2 e versões anteriores, uma [dica de ferramenta](xref:System.Windows.Forms.ToolTip) de controle só pode ser acionada para exibição ao mover o ponteiro do mouse no controle.</span><span class="sxs-lookup"><span data-stu-id="26475-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="26475-153">A partir do .NET Framework 4.8, um usuário de teclado pode disparar uma dica de ferramenta de controle, concentrando-se no controle usando uma tecla Tab ou teclas de seta, com ou sem teclas modificadoras.</span><span class="sxs-lookup"><span data-stu-id="26475-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="26475-154">Essa melhoria de acessibilidade específica exige uma outra [opção de AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="26475-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="26475-155">A figura a seguir mostrará a dica de ferramenta quando o usuário selecionar um botão com o teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Captura de tela da dica de ferramenta quando o usuário navega para o botão com o teclado.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="26475-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="26475-158">A partir do .NET Framework 4.8, o WPF inclui vários aprimoramentos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="26475-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="26475-159">**Narradores de tela não anunciam mais elementos com visibilidade recolhida ou oculta**</span><span class="sxs-lookup"><span data-stu-id="26475-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="26475-160">Elementos com visibilidade recolhida ou oculta não são mais anunciados pelo leitor de tela.</span><span class="sxs-lookup"><span data-stu-id="26475-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="26475-161">As interfaces do usuário que contêm elementos com uma Visibilidade de <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> ou <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> poderão ser adulteradas pelos leitores de tela se forem apresentadas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="26475-162">A partir do .NET Framework 4.8, o WPF não inclui mais elementos recolhidos ou ocultos na Exibição de Controle da árvore do UIAutomation. Portanto, os leitores de tela não podem anunciar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="26475-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="26475-163">**Propriedade SelectionTextBrush para uso com a seleção de texto não baseada em Adorno**</span><span class="sxs-lookup"><span data-stu-id="26475-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="26475-164">No .NET Framework 4.7.2, o WPF adicionou a capacidade de desenhar <xref:System.Windows.Controls.TextBox> e a seleção de texto <xref:System.Windows.Controls.PasswordBox> sem usar a camada de Adorno.</span><span class="sxs-lookup"><span data-stu-id="26475-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="26475-165">A cor de primeiro plano do texto selecionado nesse cenário foi determinada pelo <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="26475-166">O .NET framework 4.8 adiciona uma nova propriedade, `SelectionTextBrush`, que permite que os desenvolvedores selecionem o pincel específico para o texto selecionado quando usar a seleção de texto não baseada em Adorno.</span><span class="sxs-lookup"><span data-stu-id="26475-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="26475-167">Esta propriedade funciona apenas nos controles derivados de <xref:System.Windows.Controls.Primitives.TextBoxBase> e o controle <xref:System.Windows.Controls.PasswordBox> em aplicativos WPF com seleção de texto não baseada em Adorno habilitada.</span><span class="sxs-lookup"><span data-stu-id="26475-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="26475-168">Ela não funciona no controle <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="26475-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="26475-169">Se a seleção de texto não baseada em Adorno não estiver habilitada, essa propriedade será ignorada.</span><span class="sxs-lookup"><span data-stu-id="26475-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="26475-170">Para usar essa propriedade, basta adicioná-la ao seu código XAML e usar a associação ou o pincel adequado.</span><span class="sxs-lookup"><span data-stu-id="26475-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="26475-171">A seleção de texto resultante tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="26475-171">The resulting text selection looks like this:</span></span>

![Captura de tela do aplicativo em execução com as palavras Hello World selecionadas.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="26475-173">Você pode combinar o uso das propriedades `SelectionBrush` e `SelectionTextBrush` para gerar qualquer combinação de plano de fundo e cor de primeiro plano que julgar adequada.</span><span class="sxs-lookup"><span data-stu-id="26475-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="26475-174">**Suporte para a propriedade ControllerFor do UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="26475-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="26475-175">A propriedade `ControllerFor` do UIAutomation retorna uma matriz de elementos de automação manipulados pelo elemento de automação que dá suporte a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="26475-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="26475-176">Essa propriedade normalmente é usada para acessibilidade de sugestão automática.</span><span class="sxs-lookup"><span data-stu-id="26475-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="26475-177">`ControllerFor` é usado quando um elemento de automação afeta um ou mais segmentos de interface do usuário do aplicativo ou da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="26475-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="26475-178">Caso contrário, é difícil associar o impacto da operação de controle com elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="26475-179">Este recurso adiciona a capacidade de controles para fornecer um valor para a propriedade `ControllerFor`.</span><span class="sxs-lookup"><span data-stu-id="26475-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="26475-180">O .NET framework 4.8 adiciona um novo método virtual, o <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-181">Para fornecer um valor para a propriedade `ControllerFor`, basta substituir este método e retornar um `List<AutomationPeer>` para os controles manipulados por este <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="26475-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="26475-182">**Dicas de ferramentas sobre acesso ao teclado**</span><span class="sxs-lookup"><span data-stu-id="26475-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="26475-183">No .NET Framework 4.7.2 e versões anteriores, as dicas de ferramentas são exibidas somente quando o usuário passar o cursor do mouse sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="26475-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="26475-184">No .NET Framework 4.8, as dicas de ferramentas também são exibidas no foco do teclado, bem como por meio de um atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="26475-185">Para habilitar esse recurso, um aplicativo precisa direcionar o .NET Framework 4.8 ou aceitar ao usar as opções `Switch.UseLegacyAccessibilityFeatures.3` e `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="26475-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="26475-186">Veja a seguir um arquivo de exemplo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="26475-186">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="26475-187">Depois de habilitados, todos os controles que contêm uma dica de ferramenta vão exibi-la depois que o controle receber o foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="26475-188">A dica de ferramenta pode ser ignorada com o tempo ou quando o foco do teclado mudar.</span><span class="sxs-lookup"><span data-stu-id="26475-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="26475-189">Os usuários também podem ignorar a dica de ferramenta manualmente usando um novo atalho de teclado, Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="26475-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="26475-190">Depois que a dica de ferramenta for ignorada, ela poderá ser exibida novamente usando o mesmo atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="26475-191">As [dicas de ferramentas da faixa de opções](xref:System.Windows.Controls.Ribbon.RibbonToolTip) nos controles <xref:System.Windows.Controls.Ribbon.Ribbon> não serão exibidas no foco do teclado. São exibidas somente por meio do atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="26475-192">**Adicionado suporte para propriedades SizeOfSet e PositionInSet do UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="26475-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="26475-193">O Windows 10 introduziu duas novas propriedades do UIAutomation, `SizeOfSet` e `PositionInSet`, que são usadas por aplicativos para descrever a contagem de itens em um conjunto.</span><span class="sxs-lookup"><span data-stu-id="26475-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="26475-194">Aplicativos de cliente do UIAutomation, como leitores de tela podem, então, consultar um aplicativo para essas propriedades e anunciar uma representação precisa da interface de usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26475-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="26475-195">A partir do .NET Framework 4.8, o WPF expõe essas duas propriedades para o UIAutomation em aplicativos do WPF.</span><span class="sxs-lookup"><span data-stu-id="26475-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="26475-196">Isso pode ser feito de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="26475-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="26475-197">Usando propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="26475-197">By using dependency properties.</span></span>

  <span data-ttu-id="26475-198">O WPF adiciona duas novas propriedades de dependência, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-199">Um desenvolvedor pode usar o XAML para definir seus valores:</span><span class="sxs-lookup"><span data-stu-id="26475-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="26475-200">Ao substituir métodos virtuais do AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="26475-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="26475-201">Os métodos virtuais <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> foram adicionados à classe AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="26475-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="26475-202">Um desenvolvedor pode fornecer valores para `SizeOfSet` e `PositionInSet` por meio da substituição desses métodos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="26475-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="26475-203">Além disso, os itens nas instâncias <xref:System.Windows.Controls.ItemsControl> fornecem um valor para essas propriedades automaticamente sem ação adicional do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="26475-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="26475-204">Se um <xref:System.Windows.Controls.ItemsControl> for agrupado, a coleção de grupos será representada como um conjunto e cada grupo será contado como um conjunto separado, com cada item dentro desse grupo fornecendo sua posição dentro desse grupo, bem como o tamanho do grupo.</span><span class="sxs-lookup"><span data-stu-id="26475-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="26475-205">Valores automáticos não são afetados pela virtualização.</span><span class="sxs-lookup"><span data-stu-id="26475-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="26475-206">Mesmo que um item não seja percebido, ele ainda é contado para o tamanho total do conjunto e afeta a posição no conjunto de seus itens irmãos.</span><span class="sxs-lookup"><span data-stu-id="26475-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="26475-207">Valores automáticos serão fornecidos apenas se o aplicativo for destinado ao .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="26475-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="26475-208">Para aplicativos que se destinam a uma versão anterior do .NET Framework, você pode definir a `Switch.UseLegacyAccessibilityFeatures.3` [opção AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), conforme mostrado no seguinte arquivo App.config:</span><span class="sxs-lookup"><span data-stu-id="26475-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="26475-209">Designer de fluxo de trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="26475-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="26475-210">O designer de fluxo de trabalho inclui as seguintes alterações no .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="26475-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="26475-211">Os usuários que utilizam o Narrador verão melhorias em rótulos de caso do FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="26475-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="26475-212">Os usuários que utilizam o Narrador verão melhorias em descrições de botão.</span><span class="sxs-lookup"><span data-stu-id="26475-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="26475-213">Usuários que escolherem temas de Alto Contraste verão melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.</span><span class="sxs-lookup"><span data-stu-id="26475-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="26475-214">Se o seu aplicativo for destinado ao .NET Framework 4.7.2 ou uma versão anterior, você poderá aceitar essas alterações, definindo a `Switch.UseLegacyAccessibilityFeatures.3` [opção de AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) para `false` no seu arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26475-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="26475-215">Para obter mais informações, consulte a seção [Aproveitando os aprimoramentos de acessibilidade](#taking-advantage-of-accessibility-enhancements) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="26475-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="26475-216">Novidades na acessibilidade do .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="26475-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="26475-217">O .NET Framework 4.7.2 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="26475-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="26475-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="26475-219">Fundação de Apresentação do Windows (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="26475-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-220">Windows Forms</span></span>

<span data-ttu-id="26475-221">**Cores definidas pelo sistema operacional em temas de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="26475-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="26475-222">Começando no .NET Framework 4.7.2, o Windows Forms usa cores definidas pelo sistema operacional em temas de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="26475-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="26475-223">Isso afeta os seguintes controles:</span><span class="sxs-lookup"><span data-stu-id="26475-223">This affects the following controls:</span></span>

- <span data-ttu-id="26475-224">A seta suspensa do controle <xref:System.Windows.Forms.ToolStripDropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="26475-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="26475-225">Os controles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com <xref:System.Windows.Forms.ButtonBase.FlatStyle> definido como <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-226">Anteriormente, as cores de texto e da tela de fundo selecionadas não eram contrastantes e eram difíceis de serem lidas.</span><span class="sxs-lookup"><span data-stu-id="26475-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="26475-227">Os controles contidos em uma <xref:System.Windows.Forms.GroupBox> que tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="26475-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="26475-228">Os controles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> e <xref:System.Windows.Forms.ToolStripDropDownButton>, que têm uma taxa maior de contraste de luminosidade no Modo de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="26475-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="26475-229">A propriedade <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> do <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="26475-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="26475-230">**Melhorias do Narrador**</span><span class="sxs-lookup"><span data-stu-id="26475-230">**Narrator improvements**</span></span>

<span data-ttu-id="26475-231">A partir do .NET Framework 4.7.2, o suporte ao Narrador é aprimorado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="26475-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="26475-232">Ele anuncia o valor da propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quando anuncia o texto de um <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="26475-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="26475-233">Ele indica quando um <xref:System.Windows.Forms.ToolStripMenuItem> tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="26475-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="26475-234">Ele fornece comentários sobre o estado de uma caixa de seleção quando a propriedade <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="26475-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="26475-235">A ordem de foco do Modo de Verificação do Narrador é consistente com a ordem visual dos controles na janela de diálogo de download do ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="26475-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="26475-236">**Melhorias de DataGridView**</span><span class="sxs-lookup"><span data-stu-id="26475-236">**DataGridView improvements**</span></span>

<span data-ttu-id="26475-237">A partir do .NET Framework 4.7.2, o controle <xref:System.Windows.Forms.DataGridView> introduziu as seguintes melhorias de acessibilidade:</span><span class="sxs-lookup"><span data-stu-id="26475-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="26475-238">As linhas podem ser classificadas com o teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="26475-239">Um usuário pode usar a tecla F3 para classificar pela coluna atual.</span><span class="sxs-lookup"><span data-stu-id="26475-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="26475-240">Quando o <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> é definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, o cabeçalho da coluna muda de cor para indicar a coluna atual, à medida que o usuário pressiona Tab para percorrer as células na linha atual.</span><span class="sxs-lookup"><span data-stu-id="26475-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="26475-241">A propriedade <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> de um <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> retorna o controle pai correto.</span><span class="sxs-lookup"><span data-stu-id="26475-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="26475-242">**Pistas visuais melhoradas**</span><span class="sxs-lookup"><span data-stu-id="26475-242">**Improved visual cues**</span></span>

- <span data-ttu-id="26475-243">Os controles <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com uma propriedade <xref:System.Windows.Forms.ButtonBase.Text> vazia exibem um indicador de foco quando recebem o foco.</span><span class="sxs-lookup"><span data-stu-id="26475-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="26475-244">**Melhoria no suporte à grade de propriedade**</span><span class="sxs-lookup"><span data-stu-id="26475-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="26475-245">Os elementos filhos do controle <xref:System.Windows.Forms.PropertyGrid> agora retornam um `true` para a propriedade <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> somente quando um elemento PropertyGrid está habilitado.</span><span class="sxs-lookup"><span data-stu-id="26475-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="26475-246">Os elementos filho do controle <xref:System.Windows.Forms.PropertyGrid> retornam um `false` para a propriedade <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> somente quando um elemento PropertyGrid pode ser alterado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="26475-247">**Melhoria na navegação por teclado**</span><span class="sxs-lookup"><span data-stu-id="26475-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="26475-248">O controle <xref:System.Windows.Forms.ToolStripButton> permite o foco quando contido em um <xref:System.Windows.Forms.ToolStripPanel> que tem a propriedade <xref:System.Windows.Forms.ToolStripPanel.TabStop> definida como `true`</span><span class="sxs-lookup"><span data-stu-id="26475-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="26475-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="26475-250">**Alterações nos controles CheckBox e RadioButton**</span><span class="sxs-lookup"><span data-stu-id="26475-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="26475-251">No .NET Framework 4.7.1 e nas versões anteriores, os controles <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> e <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> do WPF têm visuais de foco inconsistentes e, nos temas Clássico e de Alto Contraste, têm visuais de foco incorretos.</span><span class="sxs-lookup"><span data-stu-id="26475-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="26475-252">Esses problemas ocorrem quando os controles não têm nenhum conjunto de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="26475-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="26475-253">Isso pode dificultar a transição entre os temas e deixar o visual de foco confuso.</span><span class="sxs-lookup"><span data-stu-id="26475-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="26475-254">No .NET Framework 4.7.2, agora esses visuais são mais consistentes entre os temas e mais facilmente visíveis nos temas Clássico e de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="26475-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="26475-255">**Controles do WinForms hospedados em um aplicativo WPF**</span><span class="sxs-lookup"><span data-stu-id="26475-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="26475-256">Para controles do WinForms hospedados em um aplicativo do WPF no .NET Framework 4.7.1 e versões anteriores, os usuários não poderão sair da guia da camada do WinForms se o primeiro ou o último controle da camada for o controle <xref:System.Windows.Forms.Integration.ElementHost> do WPF.</span><span class="sxs-lookup"><span data-stu-id="26475-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="26475-257">No .NET Framework 4.7.2, os usuários agora podem sair da guia da camada do WinForms.</span><span class="sxs-lookup"><span data-stu-id="26475-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="26475-258">No entanto, os aplicativos automatizados que se baseiam em foco e que nunca são escapados da camada do WinForms podem deixar de funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="26475-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="26475-259">Novidades na acessibilidade do .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="26475-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="26475-260">O .NET Framework 4.7.1 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="26475-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="26475-261">Fundação de Apresentação do Windows (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="26475-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="26475-263">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="26475-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="26475-264">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="26475-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="26475-265">Windows Workflow Foundation (WF) Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="26475-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="26475-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="26475-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="26475-267">**Melhorias do leitor de tela**</span><span class="sxs-lookup"><span data-stu-id="26475-267">**Screen reader improvements**</span></span>

<span data-ttu-id="26475-268">Se as melhorias de acessibilidade estiverem habilitadas, o .NET Framework 4.7.1 incluirá as seguintes melhorias que afetam os leitores de tela:</span><span class="sxs-lookup"><span data-stu-id="26475-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="26475-269">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.Expander> foram divulgados pelos leitores de tela como botões.</span><span class="sxs-lookup"><span data-stu-id="26475-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="26475-270">A partir do .NET Framework 4.7.1, eles são corretamente divulgados como grupos expansíveis/recolhíveis.</span><span class="sxs-lookup"><span data-stu-id="26475-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="26475-271">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.DataGridCell> foram divulgados pelos leitores de tela como “personalizados”.</span><span class="sxs-lookup"><span data-stu-id="26475-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="26475-272">A partir do .NET Framework 4.7.1, agora eles são corretamente divulgados como célula de grade de dados (localizada).</span><span class="sxs-lookup"><span data-stu-id="26475-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="26475-273">A partir do .NET Framework 4.7.1, os leitores de tela divulgam o nome de uma <xref:System.Windows.Controls.ComboBox> editável.</span><span class="sxs-lookup"><span data-stu-id="26475-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="26475-274">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.PasswordBox> eram divulgados como “nenhum item em exibição” ou, de outro modo, apresentavam um comportamento incorreto.</span><span class="sxs-lookup"><span data-stu-id="26475-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="26475-275">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="26475-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="26475-276">**Suporte a UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="26475-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="26475-277">Leitores de tela, como o Narrador, ajudam as pessoas a ler o conteúdo da interface do usuário de um aplicativo, normalmente, pela saída de conversão de texto em fala do conteúdo da interface do usuário que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="26475-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="26475-278">No entanto, se um elemento da interface do usuário for alterado e não tiver o foco, o usuário poderá não ser notificado e perder informações importantes.</span><span class="sxs-lookup"><span data-stu-id="26475-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="26475-279">As regiões dinâmicas pretendem resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="26475-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="26475-280">Um desenvolvedor pode usá-las para informar o leitor de tela ou qualquer outro cliente de UIAutomation de que foi feita uma alteração importante em um elemento da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="26475-281">Em seguida, o leitor de tela pode decidir como e quando informar o usuário dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="26475-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="26475-282">Para dar suporte a regiões dinâmicas, as seguintes APIs foram adicionadas ao WPF:</span><span class="sxs-lookup"><span data-stu-id="26475-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="26475-283">Os campos <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, que identificam a propriedade **LiveSetting** e o evento **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="26475-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="26475-284">Eles podem ser definidos com XAML.</span><span class="sxs-lookup"><span data-stu-id="26475-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="26475-285">A propriedade anexada **AutomationProperties.LiveSetting**, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="26475-286">A propriedade <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, que identifica a propriedade anexada **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="26475-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="26475-287">O método <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, que pode ser substituído para fornecer um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="26475-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="26475-288">Os métodos <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, que obtêm e definem um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="26475-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="26475-289">A enumeração <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, que define os seguintes possíveis valores de **LiveSetting**:</span><span class="sxs-lookup"><span data-stu-id="26475-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="26475-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-291">O elemento não envia notificações se o conteúdo da região dinâmica foi alterado.</span><span class="sxs-lookup"><span data-stu-id="26475-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="26475-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-293">O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="26475-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="26475-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26475-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="26475-295">O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="26475-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="26475-296">Crie uma LiveRegion configurar a propriedade **AutomationProperties.LiveSetting** no elemento de interesse, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="26475-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="26475-297">Quando os dados da região dinâmica forem alterados e você precisar informar um leitor de tela, acione um evento explicitamente, conforme mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="26475-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="26475-298">**Alto contraste**</span><span class="sxs-lookup"><span data-stu-id="26475-298">**High contrast**</span></span>

<span data-ttu-id="26475-299">A partir do .NET Framework 4.7.1, foram feitas melhorias de alto contraste em vários controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="26475-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="26475-300">Agora eles estão visíveis quando o tema <xref:System.Windows.SystemParameters.HighContrast%2A> é definido.</span><span class="sxs-lookup"><span data-stu-id="26475-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="26475-301">Eles incluem:</span><span class="sxs-lookup"><span data-stu-id="26475-301">These include:</span></span>

- <span data-ttu-id="26475-302">Controle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="26475-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="26475-303">O visual de foco do controle <xref:System.Windows.Controls.Expander> agora está visível.</span><span class="sxs-lookup"><span data-stu-id="26475-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="26475-304">Os visuais de teclado dos controles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.RadioButton> também estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="26475-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="26475-305">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-305">For example:</span></span>

  <span data-ttu-id="26475-306">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-306">Before:</span></span>

  ![Captura de tela do controle de expansor com foco e sem foco visual.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="26475-308">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-308">After:</span></span>

  ![Captura de tela do controle de expansor com foco mostrando uma linha pontilhada em torno do texto do controle.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="26475-310">Controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="26475-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="26475-311">O texto nos controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> agora é de visualização mais fácil quando selecionado em temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="26475-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="26475-312">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-312">For example:</span></span>

  <span data-ttu-id="26475-313">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-313">Before:</span></span>

  ![Captura de tela de rádio e botões de verificação com pouca visibilidade de texto em temas de alto contraste.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="26475-315">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-315">After:</span></span>

  ![Captura de tela de rádio e botões de verificação com melhor visibilidade de texto em temas de alto contraste.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="26475-317">Controle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="26475-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="26475-318">A partir do .NET Framework 4.7.1, a borda de um controle <xref:System.Windows.Controls.ComboBox> desabilitado é da mesma cor do texto desabilitado.</span><span class="sxs-lookup"><span data-stu-id="26475-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="26475-319">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-319">For example:</span></span>

  <span data-ttu-id="26475-320">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-320">Before:</span></span>

  ![Captura de tela de um ComboBox desativado com texto de borda e controle em cores diferentes.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="26475-322">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-322">After:</span></span>

  ![Captura de tela de um ComboBox desativado com borda da mesma cor do texto de controle.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="26475-324">Além disso, os botões desabilitados e com foco usam a cor de tema correta.</span><span class="sxs-lookup"><span data-stu-id="26475-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="26475-325">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-325">Before:</span></span>

  ![Captura de tela de um botão preto com texto cinza dizendo Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="26475-327">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-327">After:</span></span>

  ![Captura de tela de um botão azul com texto preto dizendo Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="26475-329">Por fim, no .NET Framework 4.7 e em versões anteriores, a configuração do estilo de um controle <xref:System.Windows.Controls.ComboBox> como `Toolbar.ComboBoxStyleKey` fazia com que a seta suspensa ficasse invisível.</span><span class="sxs-lookup"><span data-stu-id="26475-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="26475-330">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="26475-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="26475-331">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-331">For example:</span></span>

  <span data-ttu-id="26475-332">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-332">Before:</span></span>

  ![Captura de tela de um controle ComboBox com uma seta baixa invisível.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="26475-334">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-334">After:</span></span>

  ![Captura de tela de um controle ComBoxBox exibindo a seta para baixo.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="26475-336">Controle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="26475-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="26475-337">A partir do .NET Framework 4.7.1, a seta do indicador de classificação nos controles <xref:System.Windows.Controls.DataGrid> agora usa as cores de tema corretas.</span><span class="sxs-lookup"><span data-stu-id="26475-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="26475-338">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-338">For example:</span></span>

  <span data-ttu-id="26475-339">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-339">Before:</span></span>

  ![Captura de tela da seta indicadora de tipo antes de melhorias.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="26475-341">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-341">After:</span></span>

  ![Captura de tela da seta indicadora de tipo após melhorias.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="26475-343">Além disso, no .NET Framework 4.7 e em versões anteriores, o estilo de link padrão era alterado para uma cor incorreta ao passar o mouse nos modos de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="26475-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="26475-344">Isso é resolvido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="26475-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="26475-345">Da mesma forma, as colunas da caixa de seleção <xref:System.Windows.Controls.DataGrid> usam as cores esperadas para os comentários do foco de teclado a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="26475-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="26475-346">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-346">Before:</span></span>

  ![Captura de tela de um link dizendo Click Me!](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="26475-349">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-349">After:</span></span>

  ![Captura de tela de um link dizendo Click Me!](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="26475-352">Para obter mais informações sobre as melhorias de acessibilidade do WPF no .NET Framework 4.7.1, consulte [Melhorias de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="26475-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="26475-353">Melhorias de acessibilidade do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26475-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="26475-354">No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.</span><span class="sxs-lookup"><span data-stu-id="26475-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="26475-355">**Vídeo aprimorado no modo de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="26475-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="26475-356">Do .NET Framework 4.7.1 em diante, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="26475-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="26475-357">O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="26475-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="26475-358">Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10, de modo que ela fique parecida com a seguinte:</span><span class="sxs-lookup"><span data-stu-id="26475-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="26475-359">Alguns exemplos de alterações de alto contraste incluem:</span><span class="sxs-lookup"><span data-stu-id="26475-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="26475-360">Marcas de seleção em itens <xref:System.Windows.Forms.MenuStrip> são mais fáceis de serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="26475-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="26475-361">Quando selecionados, os itens <xref:System.Windows.Forms.MenuStrip> desabilitados são mais fáceis de serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="26475-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="26475-362">O texto em um controle <xref:System.Windows.Forms.Button> selecionado contrasta com a cor da seleção.</span><span class="sxs-lookup"><span data-stu-id="26475-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="26475-363">O texto desabilitado é mais fácil de ser lido.</span><span class="sxs-lookup"><span data-stu-id="26475-363">Disabled text is easier to read.</span></span> <span data-ttu-id="26475-364">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="26475-364">For example:</span></span>

  <span data-ttu-id="26475-365">Antes:</span><span class="sxs-lookup"><span data-stu-id="26475-365">Before:</span></span>

  ![Captura de tela de um aplicativo que usa diferentes controles rodando no modo de alto contraste antes de melhorias de acessibilidade.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="26475-367">Após:</span><span class="sxs-lookup"><span data-stu-id="26475-367">After:</span></span>

  ![Captura de tela de um aplicativo que usa diferentes controles em execução no modo de alto contraste após melhorias de acessibilidade.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="26475-369">Melhorias de alto contraste na caixa de diálogo Exceção de Thread.</span><span class="sxs-lookup"><span data-stu-id="26475-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="26475-370">**Melhor suporte ao Narrador**</span><span class="sxs-lookup"><span data-stu-id="26475-370">**Improved Narrator support**</span></span>

<span data-ttu-id="26475-371">O Windows Forms no .NET Framework 4.7.1 inclui as seguintes melhorias de acessibilidade para o Narrador:</span><span class="sxs-lookup"><span data-stu-id="26475-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="26475-372">O controle <xref:System.Windows.Forms.MonthCalendar> pode ser acessado pelo Narrador, bem como por outras ferramentas de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="26475-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="26475-373">O controle <xref:System.Windows.Forms.CheckedListBox> notifica o Narrador quando o estado de seleção do item foi alterado, para que o usuário seja notificado de que ele alterou o valor de um item de lista.</span><span class="sxs-lookup"><span data-stu-id="26475-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="26475-374">O controle <xref:System.Windows.Forms.DataGridViewCell> relata o status somente leitura correto para o Narrador.</span><span class="sxs-lookup"><span data-stu-id="26475-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="26475-375">O Narrador agora pode ler o texto <xref:System.Windows.Forms.ToolStripMenuItem> desabilitado, enquanto, anteriormente, ele ignorava itens de menu desabilitados.</span><span class="sxs-lookup"><span data-stu-id="26475-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="26475-376">**Suporte aprimorado para padrões de acessibilidade de UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="26475-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="26475-377">A partir do .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem utilizar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms.</span><span class="sxs-lookup"><span data-stu-id="26475-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="26475-378">Essas melhorias de acessibilidade incluem:</span><span class="sxs-lookup"><span data-stu-id="26475-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="26475-379">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora dão suporte ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="26475-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="26475-380">O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora dá suporte ao [padrão alternar](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="26475-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="26475-381">O controle <xref:System.Windows.Forms.ToolStripItem> dá suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> e ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="26475-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="26475-382">Os controles <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> dão suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="26475-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="26475-383">**Melhor experiência do navegador de propriedades**</span><span class="sxs-lookup"><span data-stu-id="26475-383">**Improved property browser experience**</span></span>

<span data-ttu-id="26475-384">A partir do .NET Framework 4.7.1, o Windows Forms inclui:</span><span class="sxs-lookup"><span data-stu-id="26475-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="26475-385">Melhor navegação de teclado por meio das várias janelas de seleção suspensa.</span><span class="sxs-lookup"><span data-stu-id="26475-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="26475-386">Uma redução de paradas de tabulação desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="26475-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="26475-387">Melhor relatório de tipos de controle.</span><span class="sxs-lookup"><span data-stu-id="26475-387">Better reporting of control types.</span></span>
- <span data-ttu-id="26475-388">Melhor comportamento do Narrador.</span><span class="sxs-lookup"><span data-stu-id="26475-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="26475-389">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="26475-389">ASP.NET web controls</span></span>

<span data-ttu-id="26475-390">Começando com o .NET Framework 4.7.1 e o Visual Studio 2017 versão 15.3, ASP.NET melhora a forma como ASP.NET controles web funcionam com tecnologia de acessibilidade no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26475-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="26475-391">As alterações incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="26475-391">Changes include the following:</span></span>

- <span data-ttu-id="26475-392">Alterações para implementar padrões de acessibilidade de interface de interface de interface de interface ausentes nos controles, como a caixa de diálogo **Adicionar campo** no assistente **'Exibir detalhes'** ou a caixa de diálogo **Configurar listView** do assistente **ListView.**</span><span class="sxs-lookup"><span data-stu-id="26475-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="26475-393">Alterações para melhorar o display no modo De Alto Contraste, como o **Data Pager Fields Editor**.</span><span class="sxs-lookup"><span data-stu-id="26475-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="26475-394">Alterações para melhorar as experiências de navegação do teclado para controles, como a caixa de diálogo **Campos** de campos de **edição** no controle DataPager, a caixa de diálogo **Configurar objetoContexto** ou a caixa de diálogo **Configurar seleção** de dados do assistente Configurar origem de **dados.**</span><span class="sxs-lookup"><span data-stu-id="26475-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="26475-395">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="26475-395">.NET SDK Tools</span></span>

<span data-ttu-id="26475-396">A [Ferramenta Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) e a [Ferramenta Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) foram aprimoradas com a correção de problemas variados de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="26475-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="26475-397">A maioria eram problemas pequenos, como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="26475-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="26475-398">Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão essas ferramentas de SDK mais acessíveis.</span><span class="sxs-lookup"><span data-stu-id="26475-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="26475-399">Essas melhorias alteram alguns comportamentos anteriores, como a ordem de foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="26475-400">Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="26475-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="26475-401">As alterações de acessibilidade no Designer de Fluxo de Trabalho incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="26475-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="26475-402">A ordem de tabulação é alterada para a esquerda para a direita e de cima para baixo em alguns controles:</span><span class="sxs-lookup"><span data-stu-id="26475-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="26475-403">A janela de inicialização de correlação para definir dados de correlação para a atividade <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="26475-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="26475-404">A janela de definição de conteúdo para as atividades <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="26475-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="26475-405">Mais funções estão disponíveis por meio do teclado:</span><span class="sxs-lookup"><span data-stu-id="26475-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="26475-406">Ao editar as propriedades de uma atividade, grupos de propriedades podem ser recolhidos pelo teclado na primeira vez em que são colocados em foco.</span><span class="sxs-lookup"><span data-stu-id="26475-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="26475-407">Ícones de aviso podem ser acessados por teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="26475-408">O botão **Mais Propriedades** na janela **Propriedades** pode ser acessado pelo teclado.</span><span class="sxs-lookup"><span data-stu-id="26475-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="26475-409">Usuários do teclado podem acessar os itens de cabeçalho nos painéis **Argumentos** e **Variáveis** do Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="26475-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="26475-410">Melhor visibilidade de itens com foco, como ao:</span><span class="sxs-lookup"><span data-stu-id="26475-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="26475-411">Adicionar linhas às grades de dados usadas pelo Designer de Fluxo de Trabalho e por designers de atividades.</span><span class="sxs-lookup"><span data-stu-id="26475-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="26475-412">Percorrer campos nas atividades <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="26475-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="26475-413">Definir valores padrão para variáveis ou argumentos</span><span class="sxs-lookup"><span data-stu-id="26475-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="26475-414">Agora, leitores de tela podem reconhecer corretamente:</span><span class="sxs-lookup"><span data-stu-id="26475-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="26475-415">Pontos de interrupção definidos no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="26475-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="26475-416">As atividades <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> e <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="26475-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="26475-417">O conteúdo da atividade <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="26475-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="26475-418">O Tipo de Destino da atividade <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="26475-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="26475-419">A caixa de combinação Exceção e a seção Finalmente na atividade <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="26475-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="26475-420">A caixa de combinação Tipo de Mensagem, o divisor na janela Adicionar Inicializadores de Correlação, a janela Definição de Conteúdo e a janela de Definição de CorrelatesOn nas atividades de mensagens (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="26475-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="26475-421">Transições de máquinas de estado e destinos de transição.</span><span class="sxs-lookup"><span data-stu-id="26475-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="26475-422">Anotações e conectores em atividades <xref:System.Activities.Statements.FlowDecision>.</span><span class="sxs-lookup"><span data-stu-id="26475-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="26475-423">Os menus de contexto (clique com o botão direito do mouse) para atividades.</span><span class="sxs-lookup"><span data-stu-id="26475-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="26475-424">Os editores de valor de propriedade, o botão Limpar Pesquisa, os botões de classificação Por Categoria e Ordem Alfabética e a caixa de diálogo Editor de Expressão na grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="26475-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="26475-425">A porcentagem de zoom no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="26475-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="26475-426">O separador nas atividades <xref:System.Activities.Statements.Parallel> e <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="26475-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="26475-427">A atividade <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="26475-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="26475-428">A janela Selecionar Tipos para atividades de dicionário (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` etc.).</span><span class="sxs-lookup"><span data-stu-id="26475-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="26475-429">A janela Procurar e Selecionar um Tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="26475-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="26475-430">Trilhas de navegação no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="26475-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="26475-431">Usuários que escolherem temas de Alto Contraste verão muitas melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.</span><span class="sxs-lookup"><span data-stu-id="26475-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="26475-432">Confira também</span><span class="sxs-lookup"><span data-stu-id="26475-432">See also</span></span>

- [<span data-ttu-id="26475-433">Novidades no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="26475-433">What's new in the .NET Framework</span></span>](index.md)
