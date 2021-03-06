---
title: Comprimento de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869256"
---
# <a name="bad-record-length"></a>Comprimento de registro inválido

Entre as possíveis causas desse erro estão:  
  
- O comprimento de uma variável de registro especificada em `FileGet` uma `FileGetObject` `FilePut` instrução, ou `FilePutObject` difere do comprimento especificado na `FileOpen` instrução correspondente.  
  
- A variável em uma `FilePut` `FilePutObject` instrução or é ou inclui uma cadeia de caracteres de comprimento variável.  
  
- A variável em um `FilePut` ou `FilePutObject` é ou inclui um `Variant` tipo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo da variável de registro é igual ao valor indicado na `FileOpen` cláusula da instrução `Len` .  
  
2. Se a variável em uma `FilePut` `FilePutObject` instrução or for ou incluir uma cadeia de caracteres de comprimento variável, certifique-se de que a cadeia de caracteres de comprimento variável tenha pelo menos 2 caracteres mais curto do que o tamanho do registro especificado na `Len` cláusula da `FileOpen` instrução.  
  
3. Se a variável em um `FilePut` ou `FilePutObject` for ou incluir uma `Variant` , verifique se a cadeia de caracteres de comprimento variável tem pelo menos 4 bytes de comprimento menor do que o tamanho do registro especificado na `Len` cláusula da `FileOpen` instrução.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
