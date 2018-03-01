---
title: "Método ISymUnmanagedMethod::GetSequencePointCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf09a754c168a740942b60416b2c9589b12e7700
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="47868-102">Método ISymUnmanagedMethod::GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="47868-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="47868-103">Obtém a contagem de pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="47868-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47868-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47868-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47868-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47868-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="47868-106">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="47868-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47868-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47868-107">Return Value</span></span>  
 <span data-ttu-id="47868-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="47868-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47868-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47868-109">Requirements</span></span>  
 <span data-ttu-id="47868-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47868-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47868-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47868-111">See Also</span></span>  
 [<span data-ttu-id="47868-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="47868-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
