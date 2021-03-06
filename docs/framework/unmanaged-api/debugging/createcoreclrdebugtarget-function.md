---
title: Função CreateCoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: f0188facf0b7d33e6e1ecc12921a139165f777a1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686625"
---
# <a name="createcoreclrdebugtarget-function"></a>Função CreateCoreClrDebugTarget

Cria uma conexão com um proxy de depurador que está sendo executado em um computador remoto e retorna um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que pode ser usado para consultar processos em execução e os tempos de execução carregados no computador remoto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `dwAddress`  
 no Endereço IPv4 de um computador de destino remoto.  
  
 `ppTarget`  
 fora Ponteiro para um ponteiro para um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que será criado.  
  
## <a name="return-value"></a>Valor Retornado  

 S_OK  
 O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.  
  
 E_OUTOFMEMORY  
 Não é possível alocar memória suficiente para `ppTarget` .  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Outras falhas.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET Framework:** 3,5 SP1
