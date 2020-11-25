---
title: Método INotifyConnection2::RegisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 1286dd970e437af0a8b607ed050ab4838f73a41f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720042"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="6d07c-102">Método INotifyConnection2::RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="6d07c-102">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="6d07c-103">Instala uma fonte de notificação especificada.</span><span class="sxs-lookup"><span data-stu-id="6d07c-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d07c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d07c-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d07c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d07c-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="6d07c-106">no Especifica o objeto a ser usado como a fonte de notificação.</span><span class="sxs-lookup"><span data-stu-id="6d07c-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="6d07c-107">fora Recebe o objeto a ser usado como o coletor de notificação.</span><span class="sxs-lookup"><span data-stu-id="6d07c-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d07c-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6d07c-108">Return Value</span></span>  

 <span data-ttu-id="6d07c-109">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="6d07c-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d07c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d07c-110">Requirements</span></span>  

 <span data-ttu-id="6d07c-111">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="6d07c-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d07c-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d07c-112">See also</span></span>

- [<span data-ttu-id="6d07c-113">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="6d07c-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="6d07c-114">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="6d07c-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="6d07c-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="6d07c-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="6d07c-116">Método UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="6d07c-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
