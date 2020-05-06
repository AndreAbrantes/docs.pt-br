---
title: Módulos
description: 'Saiba como um módulo F # é um agrupamento de código F #, como valores, tipos e valores de função, em um programa F #.'
ms.date: 04/24/2017
ms.openlocfilehash: 5f99bbd8069478bf0c7db2800ae545f31926728a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794358"
---
# <a name="modules"></a><span data-ttu-id="fcde6-103">Módulos</span><span class="sxs-lookup"><span data-stu-id="fcde6-103">Modules</span></span>

<span data-ttu-id="fcde6-104">No contexto da linguagem F #, um *módulo* é um agrupamento de código f #, como valores, tipos e valores de função, em um programa f #.</span><span class="sxs-lookup"><span data-stu-id="fcde6-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="fcde6-105">O agrupamento de código em módulos ajuda a manter junto o código relacionado e ajuda a evitar conflitos de nome em seu programa.</span><span class="sxs-lookup"><span data-stu-id="fcde6-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcde6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcde6-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="fcde6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcde6-107">Remarks</span></span>

<span data-ttu-id="fcde6-108">Um módulo F # é um agrupamento de construções de código F #, como tipos, valores, valores de função e código em `do` associações.</span><span class="sxs-lookup"><span data-stu-id="fcde6-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="fcde6-109">Ele é implementado como uma classe Common Language Runtime (CLR) que tem apenas membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="fcde6-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="fcde6-110">Há dois tipos de declarações de módulo, dependendo se o arquivo inteiro está incluído no módulo: uma declaração de módulo de nível superior e uma declaração de módulo local.</span><span class="sxs-lookup"><span data-stu-id="fcde6-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="fcde6-111">Uma declaração de módulo de nível superior inclui o arquivo inteiro no módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="fcde6-112">Uma declaração de módulo de nível superior pode aparecer somente como a primeira declaração em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="fcde6-113">Na sintaxe para a declaração de módulo de nível superior, o *namespace qualificado* opcional é a sequência de nomes de namespace aninhados que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="fcde6-114">O namespace qualificado não precisa ser declarado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fcde6-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="fcde6-115">Você não precisa recuar declarações em um módulo de nível superior.</span><span class="sxs-lookup"><span data-stu-id="fcde6-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="fcde6-116">Você precisa recuar todas as declarações em módulos locais.</span><span class="sxs-lookup"><span data-stu-id="fcde6-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="fcde6-117">Em uma declaração de módulo local, somente as declarações que são recuadas sob essa declaração de módulo fazem parte do módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="fcde6-118">Se um arquivo de código não começar com uma declaração de módulo de nível superior ou uma declaração de namespace, todo o conteúdo do arquivo, incluindo quaisquer módulos locais, se tornará parte de um módulo de nível superior criado implicitamente que tem o mesmo nome que o arquivo, sem a extensão, com a primeira letra convertida em maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="fcde6-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="fcde6-119">Por exemplo, considere o arquivo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcde6-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="fcde6-120">Esse arquivo seria compilado como se tivesse sido escrito desta maneira:</span><span class="sxs-lookup"><span data-stu-id="fcde6-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="fcde6-121">Se você tiver vários módulos em um arquivo, deverá usar uma declaração de módulo local para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="fcde6-122">Se um namespace delimitador for declarado, esses módulos serão parte do namespace delimitador.</span><span class="sxs-lookup"><span data-stu-id="fcde6-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="fcde6-123">Se um namespace delimitador não for declarado, os módulos se tornarão parte do módulo de nível superior criado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="fcde6-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="fcde6-124">O exemplo de código a seguir mostra um arquivo de código que contém vários módulos.</span><span class="sxs-lookup"><span data-stu-id="fcde6-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="fcde6-125">O compilador cria implicitamente um módulo de nível superior denominado `Multiplemodules`e `MyModule1` e `MyModule2` é aninhado nesse módulo de nível superior.</span><span class="sxs-lookup"><span data-stu-id="fcde6-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="fcde6-126">Se você tiver vários arquivos em um projeto do ou em uma única compilação, ou se estiver criando uma biblioteca, deverá incluir uma declaração de namespace ou declaração de módulo na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="fcde6-127">O compilador F # determina apenas um nome de módulo implicitamente quando há apenas um arquivo em um projeto ou linha de comando de compilação, e você está criando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="fcde6-128">O *modificador de acessibilidade* pode ser um dos seguintes: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="fcde6-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="fcde6-129">Para mais informações, consulte [Controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="fcde6-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="fcde6-130">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="fcde6-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="fcde6-131">Referenciando código em módulos</span><span class="sxs-lookup"><span data-stu-id="fcde6-131">Referencing Code in Modules</span></span>

