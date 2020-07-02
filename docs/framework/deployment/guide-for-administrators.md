---
title: Guia de implantação do .NET Framework para administradores
description: Leia o guia de implantação do .NET para administradores. Use essas informações para implantar a versão 4,5 do .NET e suas dependências do sistema em uma rede.
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: d58eac4f21e4f1069ac392aacb4e9818831e914c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622647"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="c14cc-104">Guia de implantação do .NET Framework para administradores</span><span class="sxs-lookup"><span data-stu-id="c14cc-104">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="c14cc-105">Este artigo passo a passo descreve como um administrador do sistema pode implantar o .NET Framework 4,5 e suas dependências do sistema em uma rede usando o Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-105">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="c14cc-106">Este artigo pressupõe que todos os computadores clientes de destino atendem aos requisitos mínimos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c14cc-106">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="c14cc-107">Para obter uma lista dos requisitos de hardware e software para instalar o .NET Framework 4.5, consulte [Requisitos do sistema](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14cc-107">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c14cc-108">O software referenciado neste documento, incluindo, sem limitação, o .NET Framework 4,5, Configuration Manager e Active Directory, estão sujeitos aos termos e condições da licença.</span><span class="sxs-lookup"><span data-stu-id="c14cc-108">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="c14cc-109">Essas instruções assumem que esses termos de licença e condições foram examinados e aceitos pelos licenciados apropriados do software.</span><span class="sxs-lookup"><span data-stu-id="c14cc-109">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="c14cc-110">Essas instruções não renunciam nenhum dos termos e condições dos contratos de tal licença.</span><span class="sxs-lookup"><span data-stu-id="c14cc-110">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="c14cc-111">Para obter informações sobre o suporte para o .NET Framework, consulte [.NET Framework a política de suporte oficial](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) no site do suporte da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c14cc-111">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="c14cc-112">Este tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="c14cc-112">This topic contains the following sections:</span></span>

