---
title: Função CreateDebuggingInterfaceFromVersion
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: 6f5eec282aec6a2757664023ce8031410e316f10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501840"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="3c99d-102">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="3c99d-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="3c99d-103">Cria um objeto [ICorDebug](../debugging/icordebug-interface.md) com base nas informações de versão especificadas.</span><span class="sxs-lookup"><span data-stu-id="3c99d-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="3c99d-104">Essa função está obsoleta no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3c99d-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="3c99d-105">Em vez disso, para obter uma interface para o Common Language Runtime (CLR) 2,0, use o método [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="3c99d-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="3c99d-106">Para obter uma interface para o CLR 4 ou posterior, chame a função [CLRCreateInstance](clrcreateinstance-function.md) e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="3c99d-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c99d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c99d-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c99d-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c99d-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="3c99d-109">no A versão do `ICorDebug` que é esperada pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="3c99d-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="3c99d-110">Consulte a enumeração [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) para obter os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="3c99d-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="3c99d-111">no A versão de Common Language Runtime associada ao aplicativo ou processo a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="3c99d-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="3c99d-112">Consulte o método [GetVersionFromProcess](getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) para obter informações sobre como recuperar esse valor.</span><span class="sxs-lookup"><span data-stu-id="3c99d-112">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="3c99d-113">fora O local que recebe um ponteiro para o `ICorDebug` objeto.</span><span class="sxs-lookup"><span data-stu-id="3c99d-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c99d-114">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="3c99d-114">Return Value</span></span>  
 <span data-ttu-id="3c99d-115">Esse método retorna códigos de erro COM padrão, conforme definido no arquivo WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c99d-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="3c99d-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="3c99d-116">Return code</span></span>|<span data-ttu-id="3c99d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c99d-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3c99d-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c99d-118">S_OK</span></span>|<span data-ttu-id="3c99d-119">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c99d-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="3c99d-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3c99d-120">E_INVALIDARG</span></span>|<span data-ttu-id="3c99d-121">`szDebuggeeVersion`ou `ppCordb` é nulo ou a cadeia de caracteres da versão está incorreta.</span><span class="sxs-lookup"><span data-stu-id="3c99d-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c99d-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c99d-122">Remarks</span></span>  
 <span data-ttu-id="3c99d-123">O `szDebuggeeVersion` parâmetro é mapeado para a versão correspondente do MSCorDbi. dll.</span><span class="sxs-lookup"><span data-stu-id="3c99d-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c99d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c99d-124">Requirements</span></span>  
 <span data-ttu-id="3c99d-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c99d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c99d-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c99d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c99d-127">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3c99d-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c99d-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c99d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c99d-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c99d-129">See also</span></span>

- [<span data-ttu-id="3c99d-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="3c99d-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
