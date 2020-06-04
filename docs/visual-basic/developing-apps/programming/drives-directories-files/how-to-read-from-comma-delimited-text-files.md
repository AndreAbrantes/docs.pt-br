---
title: 'Como: ler de arquivos de texto delimitados por vírgula'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411636"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="7c017-102">Como ler em arquivos de texto separados por vírgulas no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c017-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="7c017-103">O objeto `TextFieldParser` fornece uma maneira fácil e eficiente de analisar arquivos de texto estruturados, como logs.</span><span class="sxs-lookup"><span data-stu-id="7c017-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="7c017-104">A propriedade `TextFieldType` define se ele é um arquivo delimitado ou um arquivo com campos de texto de largura fixa.</span><span class="sxs-lookup"><span data-stu-id="7c017-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="7c017-105">Para analisar um arquivo de texto delimitado por vírgulas</span><span class="sxs-lookup"><span data-stu-id="7c017-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="7c017-106">Crie um `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="7c017-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="7c017-107">O código a seguir cria o `TextFieldParser` chamado `MyReader` e abre o arquivo `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="7c017-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="7c017-108">Defina o delimitador e o tipo `TextField`.</span><span class="sxs-lookup"><span data-stu-id="7c017-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="7c017-109">O código a seguir define a propriedade `TextFieldType` como `Delimited` e o delimitador como “,”.</span><span class="sxs-lookup"><span data-stu-id="7c017-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="7c017-110">Percorra em loop os campos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="7c017-110">Loop through the fields in the file.</span></span> <span data-ttu-id="7c017-111">Se alguma linha estiver corrompida, relate um erro e continue a análise.</span><span class="sxs-lookup"><span data-stu-id="7c017-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="7c017-112">O código a seguir faz um loop pelo arquivo, exibindo cada campo por sua vez e relatando quaisquer campos que estejam formatados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="7c017-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="7c017-113">Feche os blocos `While` e `Using` com `End While` e `End Using`.</span><span class="sxs-lookup"><span data-stu-id="7c017-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="7c017-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c017-114">Example</span></span>  

 <span data-ttu-id="7c017-115">Este exemplo lê do arquivo `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="7c017-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7c017-116">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="7c017-116">Robust programming</span></span>  

 <span data-ttu-id="7c017-117">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="7c017-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7c017-118">Não é possível analisar uma linha usando o formato especificado (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="7c017-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="7c017-119">A mensagem de exceção especifica a linha causando a exceção, enquanto a propriedade <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> é atribuída ao texto contido na linha.</span><span class="sxs-lookup"><span data-stu-id="7c017-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="7c017-120">O arquivo especificado não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="7c017-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="7c017-121">Uma situação de confiança parcial na qual o usuário não tem permissões suficientes para acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="7c017-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="7c017-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="7c017-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="7c017-123">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7c017-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="7c017-124">O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="7c017-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c017-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c017-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="7c017-126">Como: ler de arquivos de texto de largura fixa</span><span class="sxs-lookup"><span data-stu-id="7c017-126">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="7c017-127">Como: ler de arquivos de texto com vários formatos</span><span class="sxs-lookup"><span data-stu-id="7c017-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="7c017-128">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="7c017-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="7c017-129">Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c017-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="7c017-130">Solução de problemas: ler e gravar em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="7c017-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
