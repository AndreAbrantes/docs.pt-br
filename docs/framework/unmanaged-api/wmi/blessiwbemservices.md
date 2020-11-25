---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais do usuário permitem o acesso a uma classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 43ef617ee754c9dcd661b31abba6b17434563c22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708147"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="883e2-103">Função BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="883e2-103">BlessIWbemServices function</span></span>

<span data-ttu-id="883e2-104">Indica se as credenciais do usuário permitem o acesso à classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificada.</span><span class="sxs-lookup"><span data-stu-id="883e2-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="883e2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="883e2-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="883e2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="883e2-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="883e2-107">no Um ponteiro para o objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) para o qual são necessárias permissões.</span><span class="sxs-lookup"><span data-stu-id="883e2-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="883e2-108">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="883e2-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="883e2-109">no A senha associada a `strUser` .</span><span class="sxs-lookup"><span data-stu-id="883e2-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="883e2-110">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="883e2-110">[in] The domain name of the user.</span></span> <span data-ttu-id="883e2-111">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="883e2-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="883e2-112">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="883e2-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="883e2-113">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="883e2-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="883e2-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="883e2-114">Return value</span></span>

<span data-ttu-id="883e2-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *Winerror. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="883e2-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="883e2-116">Constante</span><span class="sxs-lookup"><span data-stu-id="883e2-116">Constant</span></span>  |<span data-ttu-id="883e2-117">Valor</span><span class="sxs-lookup"><span data-stu-id="883e2-117">Value</span></span>  |<span data-ttu-id="883e2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="883e2-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="883e2-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="883e2-119">0x80070057</span></span> | <span data-ttu-id="883e2-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="883e2-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="883e2-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="883e2-121">0x80004003</span></span> | <span data-ttu-id="883e2-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="883e2-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="883e2-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="883e2-123">0x80000008</span></span> | <span data-ttu-id="883e2-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="883e2-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="883e2-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="883e2-125">0x80000002</span></span> | <span data-ttu-id="883e2-126">Memória insuficiente disponível para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="883e2-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="883e2-127">0</span><span class="sxs-lookup"><span data-stu-id="883e2-127">0</span></span> | <span data-ttu-id="883e2-128">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="883e2-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="883e2-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="883e2-129">Requirements</span></span>  

 <span data-ttu-id="883e2-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883e2-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883e2-131">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="883e2-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="883e2-132">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="883e2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883e2-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="883e2-133">See also</span></span>

- [<span data-ttu-id="883e2-134">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="883e2-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
