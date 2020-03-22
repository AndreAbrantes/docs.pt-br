---
title: criar ouvintes de log personalizados
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353621"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="9b6bb-102">Instruções passo a passo: criando ouvintes de log personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="9b6bb-103">Estas instruções passo a passo demonstram como criar um ouvinte de log personalizado e configurá-lo para ouvir a saída do objeto `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="9b6bb-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="9b6bb-104">Getting Started</span></span>

<span data-ttu-id="9b6bb-105">Ouvintes de log devem herdar da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="9b6bb-106">Para criar o ouvinte</span><span class="sxs-lookup"><span data-stu-id="9b6bb-106">To create the listener</span></span>

- <span data-ttu-id="9b6bb-107">Em seu aplicativo, crie uma classe denominada `SimpleListener` que herda de <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="9b6bb-108">Os métodos <xref:System.Diagnostics.TraceListener.Write%2A> e <xref:System.Diagnostics.TraceListener.WriteLine%2A>, exigidos pela classe base, chamam `MsgBox` para exibir sua entrada.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="9b6bb-109">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> é aplicado aos métodos <xref:System.Diagnostics.TraceListener.Write%2A> e <xref:System.Diagnostics.TraceListener.WriteLine%2A> para que seus atributos coincidam com os métodos da classe base.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="9b6bb-110">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> permite que o host que executa o código determine que o código expõe a sincronização de proteção de host.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b6bb-111">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> é eficaz somente em aplicativos não gerenciados que hospedam o Common Language Runtime e implementam a proteção de host, como o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="9b6bb-112">Para garantir que o `My.Application.Log` use o ouvinte de log, você deve nomear fortemente o assembly que contém o ouvinte de log.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="9b6bb-113">O procedimento seguinte fornece algumas etapas simples para criar um assembly de ouvinte de log de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="9b6bb-114">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="9b6bb-115">Para nomear fortemente o assembly de ouvinte de log</span><span class="sxs-lookup"><span data-stu-id="9b6bb-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="9b6bb-116">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9b6bb-117">No menu **Projeto,** escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="9b6bb-118">Clique na guia **Assinatura** .</span><span class="sxs-lookup"><span data-stu-id="9b6bb-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="9b6bb-119">Marque a caixa **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="9b6bb-120">Selecione \*\* \<Nova>\*\* na lista de desímpara de arquivo de **chave de nome forte.**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="9b6bb-121">A caixa de diálogo **Criar Chave de Nome Forte** é aberta.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="9b6bb-122">Forneça um nome para o arquivo de chaves na caixa **Nome de arquivo de chaves**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="9b6bb-123">Digite uma senha nas caixas **Digite a senha** e **Confirmar senha** caixas.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="9b6bb-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-124">Click **OK**.</span></span>

8. <span data-ttu-id="9b6bb-125">Recompile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="9b6bb-126">Adicionando o ouvinte</span><span class="sxs-lookup"><span data-stu-id="9b6bb-126">Adding the Listener</span></span>

<span data-ttu-id="9b6bb-127">Agora que o assembly tem um nome forte, você precisa determinar o nome forte do ouvinte para que `My.Application.Log` use seu ouvinte de log.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="9b6bb-128">O formato de um tipo de nome forte é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="9b6bb-129">\<nome do tipo>, \<nome do assembly>, \<número de versão>, \<cultura>, \<nome forte></span><span class="sxs-lookup"><span data-stu-id="9b6bb-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="9b6bb-130">Para determinar o nome forte do ouvinte</span><span class="sxs-lookup"><span data-stu-id="9b6bb-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="9b6bb-131">O código a seguir mostra como determinar o tipo de nome forte de `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="9b6bb-132">O nome forte do tipo depende de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="9b6bb-133">Com o nome forte, você pode adicionar o ouvinte à coleção de ouvintes de log `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="9b6bb-134">Para adicionar o ouvinte a My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="9b6bb-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="9b6bb-135">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="9b6bb-136">-ou-</span><span class="sxs-lookup"><span data-stu-id="9b6bb-136">-or-</span></span>

     <span data-ttu-id="9b6bb-137">Se houver um arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="9b6bb-138">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="9b6bb-139">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="9b6bb-140">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-140">Click **Add**.</span></span>

2. <span data-ttu-id="9b6bb-141">Localize a seção `<listeners>`, na seção `<source>` com o `name` atributo "DefaultSource", localizado na seção `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="9b6bb-142">A seção `<sources>` está localizada na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="9b6bb-143">Adicione esse elemento à seção `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="9b6bb-144">Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="9b6bb-145">Adicione esse elemento a essa seção `<sharedListeners>`:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="9b6bb-146">Altere o valor de `SimpleLogStrongName` para ser o nome forte do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b6bb-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b6bb-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="9b6bb-148">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="9b6bb-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="9b6bb-149">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="9b6bb-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="9b6bb-150">Como gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="9b6bb-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="9b6bb-151">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="9b6bb-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
