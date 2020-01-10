---
title: Como usar os recursos de documentação XML- C# guia de programação
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 5de94b1f1ab44f954b5bab9f8b5212c33325c19d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696708"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="1c72d-102">Como usar as funcionalidades da documentação XML</span><span class="sxs-lookup"><span data-stu-id="1c72d-102">How to use the XML documentation features</span></span>

<span data-ttu-id="1c72d-103">O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.</span><span class="sxs-lookup"><span data-stu-id="1c72d-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="1c72d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c72d-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="1c72d-105">O exemplo gera um arquivo .xml com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="1c72d-105">The example generates an .xml file with the following contents:</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member 
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a><span data-ttu-id="1c72d-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1c72d-106">Compiling the code</span></span>

<span data-ttu-id="1c72d-107">Para compilar o exemplo, digite a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="1c72d-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="1c72d-108">Esse comando cria o arquivo XML *XMLsample.xml*, que você pode exibir no navegador ou usando o comando TYPE.</span><span class="sxs-lookup"><span data-stu-id="1c72d-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="1c72d-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1c72d-109">Robust programming</span></span>

<span data-ttu-id="1c72d-110">A documentação XML começa com ///.</span><span class="sxs-lookup"><span data-stu-id="1c72d-110">XML documentation starts with ///.</span></span> <span data-ttu-id="1c72d-111">Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você.</span><span class="sxs-lookup"><span data-stu-id="1c72d-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="1c72d-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="1c72d-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="1c72d-113">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="1c72d-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="1c72d-114">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="1c72d-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="1c72d-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="1c72d-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="1c72d-116">Há um conjunto de marcas recomendadas (confira [Marcas recomendadas para comentários da documentação](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="1c72d-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="1c72d-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="1c72d-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="1c72d-118">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c72d-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="1c72d-119">Se ela é usada, o compilador verifica se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="1c72d-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="1c72d-120">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="1c72d-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="1c72d-121">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="1c72d-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="1c72d-122">O compilador verifica se esse elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="1c72d-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="1c72d-123">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="1c72d-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="1c72d-124">O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="1c72d-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="1c72d-125">A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="1c72d-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1c72d-126">O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo).</span><span class="sxs-lookup"><span data-stu-id="1c72d-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="1c72d-127">Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.</span><span class="sxs-lookup"><span data-stu-id="1c72d-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c72d-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="1c72d-128">See also</span></span>

- [<span data-ttu-id="1c72d-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1c72d-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1c72d-130">-doc (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="1c72d-130">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="1c72d-131">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="1c72d-131">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="1c72d-132">Processador de documentação do DocFX</span><span class="sxs-lookup"><span data-stu-id="1c72d-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="1c72d-133">Processador de documentação do Sandcastle</span><span class="sxs-lookup"><span data-stu-id="1c72d-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
