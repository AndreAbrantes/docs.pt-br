---
title: 'Como: criar certificados temporários para uso durante o desenvolvimento'
description: Saiba como usar um cmdlet do PowerShell para criar dois certificados X. 509 temporários para uso no desenvolvimento de um cliente ou serviço WCF seguro.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 0907f7f8a3767db9d83e5deaae1d86141fbee7b0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557405"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="62230-103">Como: criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="62230-103">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="62230-104">Ao desenvolver um serviço ou cliente seguro usando Windows Communication Foundation (WCF), geralmente é necessário fornecer um certificado X. 509 para ser usado como uma credencial.</span><span class="sxs-lookup"><span data-stu-id="62230-104">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="62230-105">O certificado normalmente faz parte de uma cadeia de certificados com uma autoridade raiz encontrada no repositório de autoridades de certificação raiz confiáveis do computador.</span><span class="sxs-lookup"><span data-stu-id="62230-105">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="62230-106">Ter uma cadeia de certificados permite que você defina o escopo de um conjunto de certificados em que normalmente a autoridade raiz é de sua organização ou unidade de negócios.</span><span class="sxs-lookup"><span data-stu-id="62230-106">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="62230-107">Para emular isso no momento do desenvolvimento, você pode criar dois certificados para atender aos requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="62230-107">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="62230-108">O primeiro é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis e o segundo certificado é criado a partir do primeiro e é colocado no repositório pessoal do local do computador local ou no repositório pessoal do local do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="62230-108">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="62230-109">Este tópico percorre as etapas para criar esses dois certificados usando o cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62230-109">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62230-110">Os certificados que o cmdlet New-SelfSignedCertificate gera são fornecidos apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="62230-110">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="62230-111">Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="62230-111">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="62230-112">Isso pode ser de um servidor de certificado do Windows Server em sua organização ou de terceiros.</span><span class="sxs-lookup"><span data-stu-id="62230-112">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="62230-113">Por padrão, o cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cria certificados que são autoassinados e esses certificados são inseguros.</span><span class="sxs-lookup"><span data-stu-id="62230-113">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="62230-114">Colocar os certificados autoassinados no repositório de autoridades de certificação raiz confiáveis permite que você crie um ambiente de desenvolvimento que simula mais de forma mais minuciosa seu ambiente de implantação.</span><span class="sxs-lookup"><span data-stu-id="62230-114">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="62230-115">Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="62230-115">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="62230-116">Para obter mais informações sobre como usar um certificado como uma credencial, consulte [protegendo serviços e clientes](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="62230-116">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="62230-117">Para obter um tutorial sobre como usar a tecnologia Authenticode da Microsoft, consulte [visões gerais e tutoriais do Authenticode](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="62230-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="62230-118">Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada</span><span class="sxs-lookup"><span data-stu-id="62230-118">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="62230-119">O comando a seguir cria um certificado autoassinado com o nome da entidade "RootCA" no repositório pessoal do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="62230-119">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="62230-120">Precisamos exportar o certificado para um arquivo PFX para que ele possa ser importado para onde for necessário em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="62230-120">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="62230-121">Ao exportar um certificado com a chave privada, é necessária uma senha para protegê-lo.</span><span class="sxs-lookup"><span data-stu-id="62230-121">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="62230-122">Salvamos a senha em um `SecureString` e usamos o cmdlet [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) para exportar o certificado com a chave privada associada para um arquivo PFX.</span><span class="sxs-lookup"><span data-stu-id="62230-122">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="62230-123">Também salvamos apenas o certificado público em um arquivo CRT usando o cmdlet [Export-Certificate](/powershell/module/pkiclient/export-certificate) .</span><span class="sxs-lookup"><span data-stu-id="62230-123">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="62230-124">Para criar um novo certificado assinado por um certificado de autoridade raiz</span><span class="sxs-lookup"><span data-stu-id="62230-124">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="62230-125">O comando a seguir cria um certificado assinado pelo `RootCA` com um nome de assunto de "SignedByRootCA" usando a chave privada do emissor.</span><span class="sxs-lookup"><span data-stu-id="62230-125">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="62230-126">Da mesma forma, salvamos o certificado assinado com a chave privada em um arquivo PFX e apenas a chave pública em um arquivo CRT.</span><span class="sxs-lookup"><span data-stu-id="62230-126">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="62230-127">Instalando um certificado no repositório de autoridades de certificação raiz confiáveis</span><span class="sxs-lookup"><span data-stu-id="62230-127">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="62230-128">Depois que um certificado autoassinado for criado, você poderá instalá-lo no repositório de autoridades de certificação raiz confiáveis.</span><span class="sxs-lookup"><span data-stu-id="62230-128">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="62230-129">Todos os certificados assinados com o certificado neste momento são confiáveis para o computador.</span><span class="sxs-lookup"><span data-stu-id="62230-129">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="62230-130">Por esse motivo, exclua o certificado da loja assim que você não precisar mais dele.</span><span class="sxs-lookup"><span data-stu-id="62230-130">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="62230-131">Quando você exclui esse certificado de autoridade raiz, todos os outros certificados assinados com ele se tornam não autorizados.</span><span class="sxs-lookup"><span data-stu-id="62230-131">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="62230-132">Os certificados de autoridade raiz são simplesmente um mecanismo no qual um grupo de certificados pode ser definido como sendo necessário.</span><span class="sxs-lookup"><span data-stu-id="62230-132">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="62230-133">Por exemplo, em aplicativos ponto a ponto, normalmente não há necessidade de uma autoridade raiz porque você simplesmente confia na identidade de um indivíduo por seu certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="62230-133">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="62230-134">Para instalar um certificado autoassinado nas autoridades de certificação raiz confiáveis</span><span class="sxs-lookup"><span data-stu-id="62230-134">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="62230-135">Abra o snap-in certificado.</span><span class="sxs-lookup"><span data-stu-id="62230-135">Open the certificate snap-in.</span></span> <span data-ttu-id="62230-136">Para saber mais, consulte [Como Exibir Certificados com o Snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="62230-136">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="62230-137">Abra a pasta para armazenar o certificado, o **computador local** ou o **usuário atual**.</span><span class="sxs-lookup"><span data-stu-id="62230-137">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="62230-138">Abra a pasta **autoridades de certificação raiz confiáveis** .</span><span class="sxs-lookup"><span data-stu-id="62230-138">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="62230-139">Clique com o botão direito do mouse na pasta **certificados** e clique em **todas as tarefas**e clique em **importar**.</span><span class="sxs-lookup"><span data-stu-id="62230-139">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="62230-140">Siga as instruções do assistente na tela para importar o RootCA. pfx para o repositório.</span><span class="sxs-lookup"><span data-stu-id="62230-140">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="62230-141">Usando certificados com o WCF</span><span class="sxs-lookup"><span data-stu-id="62230-141">Using certificates With WCF</span></span>

<span data-ttu-id="62230-142">Depois de configurar os certificados temporários, você pode usá-los para desenvolver soluções WCF que especificam certificados como um tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="62230-142">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="62230-143">Por exemplo, a configuração XML a seguir especifica a segurança da mensagem e um certificado como o tipo de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="62230-143">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="62230-144">Para especificar um certificado como o tipo de credencial do cliente</span><span class="sxs-lookup"><span data-stu-id="62230-144">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="62230-145">No arquivo de configuração para um serviço, use o XML a seguir para definir o modo de segurança como mensagem e o tipo de credencial do cliente como certificado.</span><span class="sxs-lookup"><span data-stu-id="62230-145">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
        <binding name="CertificateForClient">
          <security>
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

2. <span data-ttu-id="62230-146">No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado é encontrado no repositório do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor "CohoWinery".</span><span class="sxs-lookup"><span data-stu-id="62230-146">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="CertForClient">
          <clientCredentials>
            <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

<span data-ttu-id="62230-147">Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhando com certificados](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="62230-147">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="62230-148">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62230-148">.NET Framework security</span></span>

<span data-ttu-id="62230-149">Certifique-se de excluir qualquer certificado de autoridade raiz temporário das **autoridades de certificação raiz confiáveis** e pastas **pessoais** clicando com o botão direito do mouse no certificado e clicando em **excluir**.</span><span class="sxs-lookup"><span data-stu-id="62230-149">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="62230-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="62230-150">See also</span></span>

- [<span data-ttu-id="62230-151">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="62230-151">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="62230-152">Como: exibir certificados com o snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="62230-152">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="62230-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="62230-153">Securing Services and Clients</span></span>](securing-services-and-clients.md)
