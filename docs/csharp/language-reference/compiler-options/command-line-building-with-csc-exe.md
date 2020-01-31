---
title: Build pela linha de comando com csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789865"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="000e4-102">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="000e4-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="000e4-103">Você pode invocar o compilador do C#, digitando o nome do seu arquivo executável (*csc.exe*) em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="000e4-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="000e4-104">Se você usar a janela do **Prompt de Comando do Desenvolvedor do Visual Studio**, todas as variáveis de ambiente necessárias serão definidas para você.</span><span class="sxs-lookup"><span data-stu-id="000e4-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="000e4-105">Para obter informações sobre como acessar essa ferramenta, consulte o tópico [Prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="000e4-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="000e4-106">Se você usa uma janela de Prompt de Comando padrão, deve ajustar seu caminho antes de invocar o *csc.exe* de qualquer subdiretório em seu computador.</span><span class="sxs-lookup"><span data-stu-id="000e4-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="000e4-107">Você também deve executar o *vsvars32.bat* para definir as variáveis de ambiente adequadas para dar suporte aos builds de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="000e4-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="000e4-108">Para obter mais informações sobre o *vsvars32. bat*, incluindo instruções sobre como encontrá-lo e executá-lo, consulte [como definir variáveis de ambiente para a linha de comando do Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="000e4-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="000e4-109">Se estiver trabalhando em um computador que tenha apenas o SDK (Software Development Kit) do Windows, você poderá usar o compilador do C# no **Prompt de Comando do SDK**, que é aberto na opção de menu **Microsoft .NET Framework SDK**.</span><span class="sxs-lookup"><span data-stu-id="000e4-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="000e4-110">Você também pode usar o MSBuild para compilar programas em C# programaticamente.</span><span class="sxs-lookup"><span data-stu-id="000e4-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="000e4-111">Para mais informações, consulte [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="000e4-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="000e4-112">O arquivo executável *csc.exe* normalmente está localizado na pasta Microsoft.NET\Framework\\ *\<Versão>* no diretório *Windows*.</span><span class="sxs-lookup"><span data-stu-id="000e4-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="000e4-113">O local pode variar dependendo da configuração exata de um computador específico.</span><span class="sxs-lookup"><span data-stu-id="000e4-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="000e4-114">Se mais de uma versão do .NET Framework estiver instalada em seu computador, você encontrará várias versões desse arquivo.</span><span class="sxs-lookup"><span data-stu-id="000e4-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="000e4-115">Para obter mais informações sobre essas instalações, consulte [Determinando qual versão do .NET Framework está instalada](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="000e4-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="000e4-116">Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir o comando **csc** e suas opções de compilador associadas na janela **Saída**.</span><span class="sxs-lookup"><span data-stu-id="000e4-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="000e4-117">Para exibir essas informações, siga as instruções em [Como exibir, salvar e configurar arquivos de log de build](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log), para alterar o nível de detalhes dos dados de log para **Normal** ou **Detalhado**.</span><span class="sxs-lookup"><span data-stu-id="000e4-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="000e4-118">Depois de recompilar o projeto, pesquise na janela **Saída** por **csc** para localizar a invocação do compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="000e4-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="000e4-119">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="000e4-119">**In this topic**</span></span>

- [<span data-ttu-id="000e4-120">Regras para sintaxe de linha de comando</span><span class="sxs-lookup"><span data-stu-id="000e4-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="000e4-121">Linhas de comando de exemplo</span><span class="sxs-lookup"><span data-stu-id="000e4-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="000e4-122">Diferenças entre as saídas dos compiladores do C# e do C++</span><span class="sxs-lookup"><span data-stu-id="000e4-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="000e4-123">Regras para sintaxe de linha de comando para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="000e4-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="000e4-124">O compilador do C# usa as seguintes regras para interpretar os argumentos fornecidos na linha de comando do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="000e4-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="000e4-125">Os argumentos são delimitados por espaço em branco, que é um espaço ou uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="000e4-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="000e4-126">O caractere de acento circunflexo (^) não é reconhecido como um caractere de escape ou um delimitador.</span><span class="sxs-lookup"><span data-stu-id="000e4-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="000e4-127">O caractere é tratado pelo analisador de linha de comando no sistema operacional antes de ser passado para a matriz `argv` no programa.</span><span class="sxs-lookup"><span data-stu-id="000e4-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="000e4-128">Uma cadeia de caracteres entre aspas duplas ("cadeia de caracteres") é interpretada como um único argumento, independentemente do espaço em branco que está contido nela.</span><span class="sxs-lookup"><span data-stu-id="000e4-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="000e4-129">Uma cadeia de caracteres entre aspas pode ser inserida em um argumento.</span><span class="sxs-lookup"><span data-stu-id="000e4-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="000e4-130">Aspas duplas precedidas por uma barra invertida (\\") são interpretados como um caractere literal de aspas duplas (").</span><span class="sxs-lookup"><span data-stu-id="000e4-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="000e4-131">As barras invertidas são interpretadas literalmente, a menos que precedam imediatamente as aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="000e4-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="000e4-132">Se um número par de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão interpretadas como um delimitador de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="000e4-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="000e4-133">Se um número ímpar de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão "escapadas" pela barra invertida restante.</span><span class="sxs-lookup"><span data-stu-id="000e4-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="000e4-134">Isso fará com que aspas duplas (") literais sejam adicionadas na `argv`.</span><span class="sxs-lookup"><span data-stu-id="000e4-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="000e4-135">Linhas de comando de exemplo para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="000e4-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="000e4-136">Compila o *File.cs* produzindo o *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="000e4-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="000e4-137">Compila o *File.cs* produzindo o *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="000e4-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="000e4-138">Compila o *File.cs* e cria o *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="000e4-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="000e4-139">Compila todos os arquivos do C# no diretório atual, com otimizações habilitadas e define o símbolo de DEPURAÇÃO.</span><span class="sxs-lookup"><span data-stu-id="000e4-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="000e4-140">A saída é *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="000e4-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="000e4-141">Compila todos os arquivos do C# no diretório atual, produzindo uma versão de depuração de *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="000e4-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="000e4-142">Logotipos e avisos não são exibidos:</span><span class="sxs-lookup"><span data-stu-id="000e4-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="000e4-143">Compila todos os arquivos do C# no diretório atual para *Something.xyz* (uma DLL):</span><span class="sxs-lookup"><span data-stu-id="000e4-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="000e4-144">Diferenças entre as saídas dos compiladores do C# e do C++</span><span class="sxs-lookup"><span data-stu-id="000e4-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="000e4-145">Não há arquivos de objeto ( *.obj*) criados como resultado da invocação do compilador do C#. Os arquivos de saída são criados diretamente.</span><span class="sxs-lookup"><span data-stu-id="000e4-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="000e4-146">Como um resultado disso, o compilador do C# não precisa de um vinculador.</span><span class="sxs-lookup"><span data-stu-id="000e4-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="000e4-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="000e4-147">See also</span></span>

- [<span data-ttu-id="000e4-148">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="000e4-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="000e4-149">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="000e4-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="000e4-150">Opções do compilador de C# listadas por categoria</span><span class="sxs-lookup"><span data-stu-id="000e4-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="000e4-151">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="000e4-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="000e4-152">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="000e4-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="000e4-153">Como exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="000e4-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="000e4-154">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="000e4-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
