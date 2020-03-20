---
title: Como criar certificados X.509 que podem ser acessados pelo WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184902"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="d2698-102">Como criar certificados X.509 que podem ser acessados pelo WCF</span><span class="sxs-lookup"><span data-stu-id="d2698-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="d2698-103">Para tornar um certificado X.509 acessível ao Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome e o local da loja de certificados.</span><span class="sxs-lookup"><span data-stu-id="d2698-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="d2698-104">Em certas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d2698-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="d2698-105">Para obter a chave privada associada a um certificado X.509 em uma loja de certificados, o WCF deve ter permissão para fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="d2698-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="d2698-106">Por padrão, apenas o proprietário e a conta do Sistema podem acessar a chave privada de um certificado.</span><span class="sxs-lookup"><span data-stu-id="d2698-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="d2698-107">Para tornar os certificados X.509 acessíveis ao WCF</span><span class="sxs-lookup"><span data-stu-id="d2698-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="d2698-108">Dê a conta a qual o WCF está executando acesso de leitura ao arquivo que contém a chave privada associada ao certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d2698-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="d2698-109">Determine se o WCF requer acesso à chave privada para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d2698-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="d2698-110">A tabela a seguir detalha se uma chave privada deve estar disponível ao usar um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d2698-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="d2698-111">Uso do certificado X.509</span><span class="sxs-lookup"><span data-stu-id="d2698-111">X.509 certificate use</span></span>|<span data-ttu-id="d2698-112">Chave privada</span><span class="sxs-lookup"><span data-stu-id="d2698-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="d2698-113">Assinando digitalmente uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="d2698-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="d2698-114">Sim</span><span class="sxs-lookup"><span data-stu-id="d2698-114">Yes</span></span>|  
        |<span data-ttu-id="d2698-115">Verificando a assinatura de uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="d2698-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="d2698-116">Não</span><span class="sxs-lookup"><span data-stu-id="d2698-116">No</span></span>|  
        |<span data-ttu-id="d2698-117">Criptografando uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="d2698-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="d2698-118">Não</span><span class="sxs-lookup"><span data-stu-id="d2698-118">No</span></span>|  
        |<span data-ttu-id="d2698-119">Descriptografando uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="d2698-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="d2698-120">Sim</span><span class="sxs-lookup"><span data-stu-id="d2698-120">Yes</span></span>|  
  
    2. <span data-ttu-id="d2698-121">Determine o local e o nome da loja de certificados em que o certificado é armazenado.</span><span class="sxs-lookup"><span data-stu-id="d2698-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="d2698-122">A loja de certificados em que o certificado é armazenado é especificada no código do aplicativo ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="d2698-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="d2698-123">Por exemplo, o exemplo a seguir especifica que `CurrentUser` o `My`certificado está localizado na loja de certificados nomeada .</span><span class="sxs-lookup"><span data-stu-id="d2698-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="d2698-124">Determine onde a chave privada do certificado está localizada no computador usando a ferramenta [FindPrivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)</span><span class="sxs-lookup"><span data-stu-id="d2698-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="d2698-125">A ferramenta [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) requer o nome da loja de certificados, a localização da loja de certificados e algo que identifica exclusivamente o certificado.</span><span class="sxs-lookup"><span data-stu-id="d2698-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="d2698-126">A ferramenta aceita o nome do assunto do certificado ou sua impressão digital como um identificador único.</span><span class="sxs-lookup"><span data-stu-id="d2698-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="d2698-127">Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [Como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d2698-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="d2698-128">O exemplo de código a seguir usa a ferramenta [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) para `My` determinar `CurrentUser` a localização `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`da chave privada de um certificado na loja com uma impressão digital de .</span><span class="sxs-lookup"><span data-stu-id="d2698-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="d2698-129">Determine a conta em que o WCF está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="d2698-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="d2698-130">A tabela a seguir detalha a conta a qual o WCF está executando para um determinado cenário.</span><span class="sxs-lookup"><span data-stu-id="d2698-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="d2698-131">Cenário</span><span class="sxs-lookup"><span data-stu-id="d2698-131">Scenario</span></span>|<span data-ttu-id="d2698-132">Identidade do processo</span><span class="sxs-lookup"><span data-stu-id="d2698-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="d2698-133">Cliente (aplicativo de console ou WinForms).</span><span class="sxs-lookup"><span data-stu-id="d2698-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="d2698-134">Atualmente logado no usuário.</span><span class="sxs-lookup"><span data-stu-id="d2698-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="d2698-135">Serviço que é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="d2698-135">Service that is self-hosted.</span></span>|<span data-ttu-id="d2698-136">Atualmente logado no usuário.</span><span class="sxs-lookup"><span data-stu-id="d2698-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="d2698-137">Serviço hospedado no IIS 6.0 (Windows Server 2003) ou IIS 7.0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="d2698-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="d2698-138">SERVIÇO DE REDE</span><span class="sxs-lookup"><span data-stu-id="d2698-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="d2698-139">Serviço hospedado no IIS 5.X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="d2698-139">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="d2698-140">Controlado pelo `<processModel>` elemento no arquivo Machine.config.</span><span class="sxs-lookup"><span data-stu-id="d2698-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="d2698-141">A conta padrão é ASPNET.</span><span class="sxs-lookup"><span data-stu-id="d2698-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="d2698-142">Conceder acesso de leitura ao arquivo que contém a chave privada da conta em que o WCF está executando, usando uma ferramenta como icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="d2698-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="d2698-143">O exemplo do código a seguir emite a lista de controle de acesso discricionário (DACL) para o arquivo especificado para conceder à conta DO SERVIÇO DE REDE acesso lido (:R) ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="d2698-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="d2698-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2698-144">See also</span></span>

- [<span data-ttu-id="d2698-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="d2698-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="d2698-146">Como recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="d2698-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="d2698-147">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="d2698-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
