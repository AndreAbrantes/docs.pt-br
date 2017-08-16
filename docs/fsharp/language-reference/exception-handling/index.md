---
title: "Tratamento de exceções (F#)"
description: "Tratamento de exceções (F#)"
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
translationtype: Human Translation
ms.sourcegitcommit: 0a01ec92a90d99fafaacbd3f71f5177e5cf94a68
ms.openlocfilehash: d95aca8c511524f0b9af67b34a5999f885cf3aaf
ms.lasthandoff: 04/05/2017

---

# <a name="exception-handling"></a>Tratamento de Exceção

Esta seção contém informações sobre suporte à manipulação de exceção na linguagem F#.


## <a name="exception-handling-basics"></a>Noções básicas do tratamento de exceção
O tratamento de exceção é a maneira padrão de lidar com condições de erro no .NET Framework. Portanto, qualquer linguagem .NET deve oferecer suporte a esse mecanismo, incluindo F#. Um *exceção* é um objeto que encapsula informações sobre um erro. Quando ocorrem erros, as exceções são acionadas e a execução normal é interrompida. Em vez disso, o tempo de execução procura um manipulador apropriado para a exceção. A pesquisa começa na função atual e continua na pilha passando pelas camadas de chamadores até que um manipulador correspondente é encontrado. Em seguida, o manipulador é executado.

Além disso, à medida que a pilha é liberada, o tempo de execução executa qualquer código nos blocos `finally` para garantir que os objetos sejam limpos corretamente durante o processo de liberação.


## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Tipos de Exceção](exception-types.md)|Descreve como declarar um tipo de exceção.|
|[Exceções: a expressão `try...with`](the-try-with-expression.md)|Descreve a construção de linguagem que oferece suporte à manipulação da exceção.|
|[Exceções: a expressão `try...finally`](the-try-finally-expression.md)|Descreve a construção de linguagem que permite a execução do código de limpeza conforme a pilha é liberada quando uma exceção é lançada.|
|[Exceções: a função `raise`](the-raise-Function.md)|Descreve como lançar um objeto de exceção.|
|[Exceções: a função `failwith`](the-failwith-function.md)|Descreve como gerar uma exceção geral do F#.|
|[Exceções: a função `invalidArg`](the-invalidArg-function.md)|Descreve como gerar uma exceção de argumento inválido.|
