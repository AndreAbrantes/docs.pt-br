---
title: Enumeração RUNTIME_INFO_FLAGS
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 6f4fbb40053628d60ba7f094fcb5d50a94d63e1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729935"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="41d3f-102">Enumeração RUNTIME_INFO_FLAGS</span><span class="sxs-lookup"><span data-stu-id="41d3f-102">RUNTIME_INFO_FLAGS Enumeration</span></span>

<span data-ttu-id="41d3f-103">Contém valores que indicam quais informações sobre o Common Language Runtime (CLR) devem ser retornadas.</span><span class="sxs-lookup"><span data-stu-id="41d3f-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41d3f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="41d3f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="41d3f-105">Members</span></span>  
  
|<span data-ttu-id="41d3f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="41d3f-106">Member</span></span>|<span data-ttu-id="41d3f-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="41d3f-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="41d3f-108">Indica que as informações de diretório não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="41d3f-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="41d3f-109">Indica que as informações de versão não devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="41d3f-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="41d3f-110">Indica que uma caixa de diálogo de erro não deve ser exibida após a falha.</span><span class="sxs-lookup"><span data-stu-id="41d3f-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="41d3f-111">Indica que os efeitos da chamada da função [SetError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) com o sinalizador SEM_FAILCRITICALERRORS devem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="41d3f-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="41d3f-112">Ou seja, uma caixa de diálogo de instalação deve ser mostrada após a falha, em vez de ser suprimida.</span><span class="sxs-lookup"><span data-stu-id="41d3f-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="41d3f-113">Indica uma solicitação de informações sobre uma versão compatível com AMD-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41d3f-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="41d3f-114">Indica uma solicitação de informações sobre uma versão compatível com IA-64 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41d3f-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="41d3f-115">Indica uma solicitação de informações sobre uma versão compatível com x86 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41d3f-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="41d3f-116">Indica que as informações de atualização de versão devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="41d3f-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41d3f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="41d3f-117">Remarks</span></span>  

 <span data-ttu-id="41d3f-118">Os seguintes sinalizadores de arquitetura de plataforma podem ser especificados apenas um de cada vez e não podem ser combinados:</span><span class="sxs-lookup"><span data-stu-id="41d3f-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="41d3f-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="41d3f-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="41d3f-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="41d3f-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="41d3f-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="41d3f-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d3f-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41d3f-122">Requirements</span></span>  

 <span data-ttu-id="41d3f-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d3f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d3f-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41d3f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41d3f-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41d3f-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41d3f-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d3f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d3f-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="41d3f-127">See also</span></span>

- [<span data-ttu-id="41d3f-128">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="41d3f-128">Hosting Enumerations</span></span>](hosting-enumerations.md)