<span data-ttu-id="fcde6-132">Ao fazer referência a funções, tipos e valores de outro módulo, você deve usar um nome qualificado ou abrir o módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="fcde6-133">Se você usar um nome qualificado, deverá especificar os namespaces, o módulo e o identificador para o elemento de programa desejado.</span><span class="sxs-lookup"><span data-stu-id="fcde6-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="fcde6-134">Você separa cada parte do caminho qualificado com um ponto (.), da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="fcde6-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="fcde6-135">Você pode abrir o módulo ou um ou mais dos namespaces para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="fcde6-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="fcde6-136">Para obter mais informações sobre como abrir módulos e namespaces, consulte [importar declarações `open` : a palavra-chave](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="fcde6-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="fcde6-137">O exemplo de código a seguir mostra um módulo de nível superior que contém todo o código até o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="fcde6-138">Para usar esse código de outro arquivo no mesmo projeto, você pode usar nomes qualificados ou abrir o módulo antes de usar as funções, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcde6-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="fcde6-139">Módulos aninhados</span><span class="sxs-lookup"><span data-stu-id="fcde6-139">Nested Modules</span></span>

<span data-ttu-id="fcde6-140">Os módulos podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="fcde6-140">Modules can be nested.</span></span> <span data-ttu-id="fcde6-141">Os módulos internos devem ser recuados até o momento como declarações de módulo externas para indicar que são módulos internos, não novos módulos.</span><span class="sxs-lookup"><span data-stu-id="fcde6-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="fcde6-142">Por exemplo, compare os dois exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcde6-142">For example, compare the following two examples.</span></span> <span data-ttu-id="fcde6-143">`Z` É um módulo interno no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcde6-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="fcde6-144">Mas o `Z` módulo é um irmão para `Y` o módulo no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="fcde6-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="fcde6-145">O `Z` módulo também é um módulo irmão no código a seguir, porque ele não é recuado até outras declarações no módulo `Y`.</span><span class="sxs-lookup"><span data-stu-id="fcde6-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="fcde6-146">Por fim, se o módulo externo não tiver declarações e for seguido imediatamente por outra declaração de módulo, a nova declaração de módulo será considerada um módulo interno, mas o compilador avisará se a segunda definição de módulo não for recuada além da primeira.</span><span class="sxs-lookup"><span data-stu-id="fcde6-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="fcde6-147">Para eliminar o aviso, recue o módulo interno.</span><span class="sxs-lookup"><span data-stu-id="fcde6-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="fcde6-148">Se você quiser que todo o código em um arquivo esteja em um único módulo externo e queira módulos internos, o módulo externo não exigirá o sinal de igual, e as declarações, incluindo quaisquer declarações de módulo internas, que vão no módulo externo, não precisarão ser recuadas.</span><span class="sxs-lookup"><span data-stu-id="fcde6-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="fcde6-149">As declarações dentro das declarações de módulo internas precisam ser recuadas.</span><span class="sxs-lookup"><span data-stu-id="fcde6-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="fcde6-150">O código a seguir mostra esse caso.</span><span class="sxs-lookup"><span data-stu-id="fcde6-150">The following code shows this case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="fcde6-151">Módulos recursivos</span><span class="sxs-lookup"><span data-stu-id="fcde6-151">Recursive modules</span></span>

<span data-ttu-id="fcde6-152">F # 4,1 apresenta a noção de módulos que permitem que todo o código independente seja recursivo mutuamente.</span><span class="sxs-lookup"><span data-stu-id="fcde6-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="fcde6-153">Isso é feito por `module rec`meio de.</span><span class="sxs-lookup"><span data-stu-id="fcde6-153">This is done via `module rec`.</span></span>  <span data-ttu-id="fcde6-154">O uso `module rec` de pode aliviar alguns problemas em não ser capaz de escrever código referencial mutuamente entre tipos e módulos.</span><span class="sxs-lookup"><span data-stu-id="fcde6-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="fcde6-155">Veja a seguir um exemplo disso:</span><span class="sxs-lookup"><span data-stu-id="fcde6-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
    type Orientation = Up | Down
    type PeelState = Peeled | Unpeeled

    // This exception depends on the type below.
    exception DontSqueezeTheBananaException of Banana

    type Banana(orientation : Orientation) =
        member val IsPeeled = false with get, set
        member val Orientation = orientation with get, set
        member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

        member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
        member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

    module BananaHelpers =
        let peel (b: Banana) =
            let flip (banana: Banana) =
                match banana.Orientation with
                | Up ->
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides (banana: Banana) =
                banana.Sides
                |> List.map (function
                             | Unpeeled -> Peeled
                             | Peeled -> Peeled)

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

<span data-ttu-id="fcde6-156">Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência umas às outras.</span><span class="sxs-lookup"><span data-stu-id="fcde6-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="fcde6-157">Além disso, o `BananaHelpers` módulo e a `Banana` classe também se referem uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="fcde6-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="fcde6-158">Isso não seria possível expressar em F # se você removesse a `rec` palavra-chave do `RecursiveModule` módulo.</span><span class="sxs-lookup"><span data-stu-id="fcde6-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="fcde6-159">Esse recurso também é possível em [namespaces](namespaces.md) com F # 4,1.</span><span class="sxs-lookup"><span data-stu-id="fcde6-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcde6-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcde6-160">See also</span></span>

- [<span data-ttu-id="fcde6-161">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="fcde6-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="fcde6-162">Namespaces</span><span class="sxs-lookup"><span data-stu-id="fcde6-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="fcde6-163">F # RFC FS-1009-permitir tipos referenciais mutuamente e módulos em escopos maiores nos arquivos</span><span class="sxs-lookup"><span data-stu-id="fcde6-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
