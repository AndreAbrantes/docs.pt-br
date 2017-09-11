---
title: "Não é possível emitir o assembly: &lt;mensagem de erro&gt; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
dev_langs:
- VB
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d15981a1a2fb31ba377066fa421f5a9979d47a12
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="112a4-102">Não é possível emitir o assembly: &lt;mensagem de erro&gt;</span><span class="sxs-lookup"><span data-stu-id="112a4-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="112a4-103">O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o Assembly Linker (Al.exe, também conhecido como Alink) para gerar um assembly com um manifesto, com o vinculador relatando um erro no estágio de emissão da criação do assembly.</span><span class="sxs-lookup"><span data-stu-id="112a4-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="112a4-104">**ID do erro:** BC30145</span><span class="sxs-lookup"><span data-stu-id="112a4-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="112a4-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="112a4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="112a4-106">Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para obter mais explicações e conselhos.</span><span class="sxs-lookup"><span data-stu-id="112a4-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="112a4-107">Tente assinar o assembly manualmente, usando o [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) ou [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="112a4-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="112a4-108">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="112a4-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="112a4-109">Para assinar o assembly manualmente</span><span class="sxs-lookup"><span data-stu-id="112a4-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="112a4-110">Use o [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23) para criar um arquivo de par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="112a4-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="112a4-111">Esse arquivo tem a extensão .snk.</span><span class="sxs-lookup"><span data-stu-id="112a4-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="112a4-112">Exclua a referência COM que está gerando o erro no projeto.</span><span class="sxs-lookup"><span data-stu-id="112a4-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="112a4-113">Do Windows **iniciar** , aponte para **programas**, aponte para **Microsoft Visual Studio 2008**, aponte para **Visual Studio Tools**e, em seguida, clique em **Prompt de comando do Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="112a4-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="112a4-114">Acesse o diretório onde deseja colocar o wrapper do assembly.</span><span class="sxs-lookup"><span data-stu-id="112a4-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="112a4-115">Digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="112a4-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="112a4-116">Um exemplo do código que pode ser inserido seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="112a4-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="112a4-117">Use aspas duplas (") se um caminho ou arquivo contiver espaços.</span><span class="sxs-lookup"><span data-stu-id="112a4-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="112a4-118">Em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], inclua uma referência .NET Assembly para o arquivo que acabou de ser criado.</span><span class="sxs-lookup"><span data-stu-id="112a4-118">In [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112a4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="112a4-119">See Also</span></span>  
 <span data-ttu-id="112a4-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="112a4-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="112a4-121"> [Ferramenta de Al.exe erros e avisos](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="112a4-121"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="112a4-122"> [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="112a4-122"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="112a4-123"> [Como criar um par de chaves pública/privada](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span><span class="sxs-lookup"><span data-stu-id="112a4-123"> [How to: Create a Public-Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span></span>  
<span data-ttu-id="112a4-124"> [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="112a4-124"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
