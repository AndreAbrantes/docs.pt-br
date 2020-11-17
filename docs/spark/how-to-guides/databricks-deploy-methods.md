---
title: Enviar um trabalho .NET para Apache Spark para o databricks
description: Saiba como enviar um .NET para Apache Spark trabalho para o databricks usando Spark-Submit e Set jar.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4d37383ccb3c9b311e0fbd0ada195ac20113e505
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688196"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="2c37d-103">Enviar um trabalho .NET para Apache Spark para o databricks</span><span class="sxs-lookup"><span data-stu-id="2c37d-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="2c37d-104">Você pode executar o .NET para Apache Spark trabalhos em clusters do databricks, mas ele não está disponível de pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="2c37d-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="2c37d-105">Há duas maneiras de implantar seu .NET para Apache Spark trabalho no databricks: `spark-submit` e definir jar.</span><span class="sxs-lookup"><span data-stu-id="2c37d-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="2c37d-106">Implantar usando Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="2c37d-106">Deploy using spark-submit</span></span>

<span data-ttu-id="2c37d-107">Você pode usar o comando [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar o .net para trabalhos do Apache Spark para o databricks.</span><span class="sxs-lookup"><span data-stu-id="2c37d-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="2c37d-108">`spark-submit` permite o envio somente para um cluster que é criado sob demanda.</span><span class="sxs-lookup"><span data-stu-id="2c37d-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="2c37d-109">Navegue até o espaço de trabalho do databricks e crie um trabalho.</span><span class="sxs-lookup"><span data-stu-id="2c37d-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="2c37d-110">Escolha um título para seu trabalho e, em seguida, selecione **Configurar Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="2c37d-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="2c37d-111">Cole os seguintes parâmetros na configuração do trabalho e, em seguida, selecione **confirmar**.</span><span class="sxs-lookup"><span data-stu-id="2c37d-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="2c37d-112">Atualize o conteúdo do parâmetro acima com base em seus arquivos e configurações específicos.</span><span class="sxs-lookup"><span data-stu-id="2c37d-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="2c37d-113">Por exemplo, referencie a versão do arquivo JAR do Microsoft. Spark que você carregou em DBFS e use o nome apropriado do seu aplicativo e o arquivo zip do aplicativo publicado.</span><span class="sxs-lookup"><span data-stu-id="2c37d-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="2c37d-114">Navegue até seu trabalho e selecione **Editar** para configurar o cluster do trabalho.</span><span class="sxs-lookup"><span data-stu-id="2c37d-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="2c37d-115">Defina a versão Databricks Runtime com base na versão do Apache Spark que você deseja usar em sua implantação.</span><span class="sxs-lookup"><span data-stu-id="2c37d-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="2c37d-116">Em seguida, selecione **Opções avançadas > scripts de inicialização** e defina caminho do script de inicialização como `dbfs:/spark-dotnet/db-init.sh` .</span><span class="sxs-lookup"><span data-stu-id="2c37d-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="2c37d-117">Selecione **confirmar** para confirmar as configurações de cluster.</span><span class="sxs-lookup"><span data-stu-id="2c37d-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="2c37d-118">Navegue até seu trabalho e selecione **executar agora** para executar seu trabalho em seu cluster Spark recém configurado.</span><span class="sxs-lookup"><span data-stu-id="2c37d-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="2c37d-119">Leva alguns minutos para que o cluster do trabalho seja criado.</span><span class="sxs-lookup"><span data-stu-id="2c37d-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="2c37d-120">Depois que ele for criado, seu trabalho será enviado.</span><span class="sxs-lookup"><span data-stu-id="2c37d-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="2c37d-121">Você pode exibir a saída selecionando **clusters** no menu à esquerda do seu espaço de trabalho do databricks e, em seguida, selecionar **logs de driver**.</span><span class="sxs-lookup"><span data-stu-id="2c37d-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="2c37d-122">Implantar usando Set jar</span><span class="sxs-lookup"><span data-stu-id="2c37d-122">Deploy using Set Jar</span></span>

<span data-ttu-id="2c37d-123">Como alternativa, você pode usar [set jar](/azure/databricks/jobs#--create-a-job) em seu espaço de trabalho do databricks para enviar Apache Spark trabalhos do .net para o databricks.</span><span class="sxs-lookup"><span data-stu-id="2c37d-123">Alternatively, you can use [Set Jar](/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="2c37d-124">*Set jar* permite o envio de trabalhos para um cluster ativo existente.</span><span class="sxs-lookup"><span data-stu-id="2c37d-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="2c37d-125">Configuração única</span><span class="sxs-lookup"><span data-stu-id="2c37d-125">One-time setup</span></span>

1. <span data-ttu-id="2c37d-126">Navegue até o cluster do databricks e selecione **trabalhos** no menu do lado esquerdo, seguido por **set jar**.</span><span class="sxs-lookup"><span data-stu-id="2c37d-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="2c37d-127">Carregue o apropriado `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` .</span><span class="sxs-lookup"><span data-stu-id="2c37d-127">Upload the appropriate `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`.</span></span>

3. <span data-ttu-id="2c37d-128">Modifique os seguintes parâmetros para incluir o nome correto para o executável que você publicou no lugar de `<your-app-name>` :</span><span class="sxs-lookup"><span data-stu-id="2c37d-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="2c37d-129">Configure o cluster para apontar para um cluster existente para o qual você já definiu o script de inicialização.</span><span class="sxs-lookup"><span data-stu-id="2c37d-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="2c37d-130">Publicar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c37d-130">Publish and run your app</span></span>

1. <span data-ttu-id="2c37d-131">Verifique se você publicou seu aplicativo e se o código do aplicativo não usa `SparkSession.Stop()` .</span><span class="sxs-lookup"><span data-stu-id="2c37d-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="2c37d-132">Use a [CLI do databricks](/azure/databricks/dev-tools/databricks-cli) para carregar seu aplicativo em seu cluster do databricks.</span><span class="sxs-lookup"><span data-stu-id="2c37d-132">Use [Databricks CLI](/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="2c37d-133">Por exemplo, use o seguinte comando para carregar seu aplicativo publicado em seu cluster:</span><span class="sxs-lookup"><span data-stu-id="2c37d-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="2c37d-134">Se você tiver funções definidas pelo usuário em seu aplicativo, os assemblies de aplicativo, como DLLs que contêm funções definidas pelo usuário, juntamente com suas dependências, precisam ser colocados no diretório de trabalho de cada *Microsoft. Spark. Worker*.</span><span class="sxs-lookup"><span data-stu-id="2c37d-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="2c37d-135">Carregue seus assemblies de aplicativo em seu cluster do databricks:</span><span class="sxs-lookup"><span data-stu-id="2c37d-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="2c37d-136">Remova a marca de comentário e modifique a seção de dependências do aplicativo em [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) para apontar para o caminho de dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c37d-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="2c37d-137">Em seguida, carregue o *DB-init.sh* atualizado em seu cluster:</span><span class="sxs-lookup"><span data-stu-id="2c37d-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="2c37d-138">Navegue até **cluster do databricks > trabalhos > [nome-do-trabalho] > executar agora** para executar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="2c37d-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c37d-139">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2c37d-139">Next steps</span></span>

* [<span data-ttu-id="2c37d-140">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2c37d-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="2c37d-141">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="2c37d-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="2c37d-142">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="2c37d-142">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
