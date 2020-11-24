---
title: Função CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 575e194cf952f02a3fe4fce9e955e45e1bc3653d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673907"
---
# <a name="closeclrenumeration-function"></a>Função CloseCLREnumeration

Fecha os eventos de inicialização de continuação de Common Language Runtime (CLR) válidos localizados em uma matriz de identificadores retornada pela [função EnumerateCLRs](enumerateclrs-function.md)e libera a memória para as matrizes de caminho de cadeia de caracteres e identificador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pHandleArray`  
 no Ponteiro para a matriz de identificadores de eventos retornados da [função EnumerateCLRs](enumerateclrs-function.md).  
  
 `pStringArray`  
 no Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornados da [função EnumerateCLRs](enumerateclrs-function.md).  
  
 `dwArrayLength`  
 no DWORD que contém o tamanho (comprimento) de `pHandleArray` ou `pStringArray` (eles são os mesmos).  
  
## <a name="return-value"></a>Valor Retornado  

 S_OK  
 Os identificadores abertos pela [função EnumerateCLRs](enumerateclrs-function.md) são fechados e a memória alocada para o identificador e as matrizes de cadeia de caracteres é liberada.  
  
 E_INVALIDARG  
 O comprimento de não `pHandleArray` corresponde ao comprimento passado `dwArrayLength` .  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 A função não pode liberar a memória para `pHandleArray` e `pStringArray` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim. h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET Framework:** 3,5 SP1
