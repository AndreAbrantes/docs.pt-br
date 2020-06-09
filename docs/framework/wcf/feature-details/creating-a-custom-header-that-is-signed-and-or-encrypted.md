---
title: Criar um cabeçalho personalizado que é assinado e/ou criptografado
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0adb4100bca1add2c23ff2c802ddb5e2cb1c368c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579652"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="16179-102">Criar um cabeçalho personalizado que é assinado e/ou criptografado</span><span class="sxs-lookup"><span data-stu-id="16179-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="16179-103">Ao chamar um serviço não WCF usando um cliente WCF, às vezes, é necessário usar cabeçalhos SOAP personalizados.</span><span class="sxs-lookup"><span data-stu-id="16179-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="16179-104">Há um bug de canonização no WCF que impede que os cabeçalhos personalizados assinados e criptografados trabalhem com um serviço não WCF.</span><span class="sxs-lookup"><span data-stu-id="16179-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="16179-105">O problema é causado pela canonização incorreta de namespaces XML padrão.</span><span class="sxs-lookup"><span data-stu-id="16179-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="16179-106">Isso só é problemático ao chamar serviços não WCF com cabeçalhos personalizados assinados e/ou criptografados.</span><span class="sxs-lookup"><span data-stu-id="16179-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="16179-107">Quando o serviço recebe a mensagem que contém o cabeçalho personalizado assinado e/ou criptografado, ele não pode verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="16179-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="16179-108">Essa solução alternativa evita o bug de canonização, permite a interoperabilidade com serviços não WCF, mas não impede a interoperabilidade com os serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="16179-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="16179-109">Definindo o cabeçalho personalizado</span><span class="sxs-lookup"><span data-stu-id="16179-109">Defining the custom header</span></span>  
 <span data-ttu-id="16179-110">Os cabeçalhos personalizados são definidos definindo um contrato de mensagem e marcando os membros que você deseja que sejam enviados como cabeçalhos com um <xref:System.ServiceModel.MessageHeaderAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="16179-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="16179-111">Para contornar o bug de canonização, você deve garantir que o serializador XML declare o namespace para o cabeçalho personalizado com um prefixo em vez de uma declaração de namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="16179-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="16179-112">O código a seguir mostra como definir o tipo de dados que será usado como um cabeçalho de mensagem com a declaração de namespace correta.</span><span class="sxs-lookup"><span data-stu-id="16179-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```csharp
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="16179-113">Esse código declara um novo tipo chamado `msgHeaderElement` que será serializado com o serializador XML.</span><span class="sxs-lookup"><span data-stu-id="16179-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="16179-114">Quando uma instância desse tipo é serializada, ela definirá um namespace com um prefixo ' h ', trabalhando em todo o bug de canonização.</span><span class="sxs-lookup"><span data-stu-id="16179-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="16179-115">Em seguida, o contrato de mensagem definiria uma instância de `msgHeaderElement` e marcá-la com o <xref:System.ServiceModel.MessageHeaderAttribute> atributo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="16179-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="16179-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16179-116">See also</span></span>

- [<span data-ttu-id="16179-117">Contrato padrão de mensagem</span><span class="sxs-lookup"><span data-stu-id="16179-117">Default Message Contract</span></span>](../samples/default-message-contract.md)
- [<span data-ttu-id="16179-118">Contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="16179-118">Message Contracts</span></span>](../samples/message-contracts.md)
- [<span data-ttu-id="16179-119">Utilizando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="16179-119">Using Message Contracts</span></span>](using-message-contracts.md)
