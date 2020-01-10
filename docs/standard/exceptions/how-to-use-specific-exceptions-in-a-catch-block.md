---
title: Como usar exceções específicas em um bloco catch
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 6f0956c6418d894a5768463861151f86a1948850
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708575"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Como usar exceções específicas em um bloco catch

Em geral, é uma boa prática capturar um tipo específico de exceção em vez de usar a instrução básica `catch`.

Quando ocorre uma exceção, ela é passada para cima na pilha e, a cada bloco catch, é dada a oportunidade de tratá-la. A ordem das instruções catch é importante. Coloque blocos catch direcionados para exceções específicas antes que um bloco catch de exceção geral ou o compilador possa emitir um erro. O bloco catch adequado é determinado ao fazer a correspondência entre o tipo da exceção e o nome da exceção especificada no bloco catch. Se não houver nenhum bloco catch específico, a exceção será detectada por um bloco catch geral, se houver.

O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma <xref:System.InvalidCastException>. O exemplo cria uma classe chamada `Employee` com uma única propriedade, nível do funcionário (`Emlevel`). Um método, `PromoteEmployee`, utiliza um objeto e incrementa o nível do funcionário. Um <xref:System.InvalidCastException> ocorre quando uma instância <xref:System.DateTime> é passada para o método `PromoteEmployee`.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Veja também

- [Exceções](index.md)
