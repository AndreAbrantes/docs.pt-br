---
title: função QualifierSet_Delete (referência de API não gerenciada)
description: A função QualifierSet_Delete exclui um qualificador pelo nome.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174895"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="c3f76-103">Função QualifierSet_Delete</span><span class="sxs-lookup"><span data-stu-id="c3f76-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="c3f76-104">Exclui um qualificador especificado por nome.</span><span class="sxs-lookup"><span data-stu-id="c3f76-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c3f76-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3f76-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="c3f76-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3f76-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c3f76-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="c3f76-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="c3f76-108">`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="c3f76-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="c3f76-109">`wszName`[em] O nome do qualificador para excluir.</span><span class="sxs-lookup"><span data-stu-id="c3f76-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3f76-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c3f76-110">Return value</span></span>

<span data-ttu-id="c3f76-111">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c3f76-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c3f76-112">Constante</span><span class="sxs-lookup"><span data-stu-id="c3f76-112">Constant</span></span>  |<span data-ttu-id="c3f76-113">Valor</span><span class="sxs-lookup"><span data-stu-id="c3f76-113">Value</span></span>  |<span data-ttu-id="c3f76-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f76-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c3f76-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c3f76-115">0x80041008</span></span> | <span data-ttu-id="c3f76-116">O parâmetro `wszName` não é válido.</span><span class="sxs-lookup"><span data-stu-id="c3f76-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="c3f76-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c3f76-117">0x80041016</span></span> | <span data-ttu-id="c3f76-118">Excluir este qualificador é ilegal.</span><span class="sxs-lookup"><span data-stu-id="c3f76-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c3f76-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c3f76-119">0x80041002</span></span> | <span data-ttu-id="c3f76-120">O qualificador especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="c3f76-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c3f76-121">0</span><span class="sxs-lookup"><span data-stu-id="c3f76-121">0</span></span> | <span data-ttu-id="c3f76-122">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c3f76-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="c3f76-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="c3f76-123">0x40002</span></span> | <span data-ttu-id="c3f76-124">A substituição local foi excluída e o qualificador original do objeto pai retomou o escopo.</span><span class="sxs-lookup"><span data-stu-id="c3f76-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c3f76-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3f76-125">Remarks</span></span>

<span data-ttu-id="c3f76-126">Esta função envolve uma chamada para o método [IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)</span><span class="sxs-lookup"><span data-stu-id="c3f76-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="c3f76-127">Devido às regras de propagação do qualificador, um qualificador em particular pode ter sido herdado de outro objeto e meramente substituído na classe ou instância atual.</span><span class="sxs-lookup"><span data-stu-id="c3f76-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="c3f76-128">Neste caso, `QualifierSet_Delete` o método redefine o qualificador ao seu valor herdado original.</span><span class="sxs-lookup"><span data-stu-id="c3f76-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="c3f76-129">A função neste caso retorna `WBEM_S_RESET_TO_DEFAULT`o código de status .</span><span class="sxs-lookup"><span data-stu-id="c3f76-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3f76-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3f76-130">Requirements</span></span>  
 <span data-ttu-id="c3f76-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f76-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f76-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c3f76-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c3f76-133">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f76-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f76-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3f76-134">See also</span></span>

- [<span data-ttu-id="c3f76-135">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c3f76-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
