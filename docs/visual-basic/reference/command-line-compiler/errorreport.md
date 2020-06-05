---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6a1c8fce17e3e5a54366c2ff4dff4e6aa668f56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408654"
---
# <a name="-errorreport"></a><span data-ttu-id="bfdac-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="bfdac-102">-errorreport</span></span>

<span data-ttu-id="bfdac-103">Especifica como o compilador de Visual Basic deve relatar erros internos do compilador.</span><span class="sxs-lookup"><span data-stu-id="bfdac-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfdac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfdac-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="bfdac-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfdac-105">Remarks</span></span>

<span data-ttu-id="bfdac-106">Essa opção fornece uma maneira conveniente de relatar um erro de compilador interno do Visual Basic (ICE) para a equipe de Visual Basic da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="bfdac-107">Por padrão, o compilador não envia informações à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="bfdac-108">No entanto, se você encontrar um erro interno do compilador, essa opção permitirá que você relate o erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="bfdac-109">Essas informações ajudarão os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bfdac-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="bfdac-110">A capacidade do usuário de enviar relatórios depende das permissões de política de computador e de usuário.</span><span class="sxs-lookup"><span data-stu-id="bfdac-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="bfdac-111">A tabela a seguir resume o efeito da `-errorreport` opção.</span><span class="sxs-lookup"><span data-stu-id="bfdac-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="bfdac-112">Opção</span><span class="sxs-lookup"><span data-stu-id="bfdac-112">Option</span></span>|<span data-ttu-id="bfdac-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="bfdac-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="bfdac-114">Se ocorrer um erro de compilador interno, uma caixa de diálogo aparecerá para que você possa exibir os dados exatos que o compilador coletou.</span><span class="sxs-lookup"><span data-stu-id="bfdac-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="bfdac-115">Você pode determinar se há alguma informação confidencial no relatório de erros e tomar uma decisão sobre se deseja enviá-la à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="bfdac-116">Se você decidir enviá-lo e as configurações de política de computador e de usuário permitirem, o compilador enviará os dados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="bfdac-117">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="bfdac-117">Queues the error report.</span></span> <span data-ttu-id="bfdac-118">Ao fazer logon com privilégios de administrador, você pode relatar quaisquer falhas desde a última vez que você fez logon (não será solicitado que você envie relatórios para falhas mais de uma vez a cada três dias).</span><span class="sxs-lookup"><span data-stu-id="bfdac-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="bfdac-119">Esse é o comportamento padrão quando a `-errorreport` opção não é especificada.</span><span class="sxs-lookup"><span data-stu-id="bfdac-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="bfdac-120">Se ocorrer um erro de compilador interno e as configurações de política de computador e de usuário permitirem, o compilador enviará os dados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="bfdac-121">A opção `-errorreport:send` tentará enviar automaticamente informações de erro à Microsoft se o relatório estiver habilitado pelo [relatório de erros do Windows](/windows/desktop/wer/windows-error-reporting) configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="bfdac-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="bfdac-122">Se ocorrer um erro interno do compilador, ele não será coletado nem enviado à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="bfdac-123">O compilador envia dados que incluem a pilha no momento do erro, que geralmente inclui um código-fonte.</span><span class="sxs-lookup"><span data-stu-id="bfdac-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="bfdac-124">Se `-errorreport` for usado com a opção [-bugreport](bugreport.md) , o arquivo de origem inteiro será enviado.</span><span class="sxs-lookup"><span data-stu-id="bfdac-124">If `-errorreport` is used with the [-bugreport](bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="bfdac-125">Essa opção é melhor usada com a opção [-bugreport](bugreport.md) , pois permite que os engenheiros da Microsoft reproduzam o erro mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="bfdac-125">This option is best used with the [-bugreport](bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="bfdac-126">A `-errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bfdac-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="bfdac-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfdac-127">Example</span></span>

<span data-ttu-id="bfdac-128">O código a seguir tenta compilar `T2.vb` e, se o compilador encontrar um erro de compilador interno, ele solicitará que você envie o relatório de erros à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfdac-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="bfdac-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="bfdac-129">See also</span></span>

- [<span data-ttu-id="bfdac-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfdac-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bfdac-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfdac-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="bfdac-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="bfdac-132">-bugreport</span></span>](bugreport.md)
