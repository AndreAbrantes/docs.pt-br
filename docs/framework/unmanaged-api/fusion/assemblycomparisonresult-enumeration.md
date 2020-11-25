---
title: Enumeração AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: cde25a9507006c89ef6490c13ae82033f04c2931
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731027"
---
# <a name="assemblycomparisonresult-enumeration"></a>Enumeração AssemblyComparisonResult

Indica a equivalência de duas identidades de assembly, conforme determinado pela função [CompareAssemblyIdentity](compareassemblyidentity-function.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|DESCRIÇÃO|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Indica que todos os campos de assembly na comparação correspondem.|  
|`ACR_EquivalentFXUnified`|Indica que os assemblies são considerados equivalentes com base na unificação da versão de Common Language Runtime (CLR) dos números de versão do assembly no .NET Framework versão 2,0.|  
|`ACR_EquivalentPartialFXUnified`|Indica uma correspondência parcial dos assemblies com base na Unificação de CLR dos números de versão do assembly no .NET Framework 2,0.|  
|`ACR_EquivalentPartialMatch`|Indica uma correspondência parcial dos assemblies.|  
|`ACR_EquivalentPartialUnified`|Indica uma correspondência parcial dos assemblies com base na Unificação herdada dos números de versão.|  
|`ACR_EquivalentPartialWeakNamed`|Indica uma correspondência parcial de apenas assemblies nomeados.|  
|`ACR_EquivalentUnified`|Indica que os assemblies são considerados equivalentes com base na Unificação CLR de números de versão em versões herdadas do .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Indica uma correspondência entre dois assemblies simplesmente nomeados cujos números de versão foram ignorados.|  
|`ACR_NonEquivalent`|Indica que nenhuma correspondência ocorreu entre os dois assemblies.|  
|`ACR_NonEquivalentPartialVersion`|Indica que os dois assemblies correspondem, exceto os números de versão, que correspondem apenas parcialmente.|  
|`ACR_NonEquivalentVersion`|Indica que os dois assemblies correspondem, exceto os números de versão, que não correspondem.|  
|`ACR_Unknown`|Indica que o motivo da não equivalência não é conhecido.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca:** Incluído como um recurso no MsCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função CompareAssemblyIdentity](compareassemblyidentity-function.md)
- [Enumerações Fusion](fusion-enumerations.md)
