---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo do .NET para Apache Spark no HDInsight.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9a4ca80463de41a50d103c696b2108d0cef023fc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548371"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="93489-103">Tutorial: implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="93489-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="93489-104">Este tutorial ensina como implantar seu .NET para Apache Spark aplicativo na nuvem por meio de um cluster do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="93489-105">O HDInsight facilita a criação e a configuração de um cluster Spark no Azure, pois os clusters do Spark no HDInsight são compatíveis com o armazenamento do Azure e Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="93489-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="93489-106">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="93489-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="93489-107">Acesse suas contas de armazenamento usando Gerenciador de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="93489-108">Crie um cluster HDInsight do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="93489-109">Publique seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="93489-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="93489-110">Crie e execute uma ação de script do HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="93489-111">Execute um aplicativo .NET para Apache Spark em um cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="93489-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="93489-112">Prerequisites</span></span>

<span data-ttu-id="93489-113">Antes de começar, execute as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="93489-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="93489-114">Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="93489-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="93489-115">Entre no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="93489-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="93489-116">Instale o Gerenciador de Armazenamento do Azure em seu computador [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .</span><span class="sxs-lookup"><span data-stu-id="93489-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="93489-117">Conclua o [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="93489-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="93489-118">Acessar suas contas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="93489-118">Access your storage accounts</span></span>

1. <span data-ttu-id="93489-119">Abra o Gerenciador de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="93489-120">Selecione **adicionar conta** no menu à esquerda e entre em sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Entrar na conta do Azure de Gerenciador de Armazenamento](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="93489-122">Depois de entrar, você deverá ver todas as contas de armazenamento que você tem e todos os recursos que você carregou em suas contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="93489-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="93489-123">Crie um cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="93489-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93489-124">A cobrança por clusters HDInsight é rateada por minuto, mesmo se você não os estiver usando.</span><span class="sxs-lookup"><span data-stu-id="93489-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="93489-125">Exclua seu cluster depois de terminar de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="93489-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="93489-126">Para obter mais informações, consulte a seção [limpar recursos](#clean-up-resources) deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="93489-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="93489-127">Visite o [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="93489-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="93489-128">Selecione **+ Criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="93489-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="93489-129">Em seguida, selecione **HDInsight** na categoria **análise** .</span><span class="sxs-lookup"><span data-stu-id="93489-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Criar recurso do HDInsight a partir de portal do Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="93489-131">Em **Noções básicas**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="93489-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="93489-132">Propriedade</span><span class="sxs-lookup"><span data-stu-id="93489-132">Property</span></span>  |<span data-ttu-id="93489-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="93489-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="93489-134">Subscription</span><span class="sxs-lookup"><span data-stu-id="93489-134">Subscription</span></span>  | <span data-ttu-id="93489-135">Na lista suspensa, escolha uma das suas assinaturas ativas do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="93489-136">Resource group</span><span class="sxs-lookup"><span data-stu-id="93489-136">Resource group</span></span> | <span data-ttu-id="93489-137">Especifique se deseja criar um novo grupo de recursos ou usar um existente.</span><span class="sxs-lookup"><span data-stu-id="93489-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="93489-138">Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure.</span><span class="sxs-lookup"><span data-stu-id="93489-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="93489-139">Nome do cluster</span><span class="sxs-lookup"><span data-stu-id="93489-139">Cluster name</span></span> | <span data-ttu-id="93489-140">Dê um nome para seu cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="93489-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="93489-141">Location</span><span class="sxs-lookup"><span data-stu-id="93489-141">Location</span></span>   | <span data-ttu-id="93489-142">Selecione um local para o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="93489-142">Select a location for the resource group.</span></span> <span data-ttu-id="93489-143">O modelo usa esse local para criar o cluster, bem como para o armazenamento de cluster padrão.</span><span class="sxs-lookup"><span data-stu-id="93489-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="93489-144">Tipo de cluster</span><span class="sxs-lookup"><span data-stu-id="93489-144">Cluster type</span></span>| <span data-ttu-id="93489-145">Selecione **Spark** como o tipo de cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="93489-146">Versão do cluster</span><span class="sxs-lookup"><span data-stu-id="93489-146">Cluster version</span></span>|<span data-ttu-id="93489-147">Este campo será preenchido automaticamente com a versão padrão depois que o tipo de cluster tiver sido selecionado.</span><span class="sxs-lookup"><span data-stu-id="93489-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="93489-148">Selecione uma versão 2,3 ou 2,4 do Spark.</span><span class="sxs-lookup"><span data-stu-id="93489-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="93489-149">Nome de usuário de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="93489-149">Cluster login username</span></span>| <span data-ttu-id="93489-150">Insira o nome de logon do usuário do cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-150">Enter the cluster login username.</span></span>  <span data-ttu-id="93489-151">O nome padrão é *admin*.</span><span class="sxs-lookup"><span data-stu-id="93489-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="93489-152">Senha de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="93489-152">Cluster login password</span></span>| <span data-ttu-id="93489-153">Insira qualquer senha de logon.</span><span class="sxs-lookup"><span data-stu-id="93489-153">Enter any login password.</span></span> |
    |<span data-ttu-id="93489-154">Nome de usuário do Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="93489-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="93489-155">Insira um Nome de Usuário SSH.</span><span class="sxs-lookup"><span data-stu-id="93489-155">Enter the SSH username.</span></span> <span data-ttu-id="93489-156">Por padrão, essa conta tem a mesma senha que a conta de*nome de usuário de logon do cluster*.</span><span class="sxs-lookup"><span data-stu-id="93489-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="93489-157">Selecione **Avançar: Armazenamento >>** para continuar para a página **Armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="93489-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="93489-158">Em **Armazenamento**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="93489-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="93489-159">Propriedade</span><span class="sxs-lookup"><span data-stu-id="93489-159">Property</span></span>  |<span data-ttu-id="93489-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="93489-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="93489-161">Tipo de armazenamento primário</span><span class="sxs-lookup"><span data-stu-id="93489-161">Primary storage type</span></span>|<span data-ttu-id="93489-162">Use o valor padrão **Armazenamento do Azure**.</span><span class="sxs-lookup"><span data-stu-id="93489-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="93489-163">Método de seleção</span><span class="sxs-lookup"><span data-stu-id="93489-163">Selection method</span></span>|<span data-ttu-id="93489-164">Use o valor padrão **Selecione na lista**.</span><span class="sxs-lookup"><span data-stu-id="93489-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="93489-165">Conta de armazenamento primária</span><span class="sxs-lookup"><span data-stu-id="93489-165">Primary storage account</span></span>|<span data-ttu-id="93489-166">Escolha sua assinatura e uma de suas contas de armazenamento ativas nessa assinatura.</span><span class="sxs-lookup"><span data-stu-id="93489-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="93489-167">Contêiner</span><span class="sxs-lookup"><span data-stu-id="93489-167">Container</span></span>|<span data-ttu-id="93489-168">Esse contêiner é o contêiner de blob específico em sua conta de armazenamento em que o cluster procura arquivos para executar seu aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="93489-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="93489-169">Você pode dar a ele qualquer nome disponível.</span><span class="sxs-lookup"><span data-stu-id="93489-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="93489-170">Em **Examinar + criar**, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="93489-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="93489-171">Demora cerca de 20 minutos para criar o cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="93489-172">O cluster deve ser criado para que você possa continuar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="93489-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="93489-173">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="93489-173">Publish your app</span></span>

<span data-ttu-id="93489-174">Em seguida, você publica o *mySparkApp* criado no [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , que dá acesso ao cluster Spark a todos os arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93489-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="93489-175">Execute os seguintes comandos para publicar o *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="93489-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="93489-176">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="93489-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="93489-177">**No Linux:**</span><span class="sxs-lookup"><span data-stu-id="93489-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="93489-178">Execute as seguintes tarefas para compactar seus arquivos de aplicativo publicados para que você possa carregá-los facilmente em seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="93489-179">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="93489-179">**On Windows:**</span></span>

   <span data-ttu-id="93489-180">Navegue até *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="93489-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="93489-181">Em seguida, clique com o botão direito do mouse em **publicar** pasta e selecione **Enviar para > pasta compactada (zipada)**.</span><span class="sxs-lookup"><span data-stu-id="93489-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="93489-182">Nomeie a nova pasta **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="93489-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="93489-183">**No Linux, execute o seguinte comando:**</span><span class="sxs-lookup"><span data-stu-id="93489-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="93489-184">Carregar arquivos no Azure</span><span class="sxs-lookup"><span data-stu-id="93489-184">Upload files to Azure</span></span>

<span data-ttu-id="93489-185">Em seguida, use o Gerenciador de Armazenamento do Azure para carregar os cinco arquivos a seguir no contêiner de BLOBs que você escolheu para o armazenamento do cluster:</span><span class="sxs-lookup"><span data-stu-id="93489-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="93489-186">Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="93489-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="93489-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="93489-187">install-worker.sh</span></span>
* <span data-ttu-id="93489-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="93489-188">publish.zip</span></span>
* <span data-ttu-id="93489-189">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="93489-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="93489-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="93489-190">input.txt.</span></span>

1. <span data-ttu-id="93489-191">Abra Gerenciador de Armazenamento do Azure e navegue até sua conta de armazenamento no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="93489-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="93489-192">Faça uma busca detalhada no contêiner de BLOBs do cluster em **contêineres de blob** em sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="93489-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="93489-193">O *Microsoft. Spark. Worker* ajuda a Apache Spark executar seu aplicativo, como qualquer UDFs (funções definidas pelo usuário) que você possa ter escrito.</span><span class="sxs-lookup"><span data-stu-id="93489-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="93489-194">Baixe [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="93489-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="93489-195">Em seguida, selecione **carregar** em Gerenciador de armazenamento do Azure para carregar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="93489-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Carregar arquivos para Gerenciador de Armazenamento do Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="93489-197">O *install-Worker.sh* é um script que permite que você copie o .net para Apache Spark arquivos dependentes nos nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="93489-198">Crie um novo arquivo chamado **install-Worker.sh** seu computador local e cole o [conteúdo do install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no github.</span><span class="sxs-lookup"><span data-stu-id="93489-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="93489-199">Em seguida, carregue *install-Worker.sh* em seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="93489-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="93489-200">O cluster precisa do arquivo de publish.zip que contém os arquivos publicados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93489-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="93489-201">Navegue até a pasta publicada, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, e localize **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="93489-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="93489-202">Em seguida, carregue *publish.zip* em seu contêiner de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="93489-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="93489-203">O cluster precisa do código do aplicativo que foi empacotado em um arquivo jar.</span><span class="sxs-lookup"><span data-stu-id="93489-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="93489-204">Navegue até a pasta publicada, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, e localize **Microsoft-Spark-2.3. x-0.3.0. jar**.</span><span class="sxs-lookup"><span data-stu-id="93489-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="93489-205">Em seguida, carregue o arquivo jar em seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="93489-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="93489-206">Pode haver vários arquivos. jar (para as versões 2.3. x e 2.4. x do Spark).</span><span class="sxs-lookup"><span data-stu-id="93489-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="93489-207">Você precisa escolher o arquivo. jar que corresponde à versão do Spark escolhida durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="93489-208">Por exemplo, escolha *Microsoft-Spark-2.3. x-0.3.0. jar* se você escolheu Spark 2.3.2 durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="93489-209">O cluster precisa da entrada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93489-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="93489-210">Navegue até o diretório **mySparkApp** e localize **input.txt**.</span><span class="sxs-lookup"><span data-stu-id="93489-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="93489-211">Carregue o arquivo de entrada no diretório **User/sshuser** no seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="93489-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="93489-212">Você se conectará ao cluster por meio de SSH e essa pasta será onde o cluster procurará sua entrada.</span><span class="sxs-lookup"><span data-stu-id="93489-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="93489-213">O arquivo de *input.txt* é o único arquivo carregado em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="93489-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="93489-214">Executar a ação de script do HDInsight</span><span class="sxs-lookup"><span data-stu-id="93489-214">Run the HDInsight script action</span></span>

<span data-ttu-id="93489-215">Depois que o cluster estiver em execução e você carregou seus arquivos no Azure, execute o script **install-Worker.sh** no cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="93489-216">Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **ações de script**.</span><span class="sxs-lookup"><span data-stu-id="93489-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="93489-217">Selecione **+ Enviar novo** e forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="93489-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="93489-218">Propriedade</span><span class="sxs-lookup"><span data-stu-id="93489-218">Property</span></span>  |<span data-ttu-id="93489-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="93489-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="93489-220">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="93489-220">Script type</span></span> |<span data-ttu-id="93489-221">Personalizado</span><span class="sxs-lookup"><span data-stu-id="93489-221">Custom</span></span>|
   | <span data-ttu-id="93489-222">Name</span><span class="sxs-lookup"><span data-stu-id="93489-222">Name</span></span> | <span data-ttu-id="93489-223">Instalar trabalho</span><span class="sxs-lookup"><span data-stu-id="93489-223">Install Worker</span></span>|
   | <span data-ttu-id="93489-224">URI do script Bash</span><span class="sxs-lookup"><span data-stu-id="93489-224">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="93489-225">Para confirmar esse URI, clique com o botão direito do mouse em install-worker.sh em Gerenciador de Armazenamento do Azure e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="93489-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="93489-226">Tipo(s) de nó</span><span class="sxs-lookup"><span data-stu-id="93489-226">Node type(s)</span></span>| <span data-ttu-id="93489-227">Trabalho</span><span class="sxs-lookup"><span data-stu-id="93489-227">Worker</span></span>|
   | <span data-ttu-id="93489-228">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93489-228">Parameters</span></span> | <span data-ttu-id="93489-229">azure</span><span class="sxs-lookup"><span data-stu-id="93489-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="93489-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="93489-230">/usr/local/bin</span></span>

3. <span data-ttu-id="93489-231">Selecione **criar** para enviar o script.</span><span class="sxs-lookup"><span data-stu-id="93489-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="93489-232">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="93489-232">Run your app</span></span>

1. <span data-ttu-id="93489-233">Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **SSH + logon do cluster**.</span><span class="sxs-lookup"><span data-stu-id="93489-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="93489-234">Copie as informações de logon SSH e cole o logon em um terminal.</span><span class="sxs-lookup"><span data-stu-id="93489-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="93489-235">Entre no cluster usando a senha que você definiu durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="93489-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="93489-236">Você deve ver as mensagens com boas-vindas ao Ubuntu e ao Spark.</span><span class="sxs-lookup"><span data-stu-id="93489-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="93489-237">Use o comando **Spark-Submit** para executar seu aplicativo em seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="93489-238">Lembre-se de substituir **MyContainer** e **mystorageaccount** no script de exemplo pelos nomes reais do contêiner de BLOB e da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="93489-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="93489-239">Quando seu aplicativo for executado, você verá a mesma tabela de contagem de palavras da execução local de introdução gravada no console.</span><span class="sxs-lookup"><span data-stu-id="93489-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="93489-240">Parabéns, você executou seu primeiro .NET para Apache Spark aplicativo na nuvem!</span><span class="sxs-lookup"><span data-stu-id="93489-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="93489-241">Limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="93489-241">Clean up resources</span></span>

<span data-ttu-id="93489-242">O HDInsight salva seus dados no armazenamento do Azure, para que você possa excluir um cluster com segurança quando ele não estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="93489-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="93489-243">Você também é cobrado por um cluster HDInsight, mesmo quando ele não está em uso.</span><span class="sxs-lookup"><span data-stu-id="93489-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="93489-244">Como os encargos para o cluster são muitas vezes maiores do que os encargos para armazenamento, faz sentido, do ponto de vista econômico, excluir os clusters quando não estiverem em uso.</span><span class="sxs-lookup"><span data-stu-id="93489-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="93489-245">Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="93489-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="93489-246">Ao excluir o grupo de recursos, você exclui o cluster Spark do HDInsight e a conta de armazenamento padrão.</span><span class="sxs-lookup"><span data-stu-id="93489-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="93489-247">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="93489-247">Next steps</span></span>

<span data-ttu-id="93489-248">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="93489-249">Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="93489-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93489-250">Documentação do HDInsight do Azure</span><span class="sxs-lookup"><span data-stu-id="93489-250">Azure HDInsight Documentation</span></span>](/azure/hdinsight/)
