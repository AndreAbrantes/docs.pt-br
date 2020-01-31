---
title: Método ICorDebugRegisterSet::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792115"
---
# <a name="icordebugregistersetgetregisters-method"></a>Método ICorDebugRegisterSet::GetRegisters
Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mask`  
 no Uma máscara de bits que especifica quais valores de registro devem ser recuperados. Cada bit corresponde a um registro. Se um bit for definido como um, o valor do registro será recuperado; caso contrário, o valor do registro não será recuperado.  
  
 `regCount`  
 no O número de valores de registro a serem recuperados.  
  
 `regBuffer`  
 fora Uma matriz de objetos `CORDB_REGISTER`, cada um dos quais recebe um valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O tamanho da matriz deve ser igual ao número de bits definido como um na máscara de bits. O parâmetro `regCount` especifica o número de elementos no buffer que receberão os valores de registro. Se o valor de `regCount` for muito pequeno para o número de registros indicado pela máscara, os registros numerados mais altos serão truncados do conjunto. Se o valor de `regCount` for muito grande, os elementos de `regBuffer` não utilizados não serão modificados.  
  
 Se a máscara de bits especificar um registro que não está disponível, `GetRegisters` retornará um valor indeterminado para esse registro.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
