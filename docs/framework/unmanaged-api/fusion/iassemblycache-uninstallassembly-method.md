---
title: Método IAssemblyCache::UninstallAssembly
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 36a2a609e95740ffc45722635a7e1f09e0ed5601
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670778"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="6015d-102">Método IAssemblyCache::UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="6015d-102">IAssemblyCache::UninstallAssembly Method</span></span>

<span data-ttu-id="6015d-103">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6015d-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6015d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6015d-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6015d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6015d-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="6015d-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6015d-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="6015d-107">no O nome do assembly a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="6015d-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="6015d-108">no Uma estrutura de [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) que contém os dados de instalação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="6015d-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="6015d-109">[saída, opcional] Um dos valores de disposição definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6015d-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="6015d-110">Os possíveis valores incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="6015d-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="6015d-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="6015d-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="6015d-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="6015d-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="6015d-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="6015d-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="6015d-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="6015d-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="6015d-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="6015d-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="6015d-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="6015d-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6015d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6015d-117">Requirements</span></span>  

 <span data-ttu-id="6015d-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6015d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6015d-119">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6015d-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6015d-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6015d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6015d-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="6015d-121">See also</span></span>

- [<span data-ttu-id="6015d-122">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="6015d-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
