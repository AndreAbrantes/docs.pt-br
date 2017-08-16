---
title: "Resumo de árvores de expressão"
description: "Resumo de árvores de expressão"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 82d4684ed27b23afd4972da6f68d1757472d85b6
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---

# <a name="expression-trees-summary"></a>Resumo de árvores de expressão

[Anterior – Movendo expressões](expression-trees-translating.md)

Nesta série, você viu como é possível usar as *árvores de expressão* para criar programas dinâmicos que interpretam o código como dados e criam uma nova funcionalidade com base nesse código.

Você pode examinar as árvores de expressão para entender a intenção de um algoritmo. E não apenas examinar esse código. Você pode criar novas árvores de expressão que representam versões modificadas do código original.

E também pode usar as árvores de expressão para examinar um algoritmo e mover esse algoritmo para outra linguagem ou ambiente. 

## <a name="limitations"></a>Limitações

Há alguns elementos mais recentes da linguagem C# que não se convertem bem em árvores de expressão. As árvores de expressão não podem conter expressões `await` ou expressões lambda `async`. Muitos dos recursos adicionados na versão 6 do C# não aparecem exatamente como escritos nas árvores de expressão. Em vez disso, os recursos mais recentes serão expostos em árvores de expressões na sintaxe anterior equivalente. Isso pode não ser realmente uma limitação como você imagina. Na verdade, isso significa que é provável que o seu código, que interpreta árvores de expressão, vai continuar funcionando da mesma forma que quando os novos recursos de linguagem forem introduzidos.

Mesmo com essas limitações, as árvores de expressão permitem criar algoritmos dinâmicos que se apoiam na interpretação e modificação do código que é representado como uma estrutura de dados. Elas são uma ferramenta poderosa e é um dos recursos do ecossistema do .NET que habilita as avançadas bibliotecas, como o Entity Framework, a realizarem o que fazem.


