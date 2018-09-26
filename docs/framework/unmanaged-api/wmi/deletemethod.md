---
title: Função DeleteMethod (referência de API não gerenciada)
description: A função DeleteMethod exclui o método especificado de uma definição de classe do CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5996ce41c80cb54c4fcb9104c2993c85bcc2b466
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192294"
---
# <a name="deletemethod-function"></a><span data-ttu-id="831db-103">Função DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="831db-103">DeleteMethod function</span></span>
<span data-ttu-id="831db-104">Exclui o método especificado de uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="831db-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="831db-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="831db-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="831db-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="831db-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="831db-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="831db-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="831db-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="831db-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="831db-109">[in] O nome do método a ser removido da tabela de classe.</span><span class="sxs-lookup"><span data-stu-id="831db-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="831db-110">`wszName` deve ser um ponteiro para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="831db-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="831db-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="831db-111">Return value</span></span>

<span data-ttu-id="831db-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="831db-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="831db-113">Constante</span><span class="sxs-lookup"><span data-stu-id="831db-113">Constant</span></span>  |<span data-ttu-id="831db-114">Valor</span><span class="sxs-lookup"><span data-stu-id="831db-114">Value</span></span>  |<span data-ttu-id="831db-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="831db-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="831db-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="831db-116">0x80041002</span></span> | <span data-ttu-id="831db-117">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="831db-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="831db-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="831db-118">0x80041006</span></span> | <span data-ttu-id="831db-119">Não há memória suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="831db-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="831db-120">0</span><span class="sxs-lookup"><span data-stu-id="831db-120">0</span></span> | <span data-ttu-id="831db-121">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="831db-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="831db-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="831db-122">Remarks</span></span>

<span data-ttu-id="831db-123">Essa função encapsula uma chamada para o [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) método.</span><span class="sxs-lookup"><span data-stu-id="831db-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="831db-124">Não há suporte para a exclusão do método de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiros que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="831db-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="831db-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="831db-125">Requirements</span></span>  
 <span data-ttu-id="831db-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="831db-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="831db-127">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="831db-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="831db-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="831db-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831db-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="831db-129">See also</span></span>  
[<span data-ttu-id="831db-130">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="831db-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
