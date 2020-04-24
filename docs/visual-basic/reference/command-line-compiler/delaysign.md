---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581265"
---
# <a name="-delaysign"></a><span data-ttu-id="d0be0-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="d0be0-102">-delaysign</span></span>

<span data-ttu-id="d0be0-103">Especifica se o assembly será assinado total ou parcialmente.</span><span class="sxs-lookup"><span data-stu-id="d0be0-103">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0be0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0be0-104">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="d0be0-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d0be0-105">Arguments</span></span>

<span data-ttu-id="d0be0-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d0be0-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="d0be0-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d0be0-107">Optional.</span></span> <span data-ttu-id="d0be0-108">Use `-delaysign-` se você quiser um assembly totalmente assinado.</span><span class="sxs-lookup"><span data-stu-id="d0be0-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="d0be0-109">Use `-delaysign+` se você quiser posicionar a chave pública no assembly e reservar espaço para o hash assinado.</span><span class="sxs-lookup"><span data-stu-id="d0be0-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="d0be0-110">O padrão é `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="d0be0-110">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0be0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0be0-111">Remarks</span></span>

<span data-ttu-id="d0be0-112">A `-delaysign` opção não tem nenhum efeito, a menos que seja usada com [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="d0be0-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>

<span data-ttu-id="d0be0-113">Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular.</span><span class="sxs-lookup"><span data-stu-id="d0be0-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="d0be0-114">A assinatura digital resultante é armazenada no arquivo que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="d0be0-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="d0be0-115">Quando um assembly é assinado com atraso, o compilador não computa e armazena a assinatura, mas reserva espaço no arquivo para que a assinatura possa ser adicionada posteriormente.</span><span class="sxs-lookup"><span data-stu-id="d0be0-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="d0be0-116">Por exemplo, usando `-delaysign+`o, um desenvolvedor em uma organização pode distribuir versões de teste não assinadas de um assembly que os testadores podem registrar com o cache de assembly global e usar.</span><span class="sxs-lookup"><span data-stu-id="d0be0-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="d0be0-117">Quando o trabalho no assembly é concluído, a pessoa responsável pela chave privada da organização pode assinar totalmente o assembly.</span><span class="sxs-lookup"><span data-stu-id="d0be0-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="d0be0-118">Essa compartimentalização protege a chave privada da organização contra a divulgação, ao mesmo tempo que permite que todos os desenvolvedores trabalhem nos assemblies.</span><span class="sxs-lookup"><span data-stu-id="d0be0-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="d0be0-119">Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="d0be0-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="d0be0-120">Para Set-delaysign no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0be0-120">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="d0be0-121">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="d0be0-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d0be0-122">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d0be0-122">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="d0be0-123">Clique na guia **Assinatura** .</span><span class="sxs-lookup"><span data-stu-id="d0be0-123">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="d0be0-124">Defina o valor na caixa **somente assinatura de atraso** .</span><span class="sxs-lookup"><span data-stu-id="d0be0-124">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0be0-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0be0-125">See also</span></span>

- [<span data-ttu-id="d0be0-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0be0-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d0be0-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="d0be0-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="d0be0-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="d0be0-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="d0be0-129">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0be0-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