- [<span data-ttu-id="c14cc-113">O processo de implantação</span><span class="sxs-lookup"><span data-stu-id="c14cc-113">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="c14cc-114">Implantando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c14cc-114">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="c14cc-115">Criar uma coleção</span><span class="sxs-lookup"><span data-stu-id="c14cc-115">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="c14cc-116">Crie um pacote e programa</span><span class="sxs-lookup"><span data-stu-id="c14cc-116">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="c14cc-117">Selecionar um ponto de distribuição</span><span class="sxs-lookup"><span data-stu-id="c14cc-117">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="c14cc-118">Implantar o pacote</span><span class="sxs-lookup"><span data-stu-id="c14cc-118">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="c14cc-119">Recursos</span><span class="sxs-lookup"><span data-stu-id="c14cc-119">Resources</span></span>](#resources)
- [<span data-ttu-id="c14cc-120">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c14cc-120">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="c14cc-121">O processo de implantação</span><span class="sxs-lookup"><span data-stu-id="c14cc-121">The deployment process</span></span>

<span data-ttu-id="c14cc-122">Quando você tem a infraestrutura de suporte em vigor, usa Configuration Manager para implantar o pacote redistribuível .NET Framework em computadores na rede.</span><span class="sxs-lookup"><span data-stu-id="c14cc-122">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="c14cc-123">Estabelecer uma infraestrutura envolve criar e definir cinco áreas principais: coleções, um pacote e programa para o software, pontos de distribuição e implantações.</span><span class="sxs-lookup"><span data-stu-id="c14cc-123">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="c14cc-124">**Coleções** são grupos de recursos do Configuration Manager, como usuários, grupos de usuários ou computadores, nos quais o .NET Framework é implantado.</span><span class="sxs-lookup"><span data-stu-id="c14cc-124">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="c14cc-125">Para obter mais informações, consulte [introdução às coleções em Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-125">For more information, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="c14cc-126">**Pacotes e programas** geralmente representam aplicativos de software a serem instalados em um computador cliente, mas também podem conter arquivos individuais, atualizações ou até mesmo comandos individuais.</span><span class="sxs-lookup"><span data-stu-id="c14cc-126">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="c14cc-127">Para obter mais informações, consulte [pacotes e programas em Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-127">For more information, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="c14cc-128">**Pontos de distribuição** são funções do sistema de sites do Configuration Manager que armazenam os arquivos necessários para que o software seja executado em computadores cliente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-128">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="c14cc-129">Quando o cliente do Configuration Manager recebe e processa uma implantação de software, ele contata um ponto de distribuição para baixar o conteúdo associado ao software e iniciar o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-129">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="c14cc-130">Para obter mais informações, veja [Conceitos fundamentais para gerenciamento de conteúdo no Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-130">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="c14cc-131">**Implantações** instruem os membros aplicáveis da coleção de destino especificada a instalarem o pacote de software.</span><span class="sxs-lookup"><span data-stu-id="c14cc-131">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c14cc-132">Os procedimentos neste tópico contém configurações comuns para criar e implantar um pacote e um programa e podem não abranger todas as configurações possíveis.</span><span class="sxs-lookup"><span data-stu-id="c14cc-132">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="c14cc-133">Para obter outras opções de implantação do Configuration Manager, consulte a [Biblioteca de documentação do Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="c14cc-133">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="c14cc-134">Implantando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c14cc-134">Deploying the .NET Framework</span></span>

<span data-ttu-id="c14cc-135">Você pode usar Configuration Manager para implantar uma instalação silenciosa do .NET Framework 4,5, em que os usuários não interagem com o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-135">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="c14cc-136">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="c14cc-136">Follow these steps:</span></span>

1. <span data-ttu-id="c14cc-137">[Crie uma coleção](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="c14cc-137">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="c14cc-138">[Crie um pacote e um programa para o .NET Framework redistribuível](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="c14cc-138">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="c14cc-139">[Selecione um ponto de distribuição](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="c14cc-139">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="c14cc-140">[Implante o pacote](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="c14cc-140">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="c14cc-141">Criar uma coleção</span><span class="sxs-lookup"><span data-stu-id="c14cc-141">Create a collection</span></span>

<span data-ttu-id="c14cc-142">Nesta etapa, você selecionará os computadores nos quais pacote e o programa serão implantados e os agrupará em uma coleção de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c14cc-142">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="c14cc-143">Para criar uma coleção no Configuration Manager, você pode usar regras de associação diretas (onde você especifica manualmente os membros da coleção) ou regras de consulta (onde o Configuration Manager determina os membros da coleção com base em critérios especificados).</span><span class="sxs-lookup"><span data-stu-id="c14cc-143">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="c14cc-144">Para obter mais informações sobre regras de associação, incluindo consultas e regras diretas, consulte [introdução às coleções em Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-144">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="c14cc-145">Para criar uma coleção:</span><span class="sxs-lookup"><span data-stu-id="c14cc-145">To create a collection:</span></span>

1. <span data-ttu-id="c14cc-146">No console do Configuration Manager, escolha **Ativos e Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-146">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="c14cc-147">No workspace **Ativos e Conformidade**, escolha **Coleções de Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-147">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="c14cc-148">Na guia **Início** do grupo **Criar**, escolha **Criar Coleção de Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-148">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="c14cc-149">Na página **Geral** do **Assistente de Criação de Coleção de Dispositivos**, insira um nome para a coleção.</span><span class="sxs-lookup"><span data-stu-id="c14cc-149">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="c14cc-150">Escolha **Procurar** para especificar uma coleção de restrição.</span><span class="sxs-lookup"><span data-stu-id="c14cc-150">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="c14cc-151">Na página **Regras de Associação**, escolha **Adicionar Regra** e escolha **Regra Direta** para abrir o **Assistente de Criação de Regra de Associação Direta**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-151">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="c14cc-152">Escolha **Próxima**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-152">Choose **Next**.</span></span>

7. <span data-ttu-id="c14cc-153">Na página **Pesquisar Recursos**, na lista **Classe de recurso**, escolha **Recurso do Sistema**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-153">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="c14cc-154">Na lista **Nome do atributo**, escolha **Nome**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-154">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="c14cc-155">No campo **Valor**, insira `%` e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-155">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="c14cc-156">Na página **Selecionar Recursos**, marque a caixa de seleção para cada computador no qual você deseja implantar o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c14cc-156">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="c14cc-157">Escolha **Avançar** e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-157">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="c14cc-158">Na página **Regras de Associação** do **Assistente de Criação de Coleção de Dispositivos**, escolha **Avançar** e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-158">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="c14cc-159">Crie um pacote e programa para o pacote .NET Framework redistribuível</span><span class="sxs-lookup"><span data-stu-id="c14cc-159">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="c14cc-160">As etapas a seguir criam, manualmente, um pacote para o .NET Framework redistribuível.</span><span class="sxs-lookup"><span data-stu-id="c14cc-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="c14cc-161">O pacote conterá os parâmetros especificados para instalar o .NET Framework e o local de onde o pacote será distribuído para os computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="c14cc-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="c14cc-162">Para criar um pacote:</span><span class="sxs-lookup"><span data-stu-id="c14cc-162">To create a package:</span></span>

1. <span data-ttu-id="c14cc-163">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-163">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="c14cc-164">No workspace **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="c14cc-165">Na guia **Início**, no grupo **Criar**, escolha **Criar Pacote**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="c14cc-166">Na página **Pacote** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="c14cc-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="c14cc-167">Nome: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="c14cc-167">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="c14cc-168">Fabricante: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="c14cc-168">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="c14cc-169">Idioma.</span><span class="sxs-lookup"><span data-stu-id="c14cc-169">Language.</span></span> `English (US)`

5. <span data-ttu-id="c14cc-170">Escolha **Este pacote contém arquivos de origem** e **Procurar** para selecionar a pasta de rede ou local que contém os arquivos de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c14cc-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="c14cc-171">Após selecionar a pasta, escolha **OK** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="c14cc-172">Na página **Tipo de Programa** do assistente, escolha **Programa Padrão** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="c14cc-173">Na página **Programa** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="c14cc-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="c14cc-174">**Nome:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="c14cc-174">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="c14cc-175">**Linha de comando:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (as opções de linha de comando são descritas na tabela após estas etapas)</span><span class="sxs-lookup"><span data-stu-id="c14cc-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="c14cc-176">**Executar:** escolha **Oculto**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-176">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="c14cc-177">**O programa pode ser executado:** escolha a opção que especifica que o programa pode ser executado independentemente de um usuário estar conectado.</span><span class="sxs-lookup"><span data-stu-id="c14cc-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="c14cc-178">Na página **Requisitos**, escolha **Avançar** para aceitar os valores padrão e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="c14cc-179">A tabela a seguir descreve as opções de linha de comando especificadas na etapa 7.</span><span class="sxs-lookup"><span data-stu-id="c14cc-179">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="c14cc-180">Opção</span><span class="sxs-lookup"><span data-stu-id="c14cc-180">Option</span></span>|<span data-ttu-id="c14cc-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="c14cc-181">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c14cc-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="c14cc-182">**/q**</span></span>|<span data-ttu-id="c14cc-183">Define o modo silencioso.</span><span class="sxs-lookup"><span data-stu-id="c14cc-183">Sets quiet mode.</span></span> <span data-ttu-id="c14cc-184">Nenhuma entrada do usuário é necessária e nenhuma saída é mostrada.</span><span class="sxs-lookup"><span data-stu-id="c14cc-184">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="c14cc-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="c14cc-185">**/norestart**</span></span>|<span data-ttu-id="c14cc-186">Impede que o programa de instalação reinicialize automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="c14cc-187">Se você usar essa opção, o Configuration Manager deverá processar a reinicialização do computador.</span><span class="sxs-lookup"><span data-stu-id="c14cc-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="c14cc-188">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="c14cc-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="c14cc-189">Especifica o nome do pacote que está fazendo o encadeamento.</span><span class="sxs-lookup"><span data-stu-id="c14cc-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="c14cc-190">Essa informação é relatada com outras informações da sessão de instalação para aqueles que se inscreveram no Programa de Aperfeiçoamento da Experiência do Usuário da Microsoft (CEIP).</span><span class="sxs-lookup"><span data-stu-id="c14cc-190">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="c14cc-191">Se o nome do pacote contiver espaços, use aspas duplas como delimitadores: **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="c14cc-192">Estas etapas criam um pacote chamado .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c14cc-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="c14cc-193">O programa implanta uma instalação silenciosa do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c14cc-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="c14cc-194">Em uma instalação silenciosa, os usuários não interagem com o processo de instalação e o aplicativo de encadeamento precisa capturar o código de retorno e manipular a reinicialização; consulte [Obtendo informações de progresso de um pacote de instalação](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c14cc-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="c14cc-195">Selecione um ponto de distribuição</span><span class="sxs-lookup"><span data-stu-id="c14cc-195">Select a distribution point</span></span>

<span data-ttu-id="c14cc-196">Para distribuir o pacote e o programa para computadores clientes de um servidor, primeiro designe um sistema de site como um ponto de distribuição e distribua o pacote para o ponto de distribuição.</span><span class="sxs-lookup"><span data-stu-id="c14cc-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="c14cc-197">Use as etapas a seguir para selecionar um ponto de distribuição para o pacote .NET Framework 4.5 criado na seção anterior:</span><span class="sxs-lookup"><span data-stu-id="c14cc-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="c14cc-198">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-198">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="c14cc-199">No workspace **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="c14cc-200">Na lista de pacotes, selecione o pacote **.NET Framework 4.5** que você criou na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="c14cc-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="c14cc-201">Na guia **Início** do grupo **Implantação**, escolha **Distribuir Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="c14cc-202">Na guia **Geral** do **Assistente para Distribuir Conteúdo**, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="c14cc-203">Na página **Destino de Conteúdo** do assistente, escolha **Adicionar** e **Ponto de Distribuição**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="c14cc-204">Na caixa de diálogo **Adicionar Pontos de Distribuição**, selecione os pontos de distribuição que hospedarão o pacote e o programa e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="c14cc-205">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-205">Complete the wizard.</span></span>

<span data-ttu-id="c14cc-206">O pacote agora conterá todas as informações que você precisa para implantar silenciosamente o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c14cc-206">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="c14cc-207">Antes de implantar o pacote e o programa, verifique se ele foi instalado no ponto de distribuição; consulte a seção "monitoramento de status de conteúdo" do [Monitor de conteúdo que você distribui com o Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) na biblioteca de documentação Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="c14cc-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="c14cc-208">Implantar o pacote</span><span class="sxs-lookup"><span data-stu-id="c14cc-208">Deploy the package</span></span>

<span data-ttu-id="c14cc-209">Para implantar o pacote e o programa .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="c14cc-209">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="c14cc-210">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-210">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="c14cc-211">No workspace **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="c14cc-212">Na lista de pacotes, selecione o pacote criado e denominado **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="c14cc-213">Na guia **Início**, no grupo **Implantação**, escolha **Implantar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="c14cc-214">Na página **Geral** do **Assistente de Implantação de Software**, escolha **Procurar** e selecione a coleção anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="c14cc-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="c14cc-215">Escolha **Próxima**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-215">Choose **Next**.</span></span>

6. <span data-ttu-id="c14cc-216">Na página **Conteúdo** do assistente, verifique se o ponto do qual você deseja distribuir o software é exibido e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="c14cc-217">Na página **Configurações de Implantação** do assistente, confirme se a **Ação** está definida como **Instalar** e a **Finalidade** como **Obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="c14cc-218">Isso garantirá que o pacote de software seja uma instalação obrigatória nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="c14cc-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="c14cc-219">Escolha **Próxima**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-219">Choose **Next**.</span></span>

8. <span data-ttu-id="c14cc-220">Na página **Agendamento** do assistente, especifique quando você deseja que o .NET Framework seja instalado.</span><span class="sxs-lookup"><span data-stu-id="c14cc-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="c14cc-221">Você pode escolher **Nova** para atribuir uma hora de instalação ou instruir o software a ser instalado quando o usuário fizer logon, logoff ou assim que possível.</span><span class="sxs-lookup"><span data-stu-id="c14cc-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="c14cc-222">Escolha **Próxima**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-222">Choose **Next**.</span></span>

9. <span data-ttu-id="c14cc-223">Na página **Experiência do Usuário** do assistente, use os valores padrão e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c14cc-224">O ambiente de produção pode ter políticas que exijam diferentes seleções de agendamento de implantação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="c14cc-225">Para obter informações sobre essas opções, confira [Propriedades de nome de anúncio: guia Agendamento](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="c14cc-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="c14cc-226">Na página **Pontos de Distribuição** do assistente, use os valores padrão e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="c14cc-227">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="c14cc-227">Complete the wizard.</span></span> <span data-ttu-id="c14cc-228">Você pode monitorar o progresso da implantação no nó **Implantações** do workspace **Monitoramento**.</span><span class="sxs-lookup"><span data-stu-id="c14cc-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="c14cc-229">O pacote agora será implantado na coleção de destino e a instalação silenciosa do .NET Framework 4.5 será iniciada.</span><span class="sxs-lookup"><span data-stu-id="c14cc-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="c14cc-230">Para obter informações sobre códigos de erro de instalação do .NET Framework 4.5, consulte a seção [Códigos de retorno](#return_codes) posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="c14cc-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="c14cc-231">Recursos</span><span class="sxs-lookup"><span data-stu-id="c14cc-231">Resources</span></span>

<span data-ttu-id="c14cc-232">Para obter mais informações sobre a infraestrutura para testar a implantação do pacote redistribuível do .NET Framework 4.5, veja os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c14cc-232">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="c14cc-233">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="c14cc-233">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="c14cc-234">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="c14cc-234">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="c14cc-235">Sistema de nome de domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="c14cc-235">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="c14cc-236">Protocolo DHCP</span><span class="sxs-lookup"><span data-stu-id="c14cc-236">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="c14cc-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="c14cc-237">**SQL Server 2008:**</span></span>

- <span data-ttu-id="c14cc-238">[Instalando o SQL Server 2008 (vídeo do SQL Server)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c14cc-238">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="c14cc-239">Visão geral de segurança do SQL Server 2008 para administradores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="c14cc-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="c14cc-240">**System Center 2012 Configuration Manager (ponto de gerenciamento, ponto de distribuição):**</span><span class="sxs-lookup"><span data-stu-id="c14cc-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="c14cc-241">Administração de site do System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="c14cc-241">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="c14cc-242">Planejando e implantando site único do Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="c14cc-242">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="c14cc-243">**Cliente do System Center 2012 Configuration Manager para computadores Windows:**</span><span class="sxs-lookup"><span data-stu-id="c14cc-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="c14cc-244">Implantação de clientes do System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="c14cc-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="c14cc-245">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c14cc-245">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="c14cc-246">Localizações dos arquivos de log</span><span class="sxs-lookup"><span data-stu-id="c14cc-246">Log file locations</span></span>

<span data-ttu-id="c14cc-247">Os seguintes arquivos de log são gerados durante a configuração do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c14cc-247">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="c14cc-248">%temp%\Microsoft .NET Framework *version* \* . txt</span><span class="sxs-lookup"><span data-stu-id="c14cc-248">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="c14cc-249">%temp%\Microsoft .NET Framework *versão* \* . html</span><span class="sxs-lookup"><span data-stu-id="c14cc-249">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="c14cc-250">em que *versão* é a versão do .NET Framework que você está instalando, como 4.5 ou 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="c14cc-250">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="c14cc-251">Também é possível especificar o diretório no qual os arquivos de log são gravados usando a opção de linha de comando `/log` no comando de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c14cc-251">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="c14cc-252">Para obter mais informações, consulte [Guia de implantação do .NET Framework para desenvolvedores](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="c14cc-252">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="c14cc-253">Você pode usar a [ferramenta de coleta de logs](https://www.microsoft.com/download/details.aspx?id=12493) para coletar os arquivos de log do .NET Framework e criar um arquivo de gabinete compactado (.cab) que reduz o tamanho dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="c14cc-253">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="c14cc-254">Códigos de retorno</span><span class="sxs-lookup"><span data-stu-id="c14cc-254">Return codes</span></span>

<span data-ttu-id="c14cc-255">A tabela a seguir lista os códigos de retorno mais comuns do programa de instalação redistribuível do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c14cc-255">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="c14cc-256">Os códigos de retorno são os mesmos para todas as versões do instalador.</span><span class="sxs-lookup"><span data-stu-id="c14cc-256">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="c14cc-257">Para obter links para informações detalhadas, consulte a próxima seção [Códigos de erro de download](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="c14cc-257">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="c14cc-258">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="c14cc-258">Return code</span></span>|<span data-ttu-id="c14cc-259">Descrição</span><span class="sxs-lookup"><span data-stu-id="c14cc-259">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="c14cc-260">0</span><span class="sxs-lookup"><span data-stu-id="c14cc-260">0</span></span>|<span data-ttu-id="c14cc-261">A instalação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="c14cc-261">Installation completed successfully.</span></span>|
|<span data-ttu-id="c14cc-262">1602</span><span class="sxs-lookup"><span data-stu-id="c14cc-262">1602</span></span>|<span data-ttu-id="c14cc-263">O usuário cancelou a instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-263">The user canceled installation.</span></span>|
|<span data-ttu-id="c14cc-264">1603</span><span class="sxs-lookup"><span data-stu-id="c14cc-264">1603</span></span>|<span data-ttu-id="c14cc-265">Um erro fatal ocorreu durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-265">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="c14cc-266">1641</span><span class="sxs-lookup"><span data-stu-id="c14cc-266">1641</span></span>|<span data-ttu-id="c14cc-267">É necessário reiniciar para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="c14cc-268">Esta mensagem indica êxito.</span><span class="sxs-lookup"><span data-stu-id="c14cc-268">This message indicates success.</span></span>|
|<span data-ttu-id="c14cc-269">3010</span><span class="sxs-lookup"><span data-stu-id="c14cc-269">3010</span></span>|<span data-ttu-id="c14cc-270">É necessário reiniciar para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="c14cc-270">A restart is required to complete the installation.</span></span> <span data-ttu-id="c14cc-271">Esta mensagem indica êxito.</span><span class="sxs-lookup"><span data-stu-id="c14cc-271">This message indicates success.</span></span>|
|<span data-ttu-id="c14cc-272">5100</span><span class="sxs-lookup"><span data-stu-id="c14cc-272">5100</span></span>|<span data-ttu-id="c14cc-273">O computador do usuário não atende aos requisitos do sistema.</span><span class="sxs-lookup"><span data-stu-id="c14cc-273">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="c14cc-274">Códigos de erro de download</span><span class="sxs-lookup"><span data-stu-id="c14cc-274">Download error codes</span></span>

- [<span data-ttu-id="c14cc-275">Códigos de erro do BITS (Serviço de Transferência Inteligente em Segundo Plano)</span><span class="sxs-lookup"><span data-stu-id="c14cc-275">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="c14cc-276">Códigos de erro do moniker de URL</span><span class="sxs-lookup"><span data-stu-id="c14cc-276">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="c14cc-277">Códigos de erro WinHttp</span><span class="sxs-lookup"><span data-stu-id="c14cc-277">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="c14cc-278">Outros códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="c14cc-278">Other error codes:</span></span>

- [<span data-ttu-id="c14cc-279">Códigos de erro do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="c14cc-279">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="c14cc-280">[Códigos de resultado do Windows Update Agent](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="c14cc-280">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="c14cc-281">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c14cc-281">See also</span></span>

- [<span data-ttu-id="c14cc-282">Guia de implantação para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="c14cc-282">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="c14cc-283">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="c14cc-283">System Requirements</span></span>](../get-started/system-requirements.md)
