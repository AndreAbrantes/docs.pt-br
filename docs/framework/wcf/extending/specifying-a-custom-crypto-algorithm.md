---
title: Especificando um algoritmo de criptografia personalizada
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: bdb7d45752be94c4c81e27161f57f765d64bd94a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293995"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="ef695-102">Especificando um algoritmo de criptografia personalizada</span><span class="sxs-lookup"><span data-stu-id="ef695-102">Specifying a Custom Crypto Algorithm</span></span>

<span data-ttu-id="ef695-103">O WCF permite que você especifique um algoritmo de criptografia personalizado a ser usado ao criptografar dados ou computação de assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="ef695-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="ef695-104">Isso é feito pelas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ef695-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="ef695-105">Derive uma classe de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="ef695-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="ef695-106">Registrar o algoritmo</span><span class="sxs-lookup"><span data-stu-id="ef695-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="ef695-107">Configure a associação com a <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe derivada.</span><span class="sxs-lookup"><span data-stu-id="ef695-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="ef695-108">Derive uma classe de SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ef695-108">Derive a class from SecurityAlgorithmSuite</span></span>  

 <span data-ttu-id="ef695-109">O <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> é uma classe base abstrata que permite que você especifique o algoritmo a ser usado ao executar várias operações relacionadas à segurança.</span><span class="sxs-lookup"><span data-stu-id="ef695-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="ef695-110">Por exemplo, computar um hash para uma assinatura digital ou criptografar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="ef695-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="ef695-111">O código a seguir mostra como derivar uma classe de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> :</span><span class="sxs-lookup"><span data-stu-id="ef695-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="ef695-112">Registrar o algoritmo personalizado</span><span class="sxs-lookup"><span data-stu-id="ef695-112">Register the Custom Algorithm</span></span>  

 <span data-ttu-id="ef695-113">O registro pode ser feito em um arquivo de configuração ou em código imperativo.</span><span class="sxs-lookup"><span data-stu-id="ef695-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="ef695-114">O registro de um algoritmo personalizado é feito criando-se um mapeamento entre uma classe que implementa um provedor de serviços de criptografia e um alias.</span><span class="sxs-lookup"><span data-stu-id="ef695-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="ef695-115">O alias é então mapeado para um URI que é usado ao especificar o algoritmo na associação do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ef695-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="ef695-116">O seguinte trecho de configuração ilustra como registrar um algoritmo personalizado na configuração:</span><span class="sxs-lookup"><span data-stu-id="ef695-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="ef695-117">A seção sob o <`cryptoClasses` elemento> cria o mapeamento entre o SHA256CryptoServiceProvider e o alias "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="ef695-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="ef695-118">O `nameEntry` elemento <> cria o mapeamento entre o alias "SHA256CSP" e a URL especificada `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="ef695-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="ef695-119">Para registrar o algoritmo personalizado no código, use o <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> método.</span><span class="sxs-lookup"><span data-stu-id="ef695-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="ef695-120">Esse método cria os dois mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="ef695-120">This method creates both mappings.</span></span> <span data-ttu-id="ef695-121">O exemplo a seguir mostra como chamar esse método:</span><span class="sxs-lookup"><span data-stu-id="ef695-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="ef695-122">Configurar a associação</span><span class="sxs-lookup"><span data-stu-id="ef695-122">Configure the Binding</span></span>  

 <span data-ttu-id="ef695-123">Você configura a associação especificando a <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe derivada personalizada nas configurações de associação, conforme mostrado no trecho de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ef695-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="ef695-124">Para obter um exemplo de código completo, consulte a [agilidade de criptografia no](../samples/cryptographic-agility-in-wcf-security.md) exemplo de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="ef695-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef695-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="ef695-125">See also</span></span>

- [<span data-ttu-id="ef695-126">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ef695-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ef695-127">Serviços de segurança</span><span class="sxs-lookup"><span data-stu-id="ef695-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="ef695-128">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="ef695-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="ef695-129">Conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="ef695-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
