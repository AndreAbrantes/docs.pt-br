---
title: Função ClrCreateManagedInstance
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 9aed79138499f1aa7b6fa3a28ad4505edd51b041
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731755"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="4b5b3-102">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="4b5b3-102">ClrCreateManagedInstance Function</span></span>

<span data-ttu-id="4b5b3-103">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="4b5b3-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="4b5b3-105">Use a ativação COM para criar uma instância do tipo gerenciado ou use a hospedagem (consulte [interfaces de hospedagem do CLR adicionadas no .NET Framework 4 e 4,5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="4b5b3-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5b3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b5b3-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b5b3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b5b3-107">Parameters</span></span>  

 `pTypeName`  
 <span data-ttu-id="4b5b3-108">no Um ponteiro para o nome do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="4b5b3-109">no O `IID` do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="4b5b3-110">fora Um ponteiro para um ponteiro para uma instância do tipo gerenciado que foi solicitado pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b5b3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b5b3-111">Remarks</span></span>  

 <span data-ttu-id="4b5b3-112">O Common Language Runtime já deve estar carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="4b5b3-113">Por exemplo, ele pode ser carregado usando uma chamada para a função [CorBindToRuntimeEx](corbindtoruntimeex-function.md) antes que a `ClrCreateManagedInstance` função seja chamada.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="4b5b3-114">Se o tempo de execução não for carregado, o `ClrCreateManagedInstance` primeiro tentará carregar v 1.0.3705 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="4b5b3-115">Se isso falhar, ele tentará carregar a versão mais recente do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4b5b3-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b5b3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b5b3-116">Requirements</span></span>  

 <span data-ttu-id="4b5b3-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b5b3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b5b3-118">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b5b3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b5b3-119">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b5b3-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b5b3-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b5b3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5b3-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b5b3-121">See also</span></span>

- [<span data-ttu-id="4b5b3-122">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="4b5b3-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="4b5b3-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="4b5b3-123">Hosting</span></span>](index.md)
