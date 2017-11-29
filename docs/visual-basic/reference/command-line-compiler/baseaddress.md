---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be88bf4834ca58b1fe708eb1ef7188c583fef0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress"></a><span data-ttu-id="a7078-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="a7078-102">/baseaddress</span></span>
<span data-ttu-id="a7078-103">Especifica um endereço base padrão ao criar uma DLL.</span><span class="sxs-lookup"><span data-stu-id="a7078-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7078-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7078-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7078-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7078-105">Arguments</span></span>  
  
|<span data-ttu-id="a7078-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a7078-106">Term</span></span>|<span data-ttu-id="a7078-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a7078-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="a7078-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a7078-108">Required.</span></span> <span data-ttu-id="a7078-109">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="a7078-109">The base address for the DLL.</span></span> <span data-ttu-id="a7078-110">Esse endereço deve ser especificado como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a7078-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7078-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7078-111">Remarks</span></span>  
 <span data-ttu-id="a7078-112">O endereço de base de uma DLL padrão é definido pelo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7078-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="a7078-113">Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada.</span><span class="sxs-lookup"><span data-stu-id="a7078-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="a7078-114">Por exemplo, se você especificar 0x11110001, ele é arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="a7078-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="a7078-115">Para concluir o processo de assinatura para uma DLL, use o `–R` opção da ferramenta de nomeação forte (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="a7078-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="a7078-116">Essa opção será ignorada se o destino não é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="a7078-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="a7078-117">Para definir /baseaddress no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a7078-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="a7078-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="a7078-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a7078-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a7078-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a7078-120">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="a7078-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="a7078-121">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a7078-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="a7078-122">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="a7078-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="a7078-123">4.  Modificar o valor de **endereço de base DLL:** caixa.</span><span class="sxs-lookup"><span data-stu-id="a7078-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="a7078-124">**Observação:** o **endereço de base DLL:** caixa é somente leitura, a menos que o destino é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="a7078-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7078-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7078-125">See Also</span></span>  
 [<span data-ttu-id="a7078-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7078-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a7078-127">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7078-127">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="a7078-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7078-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a7078-129">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="a7078-129">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)
