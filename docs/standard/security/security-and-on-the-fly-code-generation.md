---
title: Segurança e geração de código durante a execução
description: Gerar código em nome de código menos confiável que é executado em uma confiança mais alta é uma preocupação de segurança, especialmente quando um chamador pode influenciar a geração de código.
ms.date: 07/15/2020
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: c94da31f464a5272dd3f3c9f767a40ba7ad88a47
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824142"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="6c4ea-103">Segurança e geração de código durante a execução</span><span class="sxs-lookup"><span data-stu-id="6c4ea-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="6c4ea-104">Algumas bibliotecas operam gerando código e executando-o para executar alguma operação para o chamador.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="6c4ea-105">O problema básico é gerar código em nome de código menos confiável e executá-lo em uma relação de confiança maior.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="6c4ea-106">O problema piora quando o chamador pode influenciar a geração de código, portanto, você deve garantir que apenas o código considerado seguro seja gerado.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="6c4ea-107">Você precisa saber exatamente o código que está gerando em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="6c4ea-108">Isso significa que você deve ter controles estritos sobre quaisquer valores obtidos de um usuário, sejam eles cadeias de caracteres entre aspas (que devem ser precedidas para que não possam incluir elementos de código inesperados), identificadores (que devem ser verificados para verificar se são identificadores válidos) ou qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="6c4ea-109">Os identificadores podem ser perigosos porque um assembly compilado pode ser modificado para que seus identificadores contenham caracteres estranhos, o que provavelmente irá quebrá-lo (embora isso raramente seja uma vulnerabilidade de segurança).</span><span class="sxs-lookup"><span data-stu-id="6c4ea-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="6c4ea-110">É recomendável que você gere código com emissão de reflexo, o que geralmente ajuda a evitar muitos desses problemas.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="6c4ea-111">Ao compilar o código, considere se há alguma maneira como um programa mal-intencionado pode modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="6c4ea-112">Há uma pequena janela de tempo durante a qual o código mal-intencionado pode alterar o código-fonte no disco antes que o compilador o leia ou antes que seu código carregue o arquivo. dll?</span><span class="sxs-lookup"><span data-stu-id="6c4ea-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="6c4ea-113">Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma lista de controle de acesso no sistema de arquivos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="6c4ea-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4ea-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c4ea-114">See also</span></span>

- [<span data-ttu-id="6c4ea-115">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="6c4ea-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="6c4ea-116">Segurança de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c4ea-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
