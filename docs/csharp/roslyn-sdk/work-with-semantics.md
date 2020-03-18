---
title: Trabalhar com o modelo semântico do SDK do .NET Compiler Platform
description: Esta visão geral fornece uma compreensão do tipo que pode ser usado para entender e manipular o modelo semântico do código.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 8575988cd98a4c0ba3f24107788f065f7472f55d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156929"
---
# <a name="work-with-semantics"></a>Trabalhar com semântica

As [árvores de sintaxe](work-with-syntax.md) representam a estrutura lexical e sintática do código-fonte. Embora essas informações apenas sejam suficientes para descrever todas as declarações e a lógica na fonte, não são informações suficientes para identificar o que está sendo referenciado. Um nome pode representar:

- um tipo
- um campo
- um método
- uma variável local

Embora cada um deles seja exclusivamente diferente, determinar a qual deles um identificador, de fato, se refere exige uma compreensão profunda das regras da linguagem.

Há elementos do programa representados no código-fonte e os programas também podem se referir a bibliotecas compiladas anteriormente, empacotadas em arquivos do assembly. Embora nenhum código-fonte e, portanto, nenhum nó ou árvore de sintaxe, esteja disponível para assemblies, os programas ainda podem se referir a elementos contidos neles.

Para essas tarefas, é necessário usar o **Modelo semântico**.

Além de um modelo sintático do código-fonte, um modelo semântico encapsula as regras da linguagem, fornecendo uma maneira fácil para fazer a correspondência correta de identificadores com o elemento de programa correto que está sendo referenciado.

## <a name="compilation"></a>Compilação

Uma compilação é uma representação de tudo o que é necessário para compilar um programa do C# ou Visual Basic, que inclui todas as referências de assembly, opções do compilador e arquivos de origem.

Como todas essas informações estão em um só lugar, os elementos contidos no código-fonte podem ser descritos mais detalhadamente. A compilação representa cada tipo, membro ou variável declarada como um símbolo. A compilação contém uma variedade de métodos que ajudam você encontrar e identificar os símbolos que foram declarados no código-fonte ou importados como metadados de um assembly.

Semelhantes às árvores de sintaxe, as compilações são imutáveis. Depois de criar uma compilação, ela não pode ser alterada por você ou por outra pessoa com quem você pode está compartilhando. No entanto, é possível criar uma nova compilação com base em uma compilação existente, especificando uma alteração conforme ela é feita. Por exemplo, é possível criar uma compilação que é igual em todos os aspectos a uma compilação existente, com exceção de que ela pode incluir um arquivo de origem ou uma referência de assembly adicional.

## <a name="symbols"></a>Símbolos

Um símbolo representa um elemento distinto declarado pelo código-fonte ou importado de um assembly como metadados. Cada namespace, tipo, método, propriedade, campo, evento, parâmetro ou variável local é representado por um símbolo.

Uma variedade de métodos e propriedades no tipo <xref:Microsoft.CodeAnalysis.Compilation> ajudam você a encontrar símbolos. Por exemplo, encontre um símbolo para um tipo declarado pelo seu nome comum de metadados. Também acesse a tabela inteira de símbolos como uma árvore de símbolos com raiz no namespace global.

Os símbolos também contêm informações adicionais que o compilador determina da fonte ou dos metadados, como outros símbolos referenciados. Cada tipo de símbolo é representado por uma interface separada derivada de <xref:Microsoft.CodeAnalysis.ISymbol>, cada um com seus próprios métodos e propriedades que fornecem detalhes das informações reunidas pelo compilador. Muitas dessas propriedades referenciam outros símbolos diretamente. Por exemplo, a propriedade <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> informa o símbolo de tipo real referenciado pela declaração de método.

Os símbolos apresentam uma representação comum de namespaces, tipos e membros, entre o código-fonte e os metadados. Por exemplo, um método que foi declarado no código-fonte e um método que foi importado dos metadados são representados por um <xref:Microsoft.CodeAnalysis.IMethodSymbol> com as mesmas propriedades.

Símbolos são semelhantes em conceito ao sistema de tipos CLR, conforme representado pela API <xref:System.Reflection>, mas são mais sofisticados pois modelam mais do que apenas tipos. Namespaces, variáveis locais e rótulos são todos símbolos. Além disso, os símbolos são uma representação dos conceitos da linguagem, não dos conceitos do CLR. Há muita sobreposição, mas há muitas diferenças significativas também. Por exemplo, um método iterador no C# ou Visual Basic é um único símbolo. No entanto, quando o método iterador é convertido em metadados CLR, ele é um tipo e vários métodos.

## <a name="semantic-model"></a>Modelo semântico

Um modelo semântico representa todas as informações semânticas de um único arquivo de origem. Use-o para descobrir o seguinte:

- Os símbolos referenciados em um local específico na fonte.
- O tipo resultante de qualquer expressão.
- Todo o diagnóstico, que são erros e avisos.
- Como as variáveis fluem bidirecionalmente entre as regiões de origem.
- As respostas a perguntas mais especulativas.
