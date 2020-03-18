---
title: Cref attribute - C# guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: b06d0c9d447124dec7d8cf3c0cbbfd0daca78fe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157007"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="c7ba4-102">cref atributo (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c7ba4-102">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="c7ba4-103">O atributo `cref` em uma marca de documentação XML significa “referência de código”.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="c7ba4-104">Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="c7ba4-105">Ferramentas de documentação, como o [DocFX](https://dotnet.github.io/docfx/) e o [Sandcastle](https://github.com/EWSoftware/SHFB), usam os atributos `cref` para gerar automaticamente os hiperlinks para a página em que o tipo ou o membro está documentado.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="c7ba4-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7ba4-106">Example</span></span>

<span data-ttu-id="c7ba4-107">O exemplo `cref` a seguir mostra atributos usados em [ \<ver>](./see.md) tags.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-107">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="c7ba4-108">Quando compilado, o programa produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="c7ba4-109">Observe que o atributo `cref` do método `GetZero`, por exemplo, foi transformado em `"M:TestNamespace.TestClass.GetZero"` pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="c7ba4-110">O prefixo "M:" significa "método" e é uma convenção reconhecida por ferramentas de documentação como o DocFX e o Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="c7ba4-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="c7ba4-111">Para obter uma lista completa de prefixos, consulte [Processando o Arquivo XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba4-111">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example>
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass
            {
                static int Main()
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks>
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="c7ba4-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="c7ba4-112">See also</span></span>

- [<span data-ttu-id="c7ba4-113">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="c7ba4-113">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="c7ba4-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="c7ba4-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
