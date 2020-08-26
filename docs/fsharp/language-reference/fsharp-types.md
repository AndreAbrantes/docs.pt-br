---
title: Tipos
description: 'Saiba mais sobre os tipos que são usados em F # e como os tipos F # são nomeados e descritos.'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812062"
---
# <a name="f-types"></a>Tipos F#

Este tópico descreve os tipos que são usados em F # e como os tipos F # são nomeados e descritos.

## <a name="summary-of-f-types"></a>Resumo dos tipos F #

Alguns tipos são considerados *tipos primitivos*, como o tipo booliano `bool` e os tipos de ponto flutuante e integral de vários tamanhos, que incluem tipos de bytes e caracteres. Esses tipos são descritos em [tipos primitivos](basic-types.md).

Outros tipos que são criados no idioma incluem tuplas, listas, matrizes, sequências, registros e uniões discriminadas. Se você tiver experiência com outras linguagens .NET e estiver aprendendo F #, leia os tópicos para cada um desses tipos. Esses tipos específicos de F # dão suporte a estilos de programação comuns a linguagens de programação funcionais. Muitos desses tipos têm módulos associados na biblioteca F # que oferecem suporte a operações comuns nesses tipos.

O tipo de uma função inclui informações sobre os tipos de parâmetro e tipo de retorno.

A .NET Framework é a fonte de tipos de objeto, tipos de interface, tipos de delegado e outros. Você pode definir seus próprios tipos de objeto assim como você pode em qualquer outra linguagem .NET.

Além disso, o código F # pode definir aliases, que são *abreviações de tipo*nomeado, que são nomes alternativos para tipos. Você pode usar abreviações de tipo quando o tipo pode mudar no futuro e você deseja evitar alterar o código que depende do tipo. Ou, você pode usar uma abreviação de tipo como um nome amigável para um tipo que pode tornar o código mais fácil de ler e entender.

O F # fornece tipos de coleção úteis que são projetados com a programação funcional em mente. O uso desses tipos de coleção ajuda a escrever código mais funcional em estilo. Para obter mais informações, consulte [tipos de coleção de F #](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Sintaxe para tipos

No código F #, geralmente você precisa escrever os nomes dos tipos. Cada tipo tem um formato sintático e você usa esses formulários sintáticos em anotações de tipo, declarações de métodos abstratos, declarações de delegado, assinaturas e outras construções. Sempre que você declara uma construção de novo programa no intérprete, o intérprete imprime o nome da construção e a sintaxe para seu tipo. Essa sintaxe pode ser apenas um identificador para um tipo definido pelo usuário ou um identificador interno, como para `int` ou `string` , mas para tipos mais complexos, a sintaxe é mais complexa.

A tabela a seguir mostra aspectos da sintaxe de tipo para tipos F #.

|Tipo|Sintaxe de tipo|Exemplos|
|----|-----------|--------|
|tipo primitivo|*nome do tipo*|`int`<br /><br />`float`<br /><br />`string`|
|tipo de agregação (classe, estrutura, União, registro, enumeração e assim por diante)|*nome do tipo*|`System.DateTime`<br /><br />`Color`|
|abreviação de tipo|*tipo-abreviação-nome*|`bigint`|
|tipo totalmente qualificado|*namespaces. tipo-nome*<br /><br />ou<br /><br />*modules. Type-Name*<br /><br />ou<br /><br />*namespaces. modules. Type-Name*|`System.IO.StreamWriter`|
|matriz|*Type-Name*[] ou<br /><br />matriz *de nome de tipo*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|matriz bidimensional|*tipo-nome*[,]|`int[,]`<br /><br />`float[,]`|
|matriz tridimensional|*tipo-nome*[,,]|`float[,,]`|
|tuple|*Type-nome1* &#42; *Type-nome2* ...|Por exemplo, `(1,'b',3)` tem tipo `int * char * int`|
|tipo genérico|*tipo-* *tipo genérico-nome-* do-parâmetro<br /><br />ou<br /><br />nome de tipo *genérico* &lt; *lista de parâmetros de tipo*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|tipo construído (um tipo genérico que tem um argumento de tipo específico fornecido)|tipo *-* *tipo genérico-nome* -do-argumento<br /><br />ou<br /><br />nome de tipo *genérico* &lt; *lista de argumentos de tipo*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tipo de função que tem um único parâmetro|*parâmetro-type1*  - &gt; *tipo de retorno*|Uma função que usa um `int` e retorna um `string` tipo tem `int -> string`|
|tipo de função que tem vários parâmetros|*parâmetro-type1*  - &gt; *parâmetro-type2*  - &gt; ...- &gt; *tipo de retorno*|Uma função que usa um `int` e um `float` e retorna um `string` tipo `int -> float -> string`|
|função de ordem superior como um parâmetro|(*tipo de função*)|`List.map` tem tipo `('a -> 'b) -> 'a list -> 'b list`|
|delegado|delegado do *tipo de função*|`delegate of unit -> int`|
|tipo flexível|#*nome do tipo*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tópicos relacionados

|Tópico|Descrição|
|-----|-----------|
|[Tipos primitivos](basic-types.md)|Descreve os tipos simples internos, como tipos integrais, o tipo booliano e os tipos de caracteres.|
|[Tipo unit](unit-type.md)|Descreve o `unit` tipo, um tipo que tem um valor e que é indicado por (); equivalente a `void` em C# e `Nothing` em Visual Basic.|
|[Tuplas](tuples.md)|Descreve o tipo de tupla, um tipo que consiste em valores associados de qualquer tipo agrupado em pares, corridas, quádruplos e assim por diante.|
|[Opções](options.md)|Descreve o tipo de opção, um tipo que pode ter um valor ou estar vazio.|
|[Listas](lists.md)|Descreve as listas, que são ordenadas, em uma série imutável de elementos, todos do mesmo tipo.|
|[matrizes](arrays.md)|Descreve matrizes, que são conjuntos ordenados de elementos mutáveis do mesmo tipo que ocupam um bloco contíguo de memória e têm tamanho fixo.|
|[Sequências](sequences.md)|Descreve o tipo de sequência, que representa uma série lógica de valores; valores individuais são computados somente conforme necessário.|
|[Registros](records.md)|Descreve o tipo de registro, uma pequena agregação de valores nomeados.|
|[Uniões discriminadas](discriminated-unions.md)|Descreve o tipo de união discriminada, um tipo cujos valores podem ser qualquer um de um conjunto de tipos possíveis.|
|[Funções](./functions/index.md)|Descreve os valores de função.|
|[Classes](classes.md)|Descreve o tipo de classe, um tipo de objeto que corresponde a um tipo de referência do .NET. Os tipos de classe podem conter membros, propriedades, interfaces implementadas e um tipo base.|
|[Estruturas](structures.md)|Descreve o `struct` tipo, um tipo de objeto que corresponde a um tipo de valor .net. O `struct` tipo geralmente representa uma pequena agregação de dados.|
|[Interfaces](interfaces.md)|Descreve os tipos de interface, que são tipos que representam um conjunto de membros que fornecem determinadas funcionalidades, mas que não contêm dados. Um tipo de interface deve ser implementado por um tipo de objeto para ser útil.|
|[Representantes](delegates.md)|Descreve o tipo delegado, que representa uma função como um objeto.|
|[Enumerações](enumerations.md)|Descreve os tipos de enumeração cujos valores pertencem a um conjunto de valores nomeados.|
|[Atributos](attributes.md)|Descreve atributos, que são usados para especificar metadados para outro tipo.|
|[Tipos de exceção](./exception-handling/exception-types.md)|Descreve as exceções, que especificam informações de erro.|
