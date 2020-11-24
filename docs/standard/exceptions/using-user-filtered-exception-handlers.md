---
title: Usando manipuladores de exceções filtrados pelo usuário
ms.date: 03/30/2017
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 4b85c2be0ed61af38eac1b65fb70f0ef1ea4405e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669036"
---
# <a name="using-user-filtered-exception-handlers"></a>Usando manipuladores de exceções filtrados pelo usuário

Atualmente, o Visual Basic dá suporte a exceções filtradas pelo usuário. Os manipuladores de exceção filtrados por usuário capturam e tratam exceções com base nos requisitos que você define para a exceção. Esses manipuladores usam a instrução **Catch** com a palavra-chave **When**.  
  
 Essa técnica é útil quando um objeto de exceção em particular corresponde a vários erros. Nesse caso, o objeto normalmente tem uma propriedade que contém o código de erro específico associado ao erro. Você pode usar a propriedade do código de erro na expressão para selecionar apenas o erro específico que você deseja manipular na cláusula **Catch**.  
  
 O exemplo do Visual Basic a seguir ilustra a instrução **Catch/When**.  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 A expressão da cláusula filtrada pelo usuário não é restrita de nenhuma forma. Se ocorrer uma exceção durante a execução da expressão filtrada pelo usuário, essa exceção será descartada e será considerado que a expressão do filtro foi avaliada como falsa. Nesse caso, o Common Language Runtime continua a pesquisar um manipulador para a exceção atual.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Combinar a exceção específica e as cláusulas filtradas pelo usuário  

 Uma instrução catch pode contar a exceção específica e as cláusulas filtradas pelo usuário. O runtime testa primeiro a exceção específica. Se a exceção específica for bem-sucedida, o runtime executará o filtro do usuário. O filtro genérico pode conter uma referência à variável declarada no filtro da classe. Observe que a ordem das duas cláusulas do filtro não pode ser invertida.  
  
 O seguinte exemplo do Visual Basic mostra a exceção específica `ClassLoadException` na instrução **Catch**, além da cláusula filtrada pelo usuário usando a palavra-chave **When**.  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Confira também

- [Exceções](index.md)
