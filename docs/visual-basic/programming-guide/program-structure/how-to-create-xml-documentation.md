---
title: Como criar documentação XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403233"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="fb124-102">Como criar documentação XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb124-102">How to: Create XML Documentation in Visual Basic</span></span>

<span data-ttu-id="fb124-103">Este exemplo mostra como adicionar comentários de documentação XML ao seu código.</span><span class="sxs-lookup"><span data-stu-id="fb124-103">This example shows how to add XML documentation comments to your code.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="fb124-104">Para criar a documentação XML para um tipo ou membro</span><span class="sxs-lookup"><span data-stu-id="fb124-104">To create XML documentation for a type or member</span></span>

1. <span data-ttu-id="fb124-105">No **Editor de código**, posicione o cursor na linha acima do tipo ou do membro para o qual você deseja criar a documentação.</span><span class="sxs-lookup"><span data-stu-id="fb124-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>

2. <span data-ttu-id="fb124-106">Tipo `'''` (três aspas simples).</span><span class="sxs-lookup"><span data-stu-id="fb124-106">Type `'''` (three single-quotation marks).</span></span>

    <span data-ttu-id="fb124-107">Um esqueleto XML para o tipo ou membro é adicionado no **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="fb124-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>

3. <span data-ttu-id="fb124-108">Adicione informações descritivas entre as marcas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="fb124-108">Add descriptive information between the appropriate tags.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fb124-109">Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deverá começar com `'''` .</span><span class="sxs-lookup"><span data-stu-id="fb124-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>

4. <span data-ttu-id="fb124-110">Adicione um código adicional que use o tipo ou o membro com os novos comentários de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="fb124-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>

    <span data-ttu-id="fb124-111">O IntelliSense exibe o texto da \<summary> marca para o tipo ou o membro.</span><span class="sxs-lookup"><span data-stu-id="fb124-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>

5. <span data-ttu-id="fb124-112">Compile o código para gerar um arquivo XML contendo os comentários da documentação.</span><span class="sxs-lookup"><span data-stu-id="fb124-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="fb124-113">Para obter mais informações, consulte [-Doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="fb124-113">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb124-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb124-114">See also</span></span>

- [<span data-ttu-id="fb124-115">Documentando o código com XML</span><span class="sxs-lookup"><span data-stu-id="fb124-115">Documenting Your Code with XML</span></span>](documenting-your-code-with-xml.md)
- [<span data-ttu-id="fb124-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="fb124-116">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="fb124-117">-doc</span><span class="sxs-lookup"><span data-stu-id="fb124-117">-doc</span></span>](../../reference/command-line-compiler/doc.md)
