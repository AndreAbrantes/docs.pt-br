---
title: Criptografando dados
description: Saiba como criptografar dados no .NET usando um algoritmo simétrico ou um algoritmo assimétrico.
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 574ef3f829406d661e19f004e9a7d150954fd9e5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830591"
---
# <a name="encrypting-data"></a><span data-ttu-id="fd7d8-103">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="fd7d8-103">Encrypting Data</span></span>

<span data-ttu-id="fd7d8-104">A criptografia simétrica e a criptografia assimétrica são executadas usando processos diferentes.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="fd7d8-105">A criptografia simétrica é executada em fluxos e, portanto, é útil para criptografar grandes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="fd7d8-106">A criptografia assimétrica é executada em um pequeno número de bytes e, portanto, é útil apenas para pequenas quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="fd7d8-107">Criptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="fd7d8-107">Symmetric Encryption</span></span>  

<span data-ttu-id="fd7d8-108">As classes de criptografia simétrica gerenciadas são usadas com uma classe de fluxo especial chamada a <xref:System.Security.Cryptography.CryptoStream> que criptografa os dados lidos no fluxo.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="fd7d8-109">A classe **CryptoStream** é inicializada com uma classe de fluxo gerenciada, uma classe que implementa a <xref:System.Security.Cryptography.ICryptoTransform> interface (criada a partir de uma classe que implementa um algoritmo criptográfico) e uma <xref:System.Security.Cryptography.CryptoStreamMode> enumeração que descreve o tipo de acesso permitido para o **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="fd7d8-110">A classe **CryptoStream** pode ser inicializada usando qualquer classe derivada da <xref:System.IO.Stream> classe, incluindo <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> e <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="fd7d8-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="fd7d8-111">Usando essas classes, você pode executar a criptografia simétrica em uma variedade de objetos Stream.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="fd7d8-112">O exemplo a seguir ilustra como criar uma nova instância da classe de implementação padrão para o <xref:System.Security.Cryptography.Aes> algoritmo.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="fd7d8-113">A instância é usada para executar a criptografia em uma classe **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="fd7d8-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="fd7d8-114">Neste exemplo, o **CryptoStream** é inicializado com um objeto de fluxo chamado `myStream` que pode ser qualquer tipo de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="fd7d8-115">O método **Createencryptr** da classe **AES** é passado à chave e ao IV que são usados para criptografia.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="fd7d8-116">Nesse caso, a chave padrão e o IV gerados de `aes` são usados.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="fd7d8-117">Depois que esse código é executado, todos os dados gravados no objeto **CryptoStream** são criptografados usando o algoritmo AES.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="fd7d8-118">O exemplo a seguir mostra todo o processo de criação de um fluxo, criptografia do fluxo, gravação no fluxo e fechamento do fluxo.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="fd7d8-119">Este exemplo cria um fluxo de arquivos que é criptografado usando a classe **CryptoStream** e a classe **AES** .</span><span class="sxs-lookup"><span data-stu-id="fd7d8-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="fd7d8-120">O IV gerado é gravado no início de <xref:System.IO.FileStream> , portanto, ele pode ser lido e usado para descriptografia.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-120">Generated IV is written to beginning of <xref:System.IO.FileStream>, so it can be read and used for decryption.</span></span> <span data-ttu-id="fd7d8-121">Em seguida, uma mensagem é gravada no fluxo criptografado com a <xref:System.IO.StreamWriter> classe.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-121">Then a message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="fd7d8-122">Embora a mesma chave possa ser usada várias vezes para criptografar e descriptografar dados, é recomendável gerar um novo IV aleatório a cada vez.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-122">While the same key can be used multiple times to encrypt and decrypt data, it is recommended to generate a new random IV each time.</span></span> <span data-ttu-id="fd7d8-123">Dessa forma, os dados criptografados são sempre diferentes, mesmo quando o texto sem formatação é o mesmo.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-123">This way the encrypted data is always different, even when plain text is the same.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="fd7d8-124">O código criptografa o fluxo usando o algoritmo simétrico AES e grava o IV e, em seguida, criptografado "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="fd7d8-124">The code encrypts the stream using the AES symmetric algorithm, and writes IV and then encrypted "Hello World!"</span></span> <span data-ttu-id="fd7d8-125">para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-125">to the stream.</span></span> <span data-ttu-id="fd7d8-126">Se o código for bem-sucedido, ele criará um arquivo criptografado chamado *TestData.txt* e exibirá o seguinte texto no console:</span><span class="sxs-lookup"><span data-stu-id="fd7d8-126">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>
  
```console  
The text was encrypted.
```  

<span data-ttu-id="fd7d8-127">Você pode descriptografar o arquivo usando o exemplo de descriptografia simétrica na [descriptografia de dados](decrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="fd7d8-127">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="fd7d8-128">Esse exemplo e este exemplo especificam a mesma chave.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-128">That example and this example specify the same key.</span></span>

<span data-ttu-id="fd7d8-129">No entanto, se uma exceção for gerada, o código exibirá o seguinte texto no console:</span><span class="sxs-lookup"><span data-stu-id="fd7d8-129">However, if an exception is raised, the code displays the following text to the console:</span></span>
  
```console  
The encryption failed.
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="fd7d8-130">Criptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="fd7d8-130">Asymmetric Encryption</span></span>

<span data-ttu-id="fd7d8-131">Os algoritmos assimétrico geralmente são usados para criptografar pequenas quantidades de dados, como a criptografia de uma chave simétrica e IV.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-131">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="fd7d8-132">Normalmente, um indivíduo executando a criptografia assimétrica usa a chave pública gerada por outra entidade.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-132">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="fd7d8-133">A <xref:System.Security.Cryptography.RSA> classe é fornecida pelo .net para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-133">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="fd7d8-134">O exemplo a seguir usa informações de chave pública para criptografar uma chave simétrica e um IV.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-134">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="fd7d8-135">Duas matrizes de bytes são inicializadas que representam a chave pública de terceiros.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-135">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="fd7d8-136">Um <xref:System.Security.Cryptography.RSAParameters> objeto é inicializado para esses valores.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-136">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="fd7d8-137">Em seguida, o objeto **RSAParameters** (junto com a chave pública que ele representa) é importado para uma instância **RSA** usando o <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-137">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fd7d8-138">Por fim, a chave privada e o IV criados por uma <xref:System.Security.Cryptography.Aes> classe são criptografados.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-138">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="fd7d8-139">Este exemplo requer que os sistemas tenham a criptografia de 128 bits instalada.</span><span class="sxs-lookup"><span data-stu-id="fd7d8-139">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="fd7d8-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd7d8-140">See also</span></span>

- [<span data-ttu-id="fd7d8-141">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="fd7d8-141">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="fd7d8-142">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="fd7d8-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="fd7d8-143">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="fd7d8-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="fd7d8-144">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="fd7d8-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="fd7d8-145">Vulnerabilidades de temporização com descriptografia simétrica no modo CBC usando preenchimento</span><span class="sxs-lookup"><span data-stu-id="fd7d8-145">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="fd7d8-146">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd7d8-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
