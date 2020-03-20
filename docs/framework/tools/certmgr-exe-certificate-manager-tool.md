---
title: Certmgr.exe (ferramenta Gerenciador de Certificados)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: 06fe3a78d0b19720d4f83111980b88806312205f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129869"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="97749-102">Certmgr.exe (ferramenta Gerenciador de Certificados)</span><span class="sxs-lookup"><span data-stu-id="97749-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="97749-103">A ferramenta Gerenciador de Certificados (Certmgr.exe) gerencia certificados, CTLs (listas de certificados confiáveis) e CRLs (listas de certificados revogados).</span><span class="sxs-lookup"><span data-stu-id="97749-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="97749-104">O Gerenciador de Certificados é instalado automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97749-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="97749-105">Para iniciar a ferramenta, use os [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="97749-105">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97749-106">A ferramenta Gerenciador de Certificados (Certmgr.exe) é um utilitário de linha de comando, e Certificados (Certmgr.msc) é um snap-in MMC (Console de Gerenciamento Microsoft).</span><span class="sxs-lookup"><span data-stu-id="97749-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="97749-107">Como Certmgr.msc costuma ser encontrado no diretório do sistema do Windows, a digitação de `certmgr` na linha de comando pode carregar o snap-in do MMC de Certificados, mesmo que você tenha aberto o Prompt de Comando do Desenvolvedor para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97749-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="97749-108">Isso ocorre porque o caminho para o snap-in precede o caminho para a ferramenta Gerenciador de Certificados na variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="97749-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="97749-109">Se encontrar esse problema, você poderá executar comandos de Certmgr.exe especificando-se o caminho do executável.</span><span class="sxs-lookup"><span data-stu-id="97749-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="97749-110">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97749-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="97749-111">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="97749-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="97749-112">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="97749-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="97749-113">Para obter uma visão geral dos certificados X.509, consulte [Working with Certificates](../wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="97749-113">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="97749-114">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="97749-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97749-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97749-115">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="97749-116">parâmetros</span><span class="sxs-lookup"><span data-stu-id="97749-116">Parameters</span></span>  
  
