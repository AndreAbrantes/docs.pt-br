---
title: "Função GetQualifierSet (referência de API não gerenciada)"
description: "A função GetQualifierSet recupera o qualificador definido para uma classe ou instância."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 127e7862d0cb0d204e91cd5ee36f2d32f1453a8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getqualifierset-function"></a><span data-ttu-id="4f96f-103">Função GetQualifierSet</span><span class="sxs-lookup"><span data-stu-id="4f96f-103">GetQualifierSet function</span></span>
<span data-ttu-id="4f96f-104">Recupera o qualificador definido para uma instância da classe ou uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="4f96f-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4f96f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f96f-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="4f96f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f96f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4f96f-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="4f96f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4f96f-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="4f96f-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="4f96f-109">[out] Recebe o ponteiro de interface que permite acessar os qualificadores do objeto de classe.</span><span class="sxs-lookup"><span data-stu-id="4f96f-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="4f96f-110">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="4f96f-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="4f96f-111">Se ocorrer um erro, um novo objeto não é retornado e o ponteiro for deixado sem modificações.</span><span class="sxs-lookup"><span data-stu-id="4f96f-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4f96f-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4f96f-112">Return value</span></span>

<span data-ttu-id="4f96f-113">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="4f96f-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4f96f-114">Constante</span><span class="sxs-lookup"><span data-stu-id="4f96f-114">Constant</span></span>  |<span data-ttu-id="4f96f-115">Valor</span><span class="sxs-lookup"><span data-stu-id="4f96f-115">Value</span></span>  |<span data-ttu-id="4f96f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f96f-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="4f96f-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4f96f-117">0x80041001</span></span> | <span data-ttu-id="4f96f-118">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="4f96f-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4f96f-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4f96f-119">0x80041002</span></span> | <span data-ttu-id="4f96f-120">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="4f96f-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4f96f-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4f96f-121">0x80041006</span></span> | <span data-ttu-id="4f96f-122">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="4f96f-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4f96f-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4f96f-123">0x80041008</span></span> | <span data-ttu-id="4f96f-124">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="4f96f-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4f96f-125">0</span><span class="sxs-lookup"><span data-stu-id="4f96f-125">0</span></span> | <span data-ttu-id="4f96f-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4f96f-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4f96f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f96f-127">Remarks</span></span>

<span data-ttu-id="4f96f-128">Essa função encapsula uma chamada para o [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="4f96f-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="4f96f-129">O [IWbemQualifierSet ponteiro](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permite que o chamador adicionar, editar ou excluir esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="4f96f-129">The [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="4f96f-130">Esses qualificadores adicionados, excluídos ou editados se aplicam à definição de classe ou instância inteira.</span><span class="sxs-lookup"><span data-stu-id="4f96f-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f96f-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f96f-131">Requirements</span></span>  
<span data-ttu-id="4f96f-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f96f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f96f-133">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4f96f-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4f96f-134">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f96f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f96f-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f96f-135">See also</span></span>  
[<span data-ttu-id="4f96f-136">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="4f96f-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
