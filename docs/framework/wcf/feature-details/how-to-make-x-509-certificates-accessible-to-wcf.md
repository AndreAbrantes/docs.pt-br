---
title: Como criar certificados X.509 que podem ser acessados pelo WCF
description: Saiba como tornar um certificado X. 509 acessível ao WCF. O código do aplicativo deve especificar o nome e o local do repositório de certificados. Pode haver outros requisitos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 5cc1118640bcf1262d88cb8cdb39939ae315cae3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246864"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="17724-105">Como criar certificados X.509 que podem ser acessados pelo WCF</span><span class="sxs-lookup"><span data-stu-id="17724-105">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="17724-106">Para tornar um certificado X. 509 acessível a Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome e o local do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="17724-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="17724-107">Em determinadas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="17724-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="17724-108">Para obter a chave privada associada a um certificado X. 509 em um repositório de certificados, o WCF deve ter permissão para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="17724-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="17724-109">Por padrão, somente o proprietário e a conta do sistema podem acessar a chave privada de um certificado.</span><span class="sxs-lookup"><span data-stu-id="17724-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="17724-110">Para tornar os certificados X. 509 acessíveis para o WCF</span><span class="sxs-lookup"><span data-stu-id="17724-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="17724-111">Conceda à conta sob a qual o WCF está executando o acesso de leitura para o arquivo que contém a chave privada associada ao certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="17724-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="17724-112">Determine se o WCF requer acesso de leitura à chave privada para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="17724-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="17724-113">A tabela a seguir detalha se uma chave privada deve estar disponível ao usar um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="17724-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="17724-114">Uso do certificado X. 509</span><span class="sxs-lookup"><span data-stu-id="17724-114">X.509 certificate use</span></span>|<span data-ttu-id="17724-115">Chave privada</span><span class="sxs-lookup"><span data-stu-id="17724-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="17724-116">Assinando digitalmente uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="17724-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="17724-117">Yes</span><span class="sxs-lookup"><span data-stu-id="17724-117">Yes</span></span>|  
        |<span data-ttu-id="17724-118">Verificando a assinatura de uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="17724-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="17724-119">No</span><span class="sxs-lookup"><span data-stu-id="17724-119">No</span></span>|  
        |<span data-ttu-id="17724-120">Criptografar uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="17724-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="17724-121">No</span><span class="sxs-lookup"><span data-stu-id="17724-121">No</span></span>|  
        |<span data-ttu-id="17724-122">Descriptografar uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="17724-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="17724-123">Yes</span><span class="sxs-lookup"><span data-stu-id="17724-123">Yes</span></span>|  
  
    2. <span data-ttu-id="17724-124">Determine o local do repositório de certificados e o nome no qual o certificado está armazenado.</span><span class="sxs-lookup"><span data-stu-id="17724-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="17724-125">O repositório de certificados no qual o certificado é armazenado é especificado no código do aplicativo ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="17724-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="17724-126">Por exemplo, o exemplo a seguir especifica que o certificado está localizado no `CurrentUser` repositório de certificados chamado `My` .</span><span class="sxs-lookup"><span data-stu-id="17724-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="17724-127">Determine onde a chave privada do certificado está localizada no computador usando a ferramenta [FindPrivateKey](../samples/findprivatekey.md) .</span><span class="sxs-lookup"><span data-stu-id="17724-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="17724-128">A ferramenta [FindPrivateKey](../samples/findprivatekey.md) requer o nome do repositório de certificados, o local do repositório de certificados e algo que identifica exclusivamente o certificado.</span><span class="sxs-lookup"><span data-stu-id="17724-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="17724-129">A ferramenta aceita o nome da entidade do certificado ou sua impressão digital como um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="17724-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="17724-130">Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [como recuperar a impressão digital de um certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="17724-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="17724-131">O exemplo de código a seguir usa a ferramenta [FindPrivateKey](../samples/findprivatekey.md) para determinar o local da chave privada de um certificado no `My` repositório `CurrentUser` com uma impressão digital de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .</span><span class="sxs-lookup"><span data-stu-id="17724-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="17724-132">Determine a conta sob a qual o WCF está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="17724-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="17724-133">A tabela a seguir detalha a conta sob a qual o WCF está sendo executado para um determinado cenário.</span><span class="sxs-lookup"><span data-stu-id="17724-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="17724-134">Cenário</span><span class="sxs-lookup"><span data-stu-id="17724-134">Scenario</span></span>|<span data-ttu-id="17724-135">Identidade do processo</span><span class="sxs-lookup"><span data-stu-id="17724-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="17724-136">Cliente (aplicativo de console ou WinForms).</span><span class="sxs-lookup"><span data-stu-id="17724-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="17724-137">Usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="17724-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="17724-138">Serviço que é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="17724-138">Service that is self-hosted.</span></span>|<span data-ttu-id="17724-139">Usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="17724-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="17724-140">Serviço hospedado no IIS 6,0 (Windows Server 2003) ou IIS 7,0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="17724-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="17724-141">SERVIÇO DE REDE</span><span class="sxs-lookup"><span data-stu-id="17724-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="17724-142">Serviço hospedado no IIS 5. X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="17724-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="17724-143">Controlado pelo `<processModel>` elemento no arquivo de Machine.config.</span><span class="sxs-lookup"><span data-stu-id="17724-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="17724-144">A conta padrão é ASPNET.</span><span class="sxs-lookup"><span data-stu-id="17724-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="17724-145">Conceda acesso de leitura ao arquivo que contém a chave privada para a conta em que o WCF está sendo executado, usando uma ferramenta como o icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="17724-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="17724-146">O exemplo de código a seguir edita a DACL (lista de controle de acesso discricionário) do arquivo especificado para conceder à conta de serviço de rede acesso de leitura (: R) ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="17724-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="17724-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="17724-147">See also</span></span>

- [<span data-ttu-id="17724-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="17724-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="17724-149">Como recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="17724-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="17724-150">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="17724-150">Working with Certificates</span></span>](working-with-certificates.md)