|<span data-ttu-id="97749-117">Argumento</span><span class="sxs-lookup"><span data-stu-id="97749-117">Argument</span></span>|<span data-ttu-id="97749-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="97749-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="97749-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="97749-119">*sourceStorename*</span></span>|<span data-ttu-id="97749-120">O repositório de certificados que contém os certificados, as CTLs ou as CRLs existentes que serão adicionados, excluídos, salvos ou exibidos.</span><span class="sxs-lookup"><span data-stu-id="97749-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="97749-121">Ele pode ser um arquivo de repositório ou um repositório de sistemas.</span><span class="sxs-lookup"><span data-stu-id="97749-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="97749-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="97749-122">*destinationStorename*</span></span>|<span data-ttu-id="97749-123">O repositório ou o arquivo de certificados de saída.</span><span class="sxs-lookup"><span data-stu-id="97749-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="97749-124">Opção</span><span class="sxs-lookup"><span data-stu-id="97749-124">Option</span></span>|<span data-ttu-id="97749-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="97749-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97749-126">**/add**</span><span class="sxs-lookup"><span data-stu-id="97749-126">**/add**</span></span>|<span data-ttu-id="97749-127">Adiciona certificados, CTLs e CRLs a um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="97749-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="97749-128">**/all**</span><span class="sxs-lookup"><span data-stu-id="97749-128">**/all**</span></span>|<span data-ttu-id="97749-129">Adiciona todas as entradas quando usadas com **/add**.</span><span class="sxs-lookup"><span data-stu-id="97749-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="97749-130">Exclui todas as entradas quando usada com **/del**. Exibe todas as entradas quando usadas sem as opções **/add** **ou /del.**</span><span class="sxs-lookup"><span data-stu-id="97749-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="97749-131">A opção **/all** não pode ser usada com **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="97749-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="97749-132">**/c**</span></span>|<span data-ttu-id="97749-133">Adiciona certificados quando usados com **/add**.</span><span class="sxs-lookup"><span data-stu-id="97749-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="97749-134">Exclui certificados quando usado com **/del**. Salva certificados quando usado com **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="97749-135">Exibe certificados quando usados sem as opções **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="97749-136">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="97749-136">**/CRL**</span></span>|<span data-ttu-id="97749-137">Adiciona CRLs quando usadas com **/add**.</span><span class="sxs-lookup"><span data-stu-id="97749-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="97749-138">Exclui CRLs quando usado com **/del**. Salva CRLs quando usado com **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="97749-139">Exibe CRLs quando usadas sem a opção **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="97749-140">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="97749-140">**/CTL**</span></span>|<span data-ttu-id="97749-141">Adiciona CTLs quando usadas com **/add**.</span><span class="sxs-lookup"><span data-stu-id="97749-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="97749-142">Exclui CTLs quando usado com **/del**. Salva CTLs quando usado com **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="97749-143">Exibe CTLs quando usadas sem as opções **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="97749-144">**/del**</span><span class="sxs-lookup"><span data-stu-id="97749-144">**/del**</span></span>|<span data-ttu-id="97749-145">Exclui certificados, CTLs e CRLs de um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="97749-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="97749-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="97749-146">**/e** *encodingType*</span></span>|<span data-ttu-id="97749-147">Especifica o tipo de codificação do certificado.</span><span class="sxs-lookup"><span data-stu-id="97749-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="97749-148">O padrão é `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="97749-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="97749-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="97749-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="97749-150">Especifica o sinalizador de repositório aberto.</span><span class="sxs-lookup"><span data-stu-id="97749-150">Specifies the store open flag.</span></span> <span data-ttu-id="97749-151">Esse é o parâmetro *dwFlags* passado para **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="97749-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="97749-152">O valor padrão é CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="97749-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="97749-153">Essa opção só será ignorada se a opção **/y** for usada.</span><span class="sxs-lookup"><span data-stu-id="97749-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="97749-154">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="97749-154">**/h**[**elp**]</span></span>|<span data-ttu-id="97749-155">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="97749-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="97749-156">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="97749-156">**/n** *nam*</span></span>|<span data-ttu-id="97749-157">Especifica o nome comum do certificado a ser adicionado, excluído ou salvo.</span><span class="sxs-lookup"><span data-stu-id="97749-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="97749-158">Essa opção só pode ser usada com certificados; ela não pode ser usada com CTLs ou CRLs.</span><span class="sxs-lookup"><span data-stu-id="97749-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="97749-159">**/put**</span><span class="sxs-lookup"><span data-stu-id="97749-159">**/put**</span></span>|<span data-ttu-id="97749-160">Salva um certificado X.509, uma CTL ou uma CRL de um repositório de certificados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="97749-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="97749-161">O arquivo é salvo no formato X.509.</span><span class="sxs-lookup"><span data-stu-id="97749-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="97749-162">É possível usar a opção **/7** com a opção **/put** para salvar o arquivo no formato PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="97749-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="97749-163">A opção **/put** deve ser seguida por **/c**, **/CTL** ou **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="97749-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="97749-164">A opção **/all** não pode ser usada com **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="97749-165">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="97749-165">**/r** *location*</span></span>|<span data-ttu-id="97749-166">Identifica o local do Registro do repositório do sistema.</span><span class="sxs-lookup"><span data-stu-id="97749-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="97749-167">Essa opção só será ignorada se você especificar a opção **/s**.</span><span class="sxs-lookup"><span data-stu-id="97749-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="97749-168">*location* deve ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="97749-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="97749-169">-   `currentUser` indica que o repositório de certificados está na chave HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="97749-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="97749-170">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="97749-170">This is the default.</span></span><br /><span data-ttu-id="97749-171">-   `localMachine` indica que o repositório de certificados está na chave HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="97749-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="97749-172">**/s**</span><span class="sxs-lookup"><span data-stu-id="97749-172">**/s**</span></span>|<span data-ttu-id="97749-173">Indica que o repositório de certificados é um repositório do sistema.</span><span class="sxs-lookup"><span data-stu-id="97749-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="97749-174">Se você não especificar essa opção, o repositório será considerado um **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="97749-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="97749-175">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="97749-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="97749-176">Especifica o hash SHA1 do certificado, da CTL ou da CRL a ser adicionado, excluído ou salvo.</span><span class="sxs-lookup"><span data-stu-id="97749-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="97749-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="97749-177">**/v**</span></span>|<span data-ttu-id="97749-178">Especifica o modo detalhado; exibe informações detalhadas sobre certificados, CTLs e CRLs.</span><span class="sxs-lookup"><span data-stu-id="97749-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="97749-179">Essa opção não pode ser usada com as opções **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="97749-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="97749-180">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="97749-180">**/y** *provider*</span></span>|<span data-ttu-id="97749-181">Especifica o nome do provedor de repositório.</span><span class="sxs-lookup"><span data-stu-id="97749-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="97749-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="97749-182">**/7**</span></span>|<span data-ttu-id="97749-183">Salva o repositório de destino como um objeto PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="97749-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="97749-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="97749-184">**/?**</span></span>|<span data-ttu-id="97749-185">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="97749-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97749-186">Comentários</span><span class="sxs-lookup"><span data-stu-id="97749-186">Remarks</span></span>  
 <span data-ttu-id="97749-187">Certmgr.exe realiza as seguintes funções básicas:</span><span class="sxs-lookup"><span data-stu-id="97749-187">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="97749-188">Exibe certificados, CTLs e CRLs para o console.</span><span class="sxs-lookup"><span data-stu-id="97749-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="97749-189">Adiciona certificados, CTLs e CRLs a um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="97749-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="97749-190">Exclui certificados, CTLs e CRLs de um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="97749-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="97749-191">Salva um certificado X.509, uma CTL ou uma CRL de um repositório de certificados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="97749-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="97749-192">Certmgr.exe trabalha com dois tipos de repositórios de certificados: **StoreFile** e repositório do sistema.</span><span class="sxs-lookup"><span data-stu-id="97749-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="97749-193">Não é necessário especificar o tipo do repositório de certificados; Certmgr.exe pode identificar o tipo de repositório e realizar as operações apropriadas.</span><span class="sxs-lookup"><span data-stu-id="97749-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="97749-194">A execução de Certmgr.exe sem especificar opções inicia o snap-in certmgr.msc, que tem uma GUI que ajuda nas tarefas de gerenciamento do certificado também disponíveis na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="97749-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="97749-195">A GUI fornece um assistente de importação, que copia certificados, CTLs e CRLs do disco para um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="97749-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="97749-196">É possível encontrar os nomes de repositórios X509Certificate para os parâmetros `sourceStorename` e `destinationStorename` compilando e executando-se o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="97749-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="97749-197">Para obter mais informações sobre certificados, consulte [Working with Certificates](../wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="97749-197">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="97749-198">Exemplos</span><span class="sxs-lookup"><span data-stu-id="97749-198">Examples</span></span>  
 <span data-ttu-id="97749-199">O comando a seguir exibe um repositório de sistema padrão chamado `my` com saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="97749-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="97749-200">O comando a seguir adiciona todos os certificados em um arquivo chamado `myFile.ext` a um novo arquivo chamado `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="97749-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="97749-201">O comando a seguir adiciona o certificado em um arquivo chamado `testcert.cer` no repositório do sistema `my`.</span><span class="sxs-lookup"><span data-stu-id="97749-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="97749-202">O comando a seguir adiciona o certificado em um arquivo chamado `TrustedCert.cer` ao repositório de certificados raiz.</span><span class="sxs-lookup"><span data-stu-id="97749-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="97749-203">O comando a seguir salva um certificado com o nome comum `myCert` no repositório do sistema `my` em um arquivo chamado `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="97749-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="97749-204">O comando a seguir exclui todas as CTLs no repositório do sistema `my` e o repositório resultante em um arquivo chamado `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="97749-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="97749-205">O comando a seguir salva um certificado no repositório do sistema `my` no arquivo `newFile`.</span><span class="sxs-lookup"><span data-stu-id="97749-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="97749-206">Você deverá inserir o número do certificado em `my` a ser colocado em `newFile`.</span><span class="sxs-lookup"><span data-stu-id="97749-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="97749-207">Confira também</span><span class="sxs-lookup"><span data-stu-id="97749-207">See also</span></span>

- [<span data-ttu-id="97749-208">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="97749-208">Tools</span></span>](index.md)
- [<span data-ttu-id="97749-209">Makecert.exe (Ferramenta de Criação de Certificado)</span><span class="sxs-lookup"><span data-stu-id="97749-209">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="97749-210">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="97749-210">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
