---
title: Função CreateICeeFileGen
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673326"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="6808a-102">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="6808a-102">CreateICeeFileGen Function</span></span>

<span data-ttu-id="6808a-103">Cria um objeto [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="6808a-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="6808a-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6808a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6808a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6808a-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6808a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6808a-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="6808a-107">fora Um ponteiro para o endereço de um novo `ICeeFileGen` objeto.</span><span class="sxs-lookup"><span data-stu-id="6808a-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6808a-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6808a-108">Return Value</span></span>  

 <span data-ttu-id="6808a-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="6808a-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6808a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6808a-110">Remarks</span></span>  

 <span data-ttu-id="6808a-111">O `ICeeFileGen` objeto é usado para criar Common Language Runtime (CLR) arquivos executáveis portáteis (PE).</span><span class="sxs-lookup"><span data-stu-id="6808a-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="6808a-112">Chame a função [DestroyICeeFileGen](destroyiceefilegen-function.md) para destruir o `ICeeFileGen` objeto quando terminar.</span><span class="sxs-lookup"><span data-stu-id="6808a-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6808a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6808a-113">Requirements</span></span>  

 <span data-ttu-id="6808a-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6808a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6808a-115">**Cabeçalho:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="6808a-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="6808a-116">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="6808a-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="6808a-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6808a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6808a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="6808a-118">See also</span></span>

- [<span data-ttu-id="6808a-119">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="6808a-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
