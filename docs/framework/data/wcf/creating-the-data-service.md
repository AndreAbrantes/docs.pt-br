---
title: Criar um serviço de dados WCF no Visual Studio
description: Saiba como criar um serviço de dados de exemplo que usa WCF Data Services para expor um feed OData com base em um banco de dados de exemplo.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: f6e95ce58e055f0c745b781c664309e4ef91ffc6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554007"
---
# <a name="create-the-data-service"></a><span data-ttu-id="7c790-103">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="7c790-103">Create the data service</span></span>

<span data-ttu-id="7c790-104">Neste tópico, você cria um serviço de dados de exemplo que usa WCF Data Services para expor um feed de Protocolo Open Data (OData) baseado no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c790-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="7c790-105">A tarefa envolve as seguintes etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="7c790-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="7c790-106">Crie um aplicativo Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7c790-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="7c790-107">Defina o modelo de dados usando as ferramentas de Modelo de Dados de Entidade.</span><span class="sxs-lookup"><span data-stu-id="7c790-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="7c790-108">Adicionar o serviço de dados para o aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="7c790-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="7c790-109">Habilitar o acesso ao serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="7c790-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="7c790-110">Criar o aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7c790-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="7c790-111">No Visual Studio, no menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="7c790-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="7c790-112">Na caixa de diálogo **novo projeto** , em Visual Basic ou Visual C#, selecione a categoria **Web** e, em seguida, selecione **aplicativo Web ASP.net**.</span><span class="sxs-lookup"><span data-stu-id="7c790-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="7c790-113">Insira `NorthwindService` como o nome do projeto e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c790-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="7c790-114">Na caixa de diálogo **novo aplicativo Web ASP.net** , selecione **vazio** e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c790-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="7c790-115">(Opcional) Especifique um número de porta específica para seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="7c790-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="7c790-116">Observação: o número da porta `12345` é usado nesta série de tópicos de início rápido.</span><span class="sxs-lookup"><span data-stu-id="7c790-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="7c790-117">No **Gerenciador de soluções**, clique com o botão direito do mouse no projeto ASP.NET que você acabou de criar e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7c790-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="7c790-118">Selecione a guia **Web** e defina o valor da caixa de texto **porta específica** como `12345` .</span><span class="sxs-lookup"><span data-stu-id="7c790-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="7c790-119">Definir o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="7c790-119">Define the data model</span></span>

1. <span data-ttu-id="7c790-120">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ASP.net e clique em **Adicionar**  >  **novo item**.</span><span class="sxs-lookup"><span data-stu-id="7c790-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7c790-121">Na caixa de diálogo **Adicionar novo item** , selecione a categoria de **dados** e, em seguida, selecione **ADO.NET modelo de dados de entidade**.</span><span class="sxs-lookup"><span data-stu-id="7c790-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="7c790-122">Para o nome do modelo de dados, digite `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="7c790-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="7c790-123">No **Assistente de modelo de dados de entidade**, selecione **EF designer do banco de dados**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7c790-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="7c790-124">Conecte o modelo de dados ao banco de dado executando uma das etapas a seguir e clique em **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="7c790-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="7c790-125">Se você não tiver uma conexão de banco de dados já configurada, clique em **nova conexão** e crie uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="7c790-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="7c790-126">Para obter mais informações, consulte [como: criar conexões para bancos de dados SQL Server](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7c790-126">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="7c790-127">Esta instância de SQL Server deve ter o banco de dados de exemplo Northwind anexado.</span><span class="sxs-lookup"><span data-stu-id="7c790-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="7c790-128">\- ou –</span><span class="sxs-lookup"><span data-stu-id="7c790-128">\- or -</span></span>

    - <span data-ttu-id="7c790-129">Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.</span><span class="sxs-lookup"><span data-stu-id="7c790-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="7c790-130">Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="7c790-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="7c790-131">Clique em **concluir** para fechar o assistente.</span><span class="sxs-lookup"><span data-stu-id="7c790-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="7c790-132">Criar o WCF Data Service</span><span class="sxs-lookup"><span data-stu-id="7c790-132">Create the WCF data service</span></span>

1. <span data-ttu-id="7c790-133">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto ASP.net e escolha **Adicionar**  >  **novo item**.</span><span class="sxs-lookup"><span data-stu-id="7c790-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7c790-134">Na caixa de diálogo **Adicionar novo item** , selecione o modelo item do **WCF Data Service** na categoria **Web** .</span><span class="sxs-lookup"><span data-stu-id="7c790-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7c790-136">O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7c790-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="7c790-137">Para o nome do serviço, digite `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="7c790-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="7c790-138">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="7c790-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7c790-139">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="7c790-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="7c790-140">Em **Gerenciador de soluções**, o serviço tem o nome Northwind com a extensão *. svc.cs* ou *. svc. vb*.</span><span class="sxs-lookup"><span data-stu-id="7c790-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="7c790-141">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="7c790-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="7c790-142">A definição da classe deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="7c790-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="7c790-143">Habilitar o acesso aos recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="7c790-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="7c790-144">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="7c790-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="7c790-145">Isso permite que clientes autorizados tenham acesso de leitura e gravação aos recursos para os conjuntos de entidades especificados.</span><span class="sxs-lookup"><span data-stu-id="7c790-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7c790-146">Qualquer cliente que possa acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="7c790-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="7c790-147">Em um serviço de dados de produção, para impedir o acesso não autorizado a recursos, você também deverá proteger o próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c790-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="7c790-148">Para obter mais informações, consulte [securing WCF Data Services](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c790-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c790-149">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7c790-149">Next steps</span></span>

<span data-ttu-id="7c790-150">Você criou com êxito um novo serviço de dados que expõe um feed OData baseado no banco de dados de exemplo Northwind e que você habilitou o acesso ao feed para clientes que têm permissões no aplicativo Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7c790-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="7c790-151">Em seguida, você iniciará o serviço de dados do Visual Studio e acessará o feed OData enviando solicitações HTTP GET por meio de um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="7c790-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c790-152">Acessar o serviço de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="7c790-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="7c790-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c790-153">See also</span></span>

- <span data-ttu-id="7c790-154">[Ferramentas de Modelo de Dados de Entidade de ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7c790-154">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
