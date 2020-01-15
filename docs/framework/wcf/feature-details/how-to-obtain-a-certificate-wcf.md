---
title: Como obter um certificado (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: bfe6dcfe6850ee17a7bbb59f3a6ccad6c3c3e7d7
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964238"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="dce2c-102">Como obter um certificado (WCF)</span><span class="sxs-lookup"><span data-stu-id="dce2c-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="dce2c-103">Para usar qualquer um dos recursos de Windows Communication Foundation (WCF) que usam certificados X. 509, primeiro você obtém certificados.</span><span class="sxs-lookup"><span data-stu-id="dce2c-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="dce2c-104">Para obter um certificado X. 509</span><span class="sxs-lookup"><span data-stu-id="dce2c-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="dce2c-105">Escolha uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="dce2c-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="dce2c-106">Compre um certificado de uma autoridade de certificação, como a VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="dce2c-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="dce2c-107">Configure seu próprio serviço de certificado e faça com que uma autoridade de certificação assine os certificados.</span><span class="sxs-lookup"><span data-stu-id="dce2c-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="dce2c-108">O Windows Server 2003, o Windows 2000 Server, o Windows 2000 Server Datacenter e o Windows 2000 Datacenter Server incluem serviços de certificados que dão suporte à PKI (infraestrutura de chave pública).</span><span class="sxs-lookup"><span data-stu-id="dce2c-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="dce2c-109">No Windows Server 2008, use a função de [serviços de certificados Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) para gerenciar uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="dce2c-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="dce2c-110">Configure seu próprio serviço de certificado e não tenha os certificados assinados.</span><span class="sxs-lookup"><span data-stu-id="dce2c-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dce2c-111">Seja qual for a abordagem adotada, o destinatário da solicitação SOAP que contém o certificado X. 509 deve confiar no certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="dce2c-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="dce2c-112">Isso significa que o certificado X. 509 ou um emissor na cadeia de certificados está no repositório de certificados de pessoas confiáveis e que o certificado X. 509 não está no repositório de certificados não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="dce2c-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce2c-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="dce2c-113">See also</span></span>

- [<span data-ttu-id="dce2c-114">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="dce2c-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dce2c-115">Como criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="dce2c-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
