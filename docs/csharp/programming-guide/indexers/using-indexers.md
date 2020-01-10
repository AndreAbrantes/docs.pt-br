---
title: Como usar indexadores – Guia de Programação em C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: bf290681395460bec10be45c4eaa1f165e453caf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702890"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="4a0af-102">Usando indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4a0af-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="4a0af-103">Os indexadores são uma conveniência sintática que permitem criar uma [classe](../../language-reference/keywords/class.md), [struct](../../language-reference/keywords/struct.md) ou [interface](../../language-reference/keywords/interface.md) que os aplicativos clientes podem acessar como uma matriz.</span><span class="sxs-lookup"><span data-stu-id="4a0af-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/keywords/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="4a0af-104">Os indexadores são implementados em tipos cuja principal finalidade é encapsular uma coleção ou matriz interna.</span><span class="sxs-lookup"><span data-stu-id="4a0af-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="4a0af-105">Por exemplo, suponha que você tenha uma classe `TempRecord` que representa a temperatura em Fahrenheit, conforme registrada em 10 momentos diferentes durante um período de 24 horas.</span><span class="sxs-lookup"><span data-stu-id="4a0af-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="4a0af-106">A classe contém uma matriz `temps` do tipo `float[]` para armazenar os valores de temperatura.</span><span class="sxs-lookup"><span data-stu-id="4a0af-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="4a0af-107">Ao implementar um indexador nessa classe, os clientes podem acessar as temperaturas em uma instância `TempRecord` como `float temp = tr[4]`, e não como `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="4a0af-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="4a0af-108">A notação do indexador não simplifica somente a sintaxe para aplicativos clientes; ela também torna a classe e sua finalidade mais intuitivas para que os outros desenvolvedores entendam.</span><span class="sxs-lookup"><span data-stu-id="4a0af-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="4a0af-109">Para declarar um indexador em uma classe ou struct, use a palavra-chave [this](../../language-reference/keywords/this.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="4a0af-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="4a0af-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a0af-110">Remarks</span></span>

<span data-ttu-id="4a0af-111">O tipo de um indexador e o tipo dos seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="4a0af-112">Para obter mais informações sobre níveis de acessibilidade, consulte [Modificadores de acesso](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4a0af-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4a0af-113">Para obter mais informações sobre como usar indexadores com uma interface, consulte [Indexadores de Interface](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4a0af-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="4a0af-114">A assinatura de um indexador consiste do número e dos tipos de seus parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="4a0af-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="4a0af-115">Ela não inclui o tipo de indexador nem os nomes dos parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="4a0af-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="4a0af-116">Se você declarar mais de um indexador na mesma classe, eles terão diferentes assinaturas.</span><span class="sxs-lookup"><span data-stu-id="4a0af-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="4a0af-117">Um valor de indexador não é classificado como uma variável; portanto, não é possível passar um valor de indexador como um parâmetro [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="4a0af-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="4a0af-118">Para fornecer o indexador com um nome que outras linguagens possam usar, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="4a0af-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="4a0af-119">Este indexador terá o nome `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="4a0af-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="4a0af-120">Não fornecer o atributo de nome tornaria `Item` o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="4a0af-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="4a0af-121">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="4a0af-121">Example 1</span></span>  
  
<span data-ttu-id="4a0af-122">O exemplo a seguir mostra como declarar um campo de matriz privada, `temps` e um indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="4a0af-123">O indexador permite acesso direto à instância `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="4a0af-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="4a0af-124">A alternativa ao uso do indexador é declarar a matriz como um membro [público](../../language-reference/keywords/public.md) e acessar seus membros, `tempRecord.temps[i]`, diretamente.</span><span class="sxs-lookup"><span data-stu-id="4a0af-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="4a0af-125">Observe que, quando o acesso de um indexador é avaliado, por exemplo, em uma instrução `Console.Write`, o acessador [get](../../language-reference/keywords/get.md) é invocado.</span><span class="sxs-lookup"><span data-stu-id="4a0af-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="4a0af-126">Portanto, se não existir nenhum acessador `get`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="4a0af-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="4a0af-127">Indexando usando outros valores</span><span class="sxs-lookup"><span data-stu-id="4a0af-127">Indexing using other values</span></span>

<span data-ttu-id="4a0af-128">O C# não limita o tipo de parâmetro do indexador ao inteiro.</span><span class="sxs-lookup"><span data-stu-id="4a0af-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="4a0af-129">Por exemplo, talvez seja útil usar uma cadeia de caracteres com um indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="4a0af-130">Esse indexador pode ser implementado pesquisando a cadeia de caracteres na coleção e retornando o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="4a0af-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="4a0af-131">Como os acessadores podem ser sobrecarregados, as versões do inteiro e da cadeia de caracteres podem coexistir.</span><span class="sxs-lookup"><span data-stu-id="4a0af-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="4a0af-132">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="4a0af-132">Example 2</span></span>  
  
<span data-ttu-id="4a0af-133">O exemplo a seguir declara uma classe que armazena os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="4a0af-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="4a0af-134">Um acessador `get` aceita uma cadeia de caracteres, o nome de um dia e retorna o inteiro correspondente.</span><span class="sxs-lookup"><span data-stu-id="4a0af-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="4a0af-135">Por exemplo, "Sunday" retorna 0, "Monday" retorna 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4a0af-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4a0af-136">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="4a0af-136">Robust programming</span></span>

 <span data-ttu-id="4a0af-137">Há duas maneiras principais nas quais a segurança e a confiabilidade de indexadores podem ser melhoradas:</span><span class="sxs-lookup"><span data-stu-id="4a0af-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="4a0af-138">Certifique-se de incorporar algum tipo de estratégia de tratamento de erros para manipular a chance de passagem de código cliente em um valor de índice inválido.</span><span class="sxs-lookup"><span data-stu-id="4a0af-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="4a0af-139">Anteriormente, no primeiro exemplo neste tópico, a classe TempRecord oferece uma propriedade Length que permite que o código cliente verifique a saída antes de passá-la para o indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="4a0af-140">Também é possível colocador o código de tratamento de erro dentro do próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="4a0af-141">Certifique-se documentar para os usuários as exceções que você gera dentro de um acessador do indexador.</span><span class="sxs-lookup"><span data-stu-id="4a0af-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="4a0af-142">Defina a acessibilidade dos acessadores [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) para que ela seja mais restritiva possível.</span><span class="sxs-lookup"><span data-stu-id="4a0af-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="4a0af-143">Isso é importante para o acessador `set` em particular.</span><span class="sxs-lookup"><span data-stu-id="4a0af-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="4a0af-144">Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="4a0af-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0af-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a0af-145">See also</span></span>

- [<span data-ttu-id="4a0af-146">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4a0af-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a0af-147">Indexadores</span><span class="sxs-lookup"><span data-stu-id="4a0af-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="4a0af-148">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4a0af-148">Properties</span></span>](../classes-and-structs/properties.md)
