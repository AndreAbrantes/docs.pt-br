---
title: Assegurando a integridade dos dados com códigos hash
description: Saiba como garantir a integridade dos dados usando códigos de hash no .NET. Um valor de hash é um valor numérico de um comprimento fixo que identifica dados exclusivamente.
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET], hash
- data integrity
- checking hash codes
- encryption [.NET], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 085a0ea387e3415e6e916bcdf9055ffaa6753fef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831085"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="ac3f3-104">Assegurando a integridade dos dados com códigos hash</span><span class="sxs-lookup"><span data-stu-id="ac3f3-104">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="ac3f3-105">Um valor de hash é um valor numérico de um comprimento fixo que identifica dados exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-105">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="ac3f3-106">Os valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que sejam usados com assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-106">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="ac3f3-107">Você pode assinar um valor de hash com mais eficiência do que assinar o valor maior.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-107">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="ac3f3-108">Os valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguros.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-108">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="ac3f3-109">O valor de hash dos dados recebidos pode ser comparado ao valor de hash dos dados conforme eles foram enviados para determinar se os dados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-109">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
<span data-ttu-id="ac3f3-110">Este tópico descreve como gerar e verificar os códigos de hash usando as classes no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-110">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="ac3f3-111">Gerando um hash</span><span class="sxs-lookup"><span data-stu-id="ac3f3-111">Generating a Hash</span></span>

 <span data-ttu-id="ac3f3-112">As classes de hash gerenciadas podem aplicar hash a uma matriz de bytes ou a um objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-112">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="ac3f3-113">O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-113">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="ac3f3-114">O exemplo usa a <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes com hash usando a <xref:System.Security.Cryptography.SHA256> classe.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-114">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA256> class.</span></span> <span data-ttu-id="ac3f3-115">O valor de hash é exibido para o console.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-115">The hash value is then displayed to the console.</span></span>  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="ac3f3-116">Esse código exibirá a seguinte cadeia de caracteres para o console:</span><span class="sxs-lookup"><span data-stu-id="ac3f3-116">This code will display the following string to the console:</span></span>  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="ac3f3-117">Verificando um hash</span><span class="sxs-lookup"><span data-stu-id="ac3f3-117">Verifying a Hash</span></span>

 <span data-ttu-id="ac3f3-118">Os dados podem ser comparados a um valor de hash para determinar sua integridade.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-118">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="ac3f3-119">Normalmente, os dados são codificados em hash em um determinado momento e o valor de hash é protegido de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-119">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="ac3f3-120">Mais tarde, os dados podem ser codificados novamente e comparados com o valor protegido.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-120">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="ac3f3-121">Se os valores de hash forem correspondentes, os dados não foram alterados.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-121">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="ac3f3-122">Se os valores não corresponderem, os dados ficarão corrompidos.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-122">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="ac3f3-123">Para que esse sistema funcione, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-123">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="ac3f3-124">O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres com um novo valor de hash.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-124">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="ac3f3-125">Este exemplo percorre cada byte dos valores de hash e faz uma comparação.</span><span class="sxs-lookup"><span data-stu-id="ac3f3-125">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="ac3f3-126">Se os dois valores de hash corresponderem, esse código exibirá o seguinte no console:</span><span class="sxs-lookup"><span data-stu-id="ac3f3-126">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="ac3f3-127">Se eles não corresponderem, o código exibirá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac3f3-127">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac3f3-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="ac3f3-128">See also</span></span>

- [<span data-ttu-id="ac3f3-129">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="ac3f3-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="ac3f3-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="ac3f3-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="ac3f3-131">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="ac3f3-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="ac3f3-132">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ac3f3-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
