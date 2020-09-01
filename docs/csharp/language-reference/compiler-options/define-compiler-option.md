---
description: -define (opções do compilador C#)
title: -define (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125872"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="c3bab-103">-define (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c3bab-103">-define (C# Compiler Options)</span></span>
<span data-ttu-id="c3bab-104">A opção **-define** define `name` como um símbolo em todos os arquivos de código-fonte do seu programa.</span><span class="sxs-lookup"><span data-stu-id="c3bab-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3bab-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3bab-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3bab-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c3bab-106">Arguments</span></span>  
 <span data-ttu-id="c3bab-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="c3bab-107">`name`, `name2`</span></span>  
 <span data-ttu-id="c3bab-108">O nome de um ou mais símbolos que você deseja definir.</span><span class="sxs-lookup"><span data-stu-id="c3bab-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3bab-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3bab-109">Remarks</span></span>  
 <span data-ttu-id="c3bab-110">A opção **-define** tem o mesmo efeito que usar uma diretiva de pré-processador [#define](../preprocessor-directives/preprocessor-define.md), exceto que a opção do compilador está em vigor para todos os arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="c3bab-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="c3bab-111">Um símbolo permanece definido em um arquivo de origem até que uma diretiva [#undef](../preprocessor-directives/preprocessor-undef.md) remova a definição no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="c3bab-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="c3bab-112">Quando você usa a opção -define, uma diretiva `#undef` em um arquivo não terá nenhum efeito em outros arquivos de código-fonte no projeto.</span><span class="sxs-lookup"><span data-stu-id="c3bab-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="c3bab-113">Você pode usar os símbolos criados por essa opção com [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md) e [#endif](../preprocessor-directives/preprocessor-endif.md) para compilar os arquivos de origem condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="c3bab-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="c3bab-114">**-d** é a forma abreviada de **-define**.</span><span class="sxs-lookup"><span data-stu-id="c3bab-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="c3bab-115">Você pode definir vários símbolos com **-define**, usando um ponto e vírgula ou uma vírgula para separar os nomes dos símbolos.</span><span class="sxs-lookup"><span data-stu-id="c3bab-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="c3bab-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3bab-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="c3bab-117">O compilador do C# não define símbolos ou macros que podem ser usados em seu código-fonte. Todas as definições de símbolo devem ser definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c3bab-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3bab-118">O `#define` do C# não permite que um valor seja dado a um símbolo, como nas linguagens como a C++.</span><span class="sxs-lookup"><span data-stu-id="c3bab-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="c3bab-119">Por exemplo, `#define` não pode ser usado para criar uma macro ou para definir uma constante.</span><span class="sxs-lookup"><span data-stu-id="c3bab-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="c3bab-120">Se você precisar definir uma constante, use uma variável `enum`.</span><span class="sxs-lookup"><span data-stu-id="c3bab-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="c3bab-121">Se você quiser criar uma macro de estilo C++, considere alternativas como os genéricos.</span><span class="sxs-lookup"><span data-stu-id="c3bab-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="c3bab-122">Como as macros são notoriamente propensas a erros, o C# não permite o uso delas, mas oferece alternativas mais seguras.</span><span class="sxs-lookup"><span data-stu-id="c3bab-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c3bab-123">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3bab-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c3bab-124">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="c3bab-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c3bab-125">Na guia **Build**, digite o símbolo que deve ser definido na caixa **Símbolos de build condicional**.</span><span class="sxs-lookup"><span data-stu-id="c3bab-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="c3bab-126">Por exemplo, se você estiver usando o exemplo de código a seguir, basta digitar `xx` na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="c3bab-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="c3bab-127">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3bab-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3bab-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3bab-128">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3bab-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3bab-129">See also</span></span>

- [<span data-ttu-id="c3bab-130">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="c3bab-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c3bab-131">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="c3bab-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
