---
title: Interface ISymUnmanagedAsyncMethod
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 02b1866f2b9e89cdc8c8795f399ecc0c733c7202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707159"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="3c3ef-102">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="3c3ef-102">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="3c3ef-103">Essa interface é o complemento de leitura para a [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c3ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c3ef-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="3c3ef-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3c3ef-105">Methods</span></span>  

 <span data-ttu-id="3c3ef-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="3c3ef-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3c3ef-107">Método</span><span class="sxs-lookup"><span data-stu-id="3c3ef-107">Method</span></span>|<span data-ttu-id="3c3ef-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c3ef-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c3ef-109">Método GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="3c3ef-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="3c3ef-110">Consulte o [método DefineAsyncStepInfo](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="3c3ef-111">Método GetAsyncStepInfoCount</span><span class="sxs-lookup"><span data-stu-id="3c3ef-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="3c3ef-112">Consulte o [método DefineAsyncStepInfo](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="3c3ef-113">Método GetCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="3c3ef-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="3c3ef-114">Consulte o [método DefineCatchHandlerILOffset](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="3c3ef-115">Método GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="3c3ef-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="3c3ef-116">Consulte o [método DefineKickoffMethod](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="3c3ef-117">Método HasCatchHandlerILOffset</span><span class="sxs-lookup"><span data-stu-id="3c3ef-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="3c3ef-118">Consulte o [método DefineCatchHandlerILOffset](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3ef-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="3c3ef-119">Método IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="3c3ef-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="3c3ef-120">Verifica se o método tem informações assíncronas ou não.</span><span class="sxs-lookup"><span data-stu-id="3c3ef-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="3c3ef-121">Se esse método retornar `FALSE` , ele será inválido para chamar outros métodos nesta interface.</span><span class="sxs-lookup"><span data-stu-id="3c3ef-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="3c3ef-122">Eles serão retornados `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="3c3ef-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c3ef-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c3ef-123">Requirements</span></span>  

 <span data-ttu-id="3c3ef-124">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3c3ef-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3ef-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c3ef-125">See also</span></span>

- [<span data-ttu-id="3c3ef-126">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="3c3ef-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
