---
title: Criação de novas cadeias de caracteres no .NET
description: Aprenda a criar cadeias de caracteres usando atribuição, construtores de classe ou métodos System. String que combinam várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: b44d0f8e1717ead72e28f0be644644961d1482b6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596442"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="afdac-103">Criação de novas cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="afdac-103">Creating New Strings in .NET</span></span>
<span data-ttu-id="afdac-104">O .NET Framework permite que cadeias de caracteres sejam criadas usando uma atribuição simples e também sobrecarrega um construtor de classe para dar suporte à criação de cadeias de caracteres usando um número de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="afdac-104">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="afdac-105">O .NET Framework também fornece vários métodos na classe <xref:System.String?displayProperty=nameWithType> que criam objetos de cadeia de caracteres combinando várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos.</span><span class="sxs-lookup"><span data-stu-id="afdac-105">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="afdac-106">Criando cadeias de caracteres usando atribuição</span><span class="sxs-lookup"><span data-stu-id="afdac-106">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="afdac-107">A maneira mais fácil para criar um novo objeto <xref:System.String> é simplesmente atribuir uma cadeia de caracteres literal a um objeto <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="afdac-107">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="afdac-108">Criando cadeias de caracteres usando um construtor de classe</span><span class="sxs-lookup"><span data-stu-id="afdac-108">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="afdac-109">Você pode usar sobrecargas do constructo de classe <xref:System.String> para criar cadeias de caracteres de matrizes de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-109">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="afdac-110">Você também pode criar uma nova cadeia de caracteres duplicando um caractere específico, m número de vezes especificado.</span><span class="sxs-lookup"><span data-stu-id="afdac-110">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="afdac-111">Métodos que retornam cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="afdac-111">Methods that Return Strings</span></span>  
 <span data-ttu-id="afdac-112">A tabela a seguir lista vários métodos úteis que retornam novos objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-112">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="afdac-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="afdac-113">Method name</span></span>|<span data-ttu-id="afdac-114">Uso</span><span class="sxs-lookup"><span data-stu-id="afdac-114">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="afdac-115">Cria uma cadeia de caracteres formatada de um conjunto de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="afdac-115">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="afdac-116">Cria cadeias de caracteres de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-116">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="afdac-117">Cria uma nova cadeia de caracteres combinando uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-117">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="afdac-118">Cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres no índice especificado de uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="afdac-118">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="afdac-119">Copia caracteres especificados de uma cadeia de caracteres para uma posição especificada em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-119">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="afdac-120">Formatar</span><span class="sxs-lookup"><span data-stu-id="afdac-120">Format</span></span>  
 <span data-ttu-id="afdac-121">Você pode usar o método **String.Format** para criar cadeias de caracteres formatadas e concatenar cadeias de caracteres que representam vários objetos.</span><span class="sxs-lookup"><span data-stu-id="afdac-121">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="afdac-122">Este método converte automaticamente qualquer objeto passado em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-122">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="afdac-123">Por exemplo, se seu aplicativo precisar exibir um valor **Int32** e um valor **DateTime** para o usuário, você pode facilmente criar uma cadeia de caracteres para representar esses valores usando o método **Format**.</span><span class="sxs-lookup"><span data-stu-id="afdac-123">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="afdac-124">Para obter informações sobre as convenções de formatação usadas com esse método, consulte a seção sobre [formatação de composição](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="afdac-124">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="afdac-125">O exemplo a seguir usa o método **Format** para criar uma cadeia de caracteres que usa uma variável de inteiro.</span><span class="sxs-lookup"><span data-stu-id="afdac-125">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="afdac-126">Neste exemplo, <xref:System.DateTime.Now%2A?displayProperty=nameWithType> exibe a data e hora atuais da maneira especificada pela cultura associada ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="afdac-126">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="afdac-127">Concat</span><span class="sxs-lookup"><span data-stu-id="afdac-127">Concat</span></span>  
 <span data-ttu-id="afdac-128">O método **String.Concat** pode ser usado para criar facilmente um novo objeto de cadeia de caracteres de dois ou mais objetos existentes.</span><span class="sxs-lookup"><span data-stu-id="afdac-128">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="afdac-129">Ele fornece uma maneira independente da linguagem para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-129">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="afdac-130">Este método aceita qualquer classe derivada de **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="afdac-130">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="afdac-131">O exemplo a seguir cria uma cadeia de caracteres de dois objetos de cadeia de caracteres existentes e um caractere de separação.</span><span class="sxs-lookup"><span data-stu-id="afdac-131">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="afdac-132">Join</span><span class="sxs-lookup"><span data-stu-id="afdac-132">Join</span></span>  
 <span data-ttu-id="afdac-133">O método **String.Join** cria uma nova cadeia de caracteres a partir de uma matriz de cadeias de caracteres e uma cadeia de caracteres de separador.</span><span class="sxs-lookup"><span data-stu-id="afdac-133">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="afdac-134">Esse método é útil se você quiser concatenar várias cadeias de caracteres fazendo uma lista, talvez separada por vírgula.</span><span class="sxs-lookup"><span data-stu-id="afdac-134">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="afdac-135">O exemplo a seguir usa um espaço para associar uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-135">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="afdac-136">Inserir</span><span class="sxs-lookup"><span data-stu-id="afdac-136">Insert</span></span>  
 <span data-ttu-id="afdac-137">O método **String.Insert** cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres em uma posição especificada em outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-137">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="afdac-138">Este método usa um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="afdac-138">This method uses a zero-based index.</span></span> <span data-ttu-id="afdac-139">O exemplo a seguir insere uma cadeia de caracteres na quinta posição do índice de `MyString` e cria uma nova cadeia de caracteres com esse valor.</span><span class="sxs-lookup"><span data-stu-id="afdac-139">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="afdac-140">CopyTo</span><span class="sxs-lookup"><span data-stu-id="afdac-140">CopyTo</span></span>  
 <span data-ttu-id="afdac-141">O método **String.CopyTo** copia partes de uma cadeia de caracteres em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-141">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="afdac-142">Você pode especificar o índice inicial da cadeia de caracteres e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="afdac-142">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="afdac-143">Este método usa o índice de origem, uma matriz de caracteres, o índice de destino e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="afdac-143">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="afdac-144">Todos os índices são baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="afdac-144">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="afdac-145">O exemplo a seguir usa o método **CopyTo** para copiar os caracteres da palavra "Hello" de um objeto de cadeia de caracteres para a primeira posição de índice de uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="afdac-145">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="afdac-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afdac-146">See also</span></span>

- [<span data-ttu-id="afdac-147">Operações básicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="afdac-147">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="afdac-148">Formatação composta</span><span class="sxs-lookup"><span data-stu-id="afdac-148">Composite Formatting</span></span>](composite-formatting.md)
