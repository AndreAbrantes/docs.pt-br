---
title: Criar um aplicativo Olá, Mundo com o .NET Core no Visual Studio
description: Saiba como criar seu primeiro aplicativo de console do .NET Core com C# ou Visual Basic usando o Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394821"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="3a541-103">Tutorial: criar seu primeiro aplicativo de console do .NET Core no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="3a541-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="3a541-104">Este artigo fornece uma introdução passo a passo para criar e executar um Olá, Mundo aplicativo de console .NET Core no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="3a541-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="3a541-105">Um aplicativo Olá, Mundo é tradicionalmente usado para apresentar iniciantes a uma nova linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="3a541-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="3a541-106">Este programa simplesmente exibe a frase "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="3a541-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="3a541-107">na tela.</span><span class="sxs-lookup"><span data-stu-id="3a541-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a541-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3a541-108">Prerequisites</span></span>

- <span data-ttu-id="3a541-109">[Visual Studio 2019 versão 16,4 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="3a541-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="3a541-110">O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a541-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="3a541-111">Para obter mais informações, consulte a seção [instalar com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) no artigo [instalar o SDK do .NET Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="3a541-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="3a541-112">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a541-112">Create the app</span></span>

<span data-ttu-id="3a541-113">As instruções a seguir criam um aplicativo simples de console de Olá, Mundo:</span><span class="sxs-lookup"><span data-stu-id="3a541-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="3a541-114">C#</span><span class="sxs-lookup"><span data-stu-id="3a541-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="3a541-115">Abra o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="3a541-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="3a541-116">Crie um novo projeto de aplicativo de console do .NET Core do C# chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="3a541-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="3a541-117">Na janela iniciar, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="3a541-117">On the start window, choose **Create a new project**.</span></span>

      ![Criar um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="3a541-119">Na página **criar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3a541-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="3a541-120">Em seguida, escolha **C#** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="3a541-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="3a541-121">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a541-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Criar uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="3a541-123">Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária instalada.</span><span class="sxs-lookup"><span data-stu-id="3a541-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="3a541-124">Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** .</span><span class="sxs-lookup"><span data-stu-id="3a541-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="3a541-125">O Instalador do Visual Studio é aberto.</span><span class="sxs-lookup"><span data-stu-id="3a541-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="3a541-126">Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="3a541-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="3a541-127">Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="3a541-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="3a541-128">Em seguida, escolha **criar**.</span><span class="sxs-lookup"><span data-stu-id="3a541-128">Then, choose **Create**.</span></span>

      ![Configurar sua nova janela de projeto com os campos nome do projeto, local e nome da solução](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="3a541-130">O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento.</span><span class="sxs-lookup"><span data-stu-id="3a541-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="3a541-131">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a541-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="3a541-132">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="3a541-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="3a541-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a541-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="3a541-135">Abra o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="3a541-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="3a541-136">Crie um novo projeto de aplicativo de console Visual Basic .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="3a541-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="3a541-137">Na janela iniciar, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="3a541-137">On the start window, choose **Create a new project**.</span></span>

      ![Criar um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="3a541-139">Na página **criar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3a541-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="3a541-140">Em seguida, escolha **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="3a541-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="3a541-141">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a541-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Escolha o modelo de Visual Basic para o Aplicativo de Console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="3a541-143">Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária instalada.</span><span class="sxs-lookup"><span data-stu-id="3a541-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="3a541-144">Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** .</span><span class="sxs-lookup"><span data-stu-id="3a541-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="3a541-145">O Instalador do Visual Studio é aberto.</span><span class="sxs-lookup"><span data-stu-id="3a541-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="3a541-146">Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="3a541-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="3a541-147">Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="3a541-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="3a541-148">Em seguida, escolha **criar**.</span><span class="sxs-lookup"><span data-stu-id="3a541-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="3a541-149">O modelo de aplicativo de console para .NET Core define automaticamente uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento.</span><span class="sxs-lookup"><span data-stu-id="3a541-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="3a541-150">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a541-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="3a541-151">Todos os argumentos de linha de comando fornecidos quando o aplicativo é iniciado estão disponíveis no `args` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3a541-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="3a541-153">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="3a541-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="3a541-154">Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3a541-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="3a541-155">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="3a541-156">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a541-156">Run the app</span></span>

1. <span data-ttu-id="3a541-157">Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="3a541-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Barra de ferramentas do Visual Studio com o botão execução HelloWorld selecionado](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="3a541-159">Uma janela de console é aberta com o texto "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="3a541-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="3a541-160">impresso na tela e algumas informações de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a541-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="3a541-162">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="3a541-163">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a541-163">Enhance the app</span></span>

<span data-ttu-id="3a541-164">Aprimore seu aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="3a541-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="3a541-165">As instruções a seguir modificam e executam o aplicativo novamente:</span><span class="sxs-lookup"><span data-stu-id="3a541-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a541-166">C#</span><span class="sxs-lookup"><span data-stu-id="3a541-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="3a541-167">Substitua o conteúdo do `Main` método, que atualmente é apenas a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3a541-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   <span data-ttu-id="3a541-168">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="3a541-168">This code displays "What is your name?"</span></span> <span data-ttu-id="3a541-169">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter.</span><span class="sxs-lookup"><span data-stu-id="3a541-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="3a541-170">Ele armazena essa cadeia de caracteres a uma variável chamada `name`.</span><span class="sxs-lookup"><span data-stu-id="3a541-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="3a541-171">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="3a541-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="3a541-172">Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/tokens/interpolated.md) para exibir esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="3a541-173">Compile o programa escolhendo **criar**  >  **solução de compilação**.</span><span class="sxs-lookup"><span data-stu-id="3a541-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="3a541-174">Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="3a541-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="3a541-175">Responda ao prompt digitando um nome e pressionando a tecla **Enter** .</span><span class="sxs-lookup"><span data-stu-id="3a541-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="3a541-177">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="3a541-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a541-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="3a541-179">Substitua o conteúdo do `Main` método, que atualmente é apenas a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3a541-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="3a541-180">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="3a541-180">This code displays "What is your name?"</span></span> <span data-ttu-id="3a541-181">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter.</span><span class="sxs-lookup"><span data-stu-id="3a541-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="3a541-182">Ele armazena essa cadeia de caracteres a uma variável chamada `name`.</span><span class="sxs-lookup"><span data-stu-id="3a541-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="3a541-183">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="3a541-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="3a541-184">Por fim, ele usa uma [cadeia de caracteres interpolada](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) para exibir esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="3a541-185">Compile o programa escolhendo **criar**  >  **solução de compilação**.</span><span class="sxs-lookup"><span data-stu-id="3a541-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="3a541-186">Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="3a541-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="3a541-187">Responda ao prompt digitando um nome e pressionando a tecla **Enter** .</span><span class="sxs-lookup"><span data-stu-id="3a541-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="3a541-189">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a541-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="3a541-190">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a541-190">Next steps</span></span>

<span data-ttu-id="3a541-191">Neste artigo, você criou e executou seu primeiro aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a541-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="3a541-192">Na próxima etapa, você depurará seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a541-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a541-193">Depurar um aplicativo .NET Core Olá, Mundo no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a541-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
