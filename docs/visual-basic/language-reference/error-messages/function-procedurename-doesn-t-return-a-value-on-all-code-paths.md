---
title: A função '<procedurename>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 19b305e337767dfb34718aed7b665f142851bd36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163357"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>BC42105: a função ' \<procedurename> ' não retorna um valor em todos os caminhos de código

A função ' \<procedurename> ' não retorna um valor em todos os caminhos de código. Você está perdendo uma instrução ' Return '?

 Um `Function` procedimento tem pelo menos um caminho possível por meio de seu código que não retorna um valor.

 Você pode retornar um valor de um `Function` procedimento de qualquer uma das seguintes maneiras:

- Inclua o valor em uma [instrução return](../statements/return-statement.md).

- Atribua o valor ao `Function` nome do procedimento e, em seguida, execute uma `Exit Function` instrução.

- Atribua o valor ao `Function` nome do procedimento e, em seguida, execute a `End Function` instrução.

 Se o controle passar para `Exit Function` ou `End Function` e você não tiver atribuído nenhum valor ao nome do procedimento, o procedimento retornará o valor padrão do tipo de dados de retorno. Para obter mais informações, consulte "Behavior" na [instrução function](../statements/function-statement.md).

 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID do erro:** BC42105

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Verifique sua lógica de fluxo de controle e certifique-se de atribuir um valor antes de cada instrução que causa um retorno.

     É mais fácil garantir que cada retorno do procedimento retorne um valor se você sempre usar a `Return` instrução. Se você fizer isso, a última instrução antes `End Function` deve ser uma `Return` instrução.

## <a name="see-also"></a>Veja também

- [Procedimentos de função](../../programming-guide/language-features/procedures/function-procedures.md)
- [Instrução Function](../statements/function-statement.md)
- [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
