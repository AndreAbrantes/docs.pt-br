---
title: Função GetFileVersion
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 57b30824c7849127f48d4da61872945366e7141e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733237"
---
# <a name="getfileversion-function"></a><span data-ttu-id="2c1fd-102">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="2c1fd-102">GetFileVersion Function</span></span>

<span data-ttu-id="2c1fd-103">Obtém as informações de versão do Common Language Runtime (CLR) do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="2c1fd-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="2c1fd-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2c1fd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c1fd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c1fd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c1fd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c1fd-106">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="2c1fd-107">no O caminho do arquivo a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="2c1fd-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2c1fd-108">[entrada, saída] O buffer alocado para as informações de versão que são retornadas.</span><span class="sxs-lookup"><span data-stu-id="2c1fd-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2c1fd-109">no O tamanho, em caracteres largos, de `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="2c1fd-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2c1fd-110">fora O tamanho, em bytes, do retornado `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="2c1fd-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c1fd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c1fd-111">Requirements</span></span>  

 <span data-ttu-id="2c1fd-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c1fd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c1fd-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c1fd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c1fd-114">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1fd-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c1fd-115">See also</span></span>

- [<span data-ttu-id="2c1fd-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="2c1fd-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
