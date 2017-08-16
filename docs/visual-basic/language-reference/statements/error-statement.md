---
title: "Instrução Error | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
dev_langs:
- VB
helpviewer_keywords:
- Error statement, syntax
- Error statement
- Error keyword
- run-time errors, codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 96ba2a726dc315dca227b4836aa987e1283cc39b
ms.lasthandoff: 03/13/2017

---
# <a name="error-statement"></a>Instrução Error
Simula a ocorrência de um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Partes  
 `errornumber`  
 Necessário. Pode ser qualquer número de erro válido.  
  
## <a name="remarks"></a>Comentários  
 O `Error` instrução é suportada para compatibilidade com versões anteriores. No novo código, especialmente ao criar objetos, use o `Err` do objeto `Raise` método para gerar erros de tempo de execução.  
  
 Se `errornumber` for definida, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:  
  
|Propriedade|Valor|  
|--------------|-----------|  
|`Number`|Valor especificado como argumento para `Error` instrução. Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto atual do Visual Basic.|  
|`Description`|Expressão correspondente para o valor de retorno de cadeia de caracteres de `Error` função especificado `Number`, se houver essa cadeia de caracteres. Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").|  
|`HelpFile`|A unidade totalmente qualificada, o caminho e o nome do arquivo de Ajuda do Visual Basic apropriado.|  
|`HelpContext`|ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic a `Number` propriedade.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existe, ou se nenhum está ativado, uma mensagem de erro é criada e exibida a partir de `Err` propriedades do objeto.  
  
> [!NOTE]
>  Alguns aplicativos de host do Visual Basic não podem criar objetos. Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Error` instrução para gerar o erro número 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A></xref:Microsoft.VisualBasic.ErrObject.Clear%2A>   
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A></xref:Microsoft.VisualBasic.ErrObject.Raise%2A>   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
