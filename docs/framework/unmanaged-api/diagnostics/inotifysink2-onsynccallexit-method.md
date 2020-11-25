---
title: Método INotifySink2::OnSyncCallExit
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 9049cd42e9c10cdcff62b005094b56c9df9ce975
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719990"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="1d852-102">Método INotifySink2::OnSyncCallExit</span><span class="sxs-lookup"><span data-stu-id="1d852-102">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="1d852-103">É invocado ao sair de uma chamada.</span><span class="sxs-lookup"><span data-stu-id="1d852-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d852-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d852-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d852-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d852-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="1d852-106">no ID da chamada sendo encerrada.</span><span class="sxs-lookup"><span data-stu-id="1d852-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="1d852-107">Consulte [estrutura de CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="1d852-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="1d852-108">fora Buffer de chamadas.</span><span class="sxs-lookup"><span data-stu-id="1d852-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="1d852-109">fora Tamanho do buffer de chamada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="1d852-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d852-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="1d852-110">Return Value</span></span>  

 <span data-ttu-id="1d852-111">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="1d852-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d852-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d852-112">Requirements</span></span>  

 <span data-ttu-id="1d852-113">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="1d852-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d852-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d852-114">See also</span></span>

- [<span data-ttu-id="1d852-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="1d852-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="1d852-116">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="1d852-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="1d852-117">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="1d852-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
