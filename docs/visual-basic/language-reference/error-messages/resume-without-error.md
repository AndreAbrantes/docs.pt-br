---
title: Retomar sem erro | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
dev_langs:
- VB
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
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
ms.openlocfilehash: 7228830df410049c4efa07e800babf6a2aa91a39
ms.lasthandoff: 03/13/2017

---
# <a name="resume-without-error"></a>Retomar sem erro
Um `Resume` instrução apareceu fora do código de tratamento de erros, ou o código entrou em um manipulador de erro mesmo que não houve erro.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Mova o `Resume`instrução em um manipulador de erro, ou excluí-lo.  
  
2.  Então vai para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro. Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é um `On Error GoTo` instrução, alterar o rótulo de linha de acordo com seu destino pretendido.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
