---
title: 'Como: criptografar elementos XML com chaves assimétricas'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSA class
- asymmetric keys [.NET]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- encryption [.NET], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 29fe7c229664b08c9e1563413525818f2e883198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729337"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="35c8e-102">Como: criptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="35c8e-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="35c8e-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="35c8e-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="35c8e-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="35c8e-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="35c8e-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="35c8e-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="35c8e-106">Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um `EncryptedData` elemento <> que contenha os dados XML criptografados.</span><span class="sxs-lookup"><span data-stu-id="35c8e-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="35c8e-107">O `EncryptedData` elemento> de <também pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.</span><span class="sxs-lookup"><span data-stu-id="35c8e-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="35c8e-108">A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="35c8e-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="35c8e-109">O exemplo de código neste procedimento mostra como criar um elemento <`EncryptedData`> juntamente com vários outros subelementos que você pode usar posteriormente durante a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="35c8e-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="35c8e-110">Este exemplo criptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="35c8e-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="35c8e-111">Ele gera um par de chaves pública/privada RSA e salva o par de chaves em um contêiner de chave segura.</span><span class="sxs-lookup"><span data-stu-id="35c8e-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="35c8e-112">Em seguida, o exemplo cria uma chave de sessão separada usando o algoritmo de criptografia AES (AES).</span><span class="sxs-lookup"><span data-stu-id="35c8e-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm.</span></span>  <span data-ttu-id="35c8e-113">O exemplo usa a chave de sessão AES para criptografar o documento XML e, em seguida, usa a chave pública RSA para criptografar a chave de sessão AES.</span><span class="sxs-lookup"><span data-stu-id="35c8e-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="35c8e-114">Por fim, o exemplo salva a chave de sessão AES criptografada e os dados XML criptografados no documento XML em um novo `EncryptedData` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="35c8e-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="35c8e-115">Para descriptografar o elemento XML, recupere a chave privada RSA do contêiner de chave, use-a para descriptografar a chave de sessão e, em seguida, use a chave de sessão para descriptografar o documento.</span><span class="sxs-lookup"><span data-stu-id="35c8e-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="35c8e-116">Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves assimétricas](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="35c8e-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="35c8e-117">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="35c8e-118">Para criptografar um elemento XML com uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="35c8e-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="35c8e-119">Crie um <xref:System.Security.Cryptography.CspParameters> objeto e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="35c8e-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="35c8e-120">Gere uma chave simétrica usando a <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="35c8e-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="35c8e-121">A chave é salva automaticamente no contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor da <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="35c8e-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="35c8e-122">Essa chave será usada para criptografar a chave de sessão AES e poderá ser recuperada posteriormente para descriptografá-la.</span><span class="sxs-lookup"><span data-stu-id="35c8e-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="35c8e-123">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="35c8e-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="35c8e-124">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="35c8e-125">Localize o elemento especificado no <xref:System.Xml.XmlDocument> objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="35c8e-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="35c8e-126">Neste exemplo, o `"creditcard"` elemento é criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="35c8e-127">Crie uma nova chave de sessão usando a <xref:System.Security.Cryptography.Aes> classe.</span><span class="sxs-lookup"><span data-stu-id="35c8e-127">Create a new session key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="35c8e-128">Essa chave irá criptografar o elemento XML e, em seguida, será criptografada e colocada no documento XML.</span><span class="sxs-lookup"><span data-stu-id="35c8e-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="35c8e-129">Crie uma nova instância da <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e use-a para criptografar o elemento especificado usando a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="35c8e-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="35c8e-130">O <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> método retorna o elemento Encrypted como uma matriz de bytes criptografados.</span><span class="sxs-lookup"><span data-stu-id="35c8e-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="35c8e-131">Construa um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto e popule-o com o identificador de URL do elemento XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="35c8e-132">Esse identificador de URL permite que uma parte descriptografada saiba que o XML contém um elemento criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="35c8e-133">Você pode usar o <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> campo para especificar o identificador de URL.</span><span class="sxs-lookup"><span data-stu-id="35c8e-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="35c8e-134">O elemento XML de texto não criptografado será substituído por um `EncryptedData` elemento <> encapsulado por esse <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="35c8e-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="35c8e-135">Crie um <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto que é inicializado para o identificador de URL do algoritmo criptográfico usado para gerar a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="35c8e-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="35c8e-136">Passe o <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto para a <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="35c8e-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="35c8e-137">Crie um <xref:System.Security.Cryptography.Xml.EncryptedKey> objeto para conter a chave de sessão criptografada.</span><span class="sxs-lookup"><span data-stu-id="35c8e-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="35c8e-138">Criptografe a chave de sessão, adicione-a ao <xref:System.Security.Cryptography.Xml.EncryptedKey> objeto e insira um nome de chave de sessão e uma URL de identificador de chave.</span><span class="sxs-lookup"><span data-stu-id="35c8e-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="35c8e-139">Crie um novo <xref:System.Security.Cryptography.Xml.DataReference> objeto que mapeie os dados criptografados para uma chave de sessão específica.</span><span class="sxs-lookup"><span data-stu-id="35c8e-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="35c8e-140">Essa etapa opcional permite que você especifique facilmente que várias partes de um documento XML foram criptografadas por uma única chave.</span><span class="sxs-lookup"><span data-stu-id="35c8e-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="35c8e-141">Adicione a chave criptografada ao <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="35c8e-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="35c8e-142">Crie um novo <xref:System.Security.Cryptography.Xml.KeyInfo> objeto para especificar o nome da chave RSA.</span><span class="sxs-lookup"><span data-stu-id="35c8e-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="35c8e-143">Adicione-o ao <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="35c8e-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="35c8e-144">Isso ajuda a parte descriptografada a identificar a chave assimétrica correta a ser usada ao descriptografar a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="35c8e-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="35c8e-145">Adicione os dados do elemento criptografado ao <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="35c8e-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="35c8e-146">Substitua o elemento do objeto original <xref:System.Xml.XmlDocument> pelo <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.</span><span class="sxs-lookup"><span data-stu-id="35c8e-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="35c8e-147">Salve o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="35c8e-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="35c8e-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35c8e-148">Example</span></span>  

 <span data-ttu-id="35c8e-149">Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="35c8e-150">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="35c8e-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="35c8e-151">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="35c8e-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35c8e-152">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="35c8e-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="35c8e-153">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="35c8e-153">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="35c8e-154">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="35c8e-154">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="35c8e-155">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="35c8e-155">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="35c8e-156">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="35c8e-156">.NET Security</span></span>

<span data-ttu-id="35c8e-157">Nunca armazene uma chave de criptografia simétrica em texto não criptografado ou transfira uma chave simétrica entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-157">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="35c8e-158">Além disso, nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="35c8e-158">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="35c8e-159">Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="35c8e-159">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="35c8e-160">Nunca incorpore uma chave diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="35c8e-160">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="35c8e-161">Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="35c8e-161">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
<span data-ttu-id="35c8e-162">Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="35c8e-162">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="35c8e-163">Às vezes, as chaves criptográficas podem ser lidas da memória por um depurador ou lidas de um disco rígido se o local da memória for paginado no disco.</span><span class="sxs-lookup"><span data-stu-id="35c8e-163">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c8e-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="35c8e-164">See also</span></span>

- [<span data-ttu-id="35c8e-165">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="35c8e-165">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="35c8e-166">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="35c8e-166">Cryptographic Services</span></span>](cryptographic-services.md)
- <span data-ttu-id="35c8e-167">[Criptografia de plataforma cruzada](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span><span class="sxs-lookup"><span data-stu-id="35c8e-167">[Cross-Platform Cryptography](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span></span>
- [<span data-ttu-id="35c8e-168">Como descriptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="35c8e-168">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](how-to-decrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="35c8e-169">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="35c8e-169">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
