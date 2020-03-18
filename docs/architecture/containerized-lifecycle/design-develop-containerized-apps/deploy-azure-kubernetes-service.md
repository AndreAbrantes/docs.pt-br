---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Saiba como implantar um aplicativo usando o Serviço de Kubernetes do Azure.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182365"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="8bd3e-103">Implantar no AKS (Serviço de Kubernetes do Azure)</span><span class="sxs-lookup"><span data-stu-id="8bd3e-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="8bd3e-104">Você pode interagir com o AKS usando o sistema operacional cliente de sua preferência. Aqui vamos mostrar como fazer isso com o Microsoft Windows e uma versão integrada do Ubuntu Linux no Windows usando comandos de Bash.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="8bd3e-105">Os pré-requisitos para antes do uso do AKS são:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="8bd3e-106">Computador de desenvolvimento do Linux ou Mac</span><span class="sxs-lookup"><span data-stu-id="8bd3e-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="8bd3e-107">Computador de desenvolvimento do Windows</span><span class="sxs-lookup"><span data-stu-id="8bd3e-107">Windows development machine</span></span>
  - <span data-ttu-id="8bd3e-108">Modo de desenvolvedor habilitado no Windows</span><span class="sxs-lookup"><span data-stu-id="8bd3e-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="8bd3e-109">Subsistema do Windows para Linux</span><span class="sxs-lookup"><span data-stu-id="8bd3e-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="8bd3e-110">CLI do Azure instalada no [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="8bd3e-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="8bd3e-111">Para encontrar informações completas sobre:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-111">To find complete information about:</span></span>
>
> <span data-ttu-id="8bd3e-112">CLI do Azure: <https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="8bd3e-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="8bd3e-113">Subsistema do Windows para Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="8bd3e-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="8bd3e-114">Criar o ambiente do AKS no Azure</span><span class="sxs-lookup"><span data-stu-id="8bd3e-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="8bd3e-115">Existem várias maneiras de criar o Ambiente do AKS.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="8bd3e-116">Isso pode ser feito usando os comandos da CLI do Azure ou usando o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="8bd3e-117">Aqui você pode explorar alguns exemplos usando a CLI do Azure para criar o cluster, bem como o portal do Azure para examinar os resultados.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="8bd3e-118">Você também precisará ter o Kubectl e o Docker em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="8bd3e-119">Criar o cluster do AKS</span><span class="sxs-lookup"><span data-stu-id="8bd3e-119">Create the AKS cluster</span></span>

<span data-ttu-id="8bd3e-120">Crie o cluster do AKS usando este comando:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="8bd3e-121">Após o trabalho de criação ser concluído, você poderá ver o AKS criado no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="8bd3e-122">O grupo de recursos:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-122">The resource group:</span></span>

![Exibição de navegador do grupo de recursos do AKS do Azure.](media/aks-resource-group-view.png)

<span data-ttu-id="8bd3e-124">**Figura 4-17**.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-124">**Figure 4-17**.</span></span> <span data-ttu-id="8bd3e-125">Exibição do Grupo de Recursos do AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="8bd3e-126">O cluster do AKS:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-126">The AKS cluster:</span></span>

![Exibição de navegador do grupo de recursos do AKS.](media/aks-cluster-view.png)

<span data-ttu-id="8bd3e-128">**Figura 4-18**.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-128">**Figure 4-18**.</span></span> <span data-ttu-id="8bd3e-129">Exibição do AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-129">AKS view from Azure.</span></span>

<span data-ttu-id="8bd3e-130">Você também pode exibir o nó criado usando `Azure-CLI` e `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="8bd3e-131">Em primeiro lugar, obtendo as credenciais:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Saída do console do comando acima: Mesclado "MsSampleK8Cluster como contexto atual em /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="8bd3e-133">**Figura 4-19**.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-133">**Figure 4-19**.</span></span> <span data-ttu-id="8bd3e-134">Resultado do comando `aks get-credentials`.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="8bd3e-135">E, em seguida, obtendo nós do Kubectl:</span><span class="sxs-lookup"><span data-stu-id="8bd3e-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Saída do console do comando acima: Lista de nomes com status, idade (tempo de execução) e versão](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="8bd3e-137">**Figura 4-20**.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-137">**Figure 4-20**.</span></span> <span data-ttu-id="8bd3e-138">Resultado do comando `kubectl get nodes`.</span><span class="sxs-lookup"><span data-stu-id="8bd3e-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8bd3e-139">[Próximo](orchestrate-high-scalability-availability.md)
>[anterior](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="8bd3e-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
