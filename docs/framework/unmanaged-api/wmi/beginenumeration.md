---
title: Função BeginEnumeration (referência de API não gerenciada)
description: A função BeginEnumeration redefine um enumerador para o início da enumeração
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708212"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="40082-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="40082-103">BeginEnumeration function</span></span>

<span data-ttu-id="40082-104">Redefine um enumerador de volta para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="40082-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="40082-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40082-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="40082-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40082-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="40082-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="40082-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="40082-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="40082-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="40082-109">no Uma combinação de bits de bit que indica os sinalizadores ou valores descritos na seção [comentários](#remarks) que controla as propriedades incluídas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="40082-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="40082-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="40082-110">Return value</span></span>

<span data-ttu-id="40082-111">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="40082-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="40082-112">Constante</span><span class="sxs-lookup"><span data-stu-id="40082-112">Constant</span></span>  |<span data-ttu-id="40082-113">Valor</span><span class="sxs-lookup"><span data-stu-id="40082-113">Value</span></span>  |<span data-ttu-id="40082-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="40082-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="40082-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="40082-115">0x80041008</span></span> | <span data-ttu-id="40082-116">A combinação de sinalizadores no `lEnumFlags` é inválida ou um argumento inválido foi especificado.</span><span class="sxs-lookup"><span data-stu-id="40082-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="40082-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="40082-117">0x8004101d</span></span> | <span data-ttu-id="40082-118">Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [`EndEnumeration`](endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="40082-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="40082-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="40082-119">0x80041006</span></span> | <span data-ttu-id="40082-120">Não há memória suficiente disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="40082-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="40082-121">0</span><span class="sxs-lookup"><span data-stu-id="40082-121">0</span></span> | <span data-ttu-id="40082-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="40082-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="40082-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="40082-123">Remarks</span></span>

<span data-ttu-id="40082-124">Essa função encapsula uma chamada para o método [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="40082-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="40082-125">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="40082-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="40082-126">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de qualquer outro grupo.</span><span class="sxs-lookup"><span data-stu-id="40082-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="40082-127">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="40082-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="40082-128">**Grupo 1**</span><span class="sxs-lookup"><span data-stu-id="40082-128">**Group 1**</span></span>

|<span data-ttu-id="40082-129">Constante</span><span class="sxs-lookup"><span data-stu-id="40082-129">Constant</span></span>  |<span data-ttu-id="40082-130">Valor</span><span class="sxs-lookup"><span data-stu-id="40082-130">Value</span></span>  |<span data-ttu-id="40082-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="40082-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="40082-132">0x4</span><span class="sxs-lookup"><span data-stu-id="40082-132">0x4</span></span> | <span data-ttu-id="40082-133">Inclua propriedades que constituem apenas a chave.</span><span class="sxs-lookup"><span data-stu-id="40082-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="40082-134">0x8</span><span class="sxs-lookup"><span data-stu-id="40082-134">0x8</span></span> | <span data-ttu-id="40082-135">Inclua propriedades que são referências de objeto apenas.</span><span class="sxs-lookup"><span data-stu-id="40082-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="40082-136">**Grupo 2**</span><span class="sxs-lookup"><span data-stu-id="40082-136">**Group 2**</span></span>

<span data-ttu-id="40082-137">Constante</span><span class="sxs-lookup"><span data-stu-id="40082-137">Constant</span></span>  |<span data-ttu-id="40082-138">Valor</span><span class="sxs-lookup"><span data-stu-id="40082-138">Value</span></span>  |<span data-ttu-id="40082-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="40082-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="40082-140">0x30</span><span class="sxs-lookup"><span data-stu-id="40082-140">0x30</span></span> | <span data-ttu-id="40082-141">Limitar a enumeração somente às propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="40082-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="40082-142">0x40</span><span class="sxs-lookup"><span data-stu-id="40082-142">0x40</span></span> | <span data-ttu-id="40082-143">Incluir propriedades locais e propagadas, mas excluir propriedades do sistema da enumeração.</span><span class="sxs-lookup"><span data-stu-id="40082-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="40082-144">Para classes:</span><span class="sxs-lookup"><span data-stu-id="40082-144">For classes:</span></span>

<span data-ttu-id="40082-145">Constante</span><span class="sxs-lookup"><span data-stu-id="40082-145">Constant</span></span>  |<span data-ttu-id="40082-146">Valor</span><span class="sxs-lookup"><span data-stu-id="40082-146">Value</span></span>  |<span data-ttu-id="40082-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="40082-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="40082-148">0x100</span><span class="sxs-lookup"><span data-stu-id="40082-148">0x100</span></span> | <span data-ttu-id="40082-149">Limite a enumeração às propriedades substituídas na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="40082-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="40082-150">0x100</span><span class="sxs-lookup"><span data-stu-id="40082-150">0x100</span></span> | <span data-ttu-id="40082-151">Limitar a enumeração às propriedades substituídas na definição de classe atual e às novas propriedades definidas na classe.</span><span class="sxs-lookup"><span data-stu-id="40082-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="40082-152">0x300</span><span class="sxs-lookup"><span data-stu-id="40082-152">0x300</span></span> | <span data-ttu-id="40082-153">Uma máscara (em vez de um sinalizador) a ser aplicada a um `lEnumFlags` valor para verificar se `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` está definido.</span><span class="sxs-lookup"><span data-stu-id="40082-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="40082-154">0x10</span><span class="sxs-lookup"><span data-stu-id="40082-154">0x10</span></span> | <span data-ttu-id="40082-155">Limite a enumeração a propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="40082-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="40082-156">0x20</span><span class="sxs-lookup"><span data-stu-id="40082-156">0x20</span></span> | <span data-ttu-id="40082-157">Limite a enumeração a propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="40082-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="40082-158">Para instâncias:</span><span class="sxs-lookup"><span data-stu-id="40082-158">For instances:</span></span>

<span data-ttu-id="40082-159">Constante</span><span class="sxs-lookup"><span data-stu-id="40082-159">Constant</span></span>  |<span data-ttu-id="40082-160">Valor</span><span class="sxs-lookup"><span data-stu-id="40082-160">Value</span></span>  |<span data-ttu-id="40082-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="40082-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="40082-162">0x10</span><span class="sxs-lookup"><span data-stu-id="40082-162">0x10</span></span> | <span data-ttu-id="40082-163">Limite a enumeração a propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="40082-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="40082-164">0x20</span><span class="sxs-lookup"><span data-stu-id="40082-164">0x20</span></span> | <span data-ttu-id="40082-165">Limite a enumeração a propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="40082-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="40082-166">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40082-166">Requirements</span></span>  

 <span data-ttu-id="40082-167">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40082-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40082-168">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="40082-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="40082-169">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="40082-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40082-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="40082-170">See also</span></span>

- [<span data-ttu-id="40082-171">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="40082-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
