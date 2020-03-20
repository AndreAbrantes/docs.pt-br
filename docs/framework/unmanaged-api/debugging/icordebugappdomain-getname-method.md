---
title: Método ICorDebugAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179083"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="fe23a-102">Método ICorDebugAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="fe23a-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="fe23a-103">Obtém o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe23a-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe23a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe23a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe23a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe23a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fe23a-106">[em] O tamanho `szName` da matriz.</span><span class="sxs-lookup"><span data-stu-id="fe23a-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="fe23a-107">Defina esse valor como zero para colocar este método no modo de consulta.</span><span class="sxs-lookup"><span data-stu-id="fe23a-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fe23a-108">[fora] Um ponteiro para o tamanho do nome ou o `szName`número de caracteres realmente retornado em .</span><span class="sxs-lookup"><span data-stu-id="fe23a-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="fe23a-109">No modo de consulta, este valor permite que o chamador saiba o tamanho de um buffer para alocar para o nome.</span><span class="sxs-lookup"><span data-stu-id="fe23a-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="fe23a-110">[fora] Uma matriz que armazena o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe23a-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe23a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe23a-111">Remarks</span></span>  
 <span data-ttu-id="fe23a-112">Um depurador `GetName` chama o método uma vez para obter o tamanho de um buffer necessário para o nome.</span><span class="sxs-lookup"><span data-stu-id="fe23a-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="fe23a-113">O depurador aloca o buffer e, em seguida, chama o método uma segunda vez para preencher o buffer.</span><span class="sxs-lookup"><span data-stu-id="fe23a-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="fe23a-114">A primeira chamada, para obter o tamanho do nome, é referida como *modo de consulta*.</span><span class="sxs-lookup"><span data-stu-id="fe23a-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe23a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe23a-115">Requirements</span></span>  
 <span data-ttu-id="fe23a-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe23a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe23a-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe23a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe23a-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe23a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe23a-119">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe23a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
