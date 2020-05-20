---
title: Função _CorValidateImage
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616496"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="e0870-102">Função _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="e0870-102">_CorValidateImage Function</span></span>
<span data-ttu-id="e0870-103">Valida as imagens de módulo gerenciado e notifica o carregador do sistema operacional depois que elas tiverem sido carregadas.</span><span class="sxs-lookup"><span data-stu-id="e0870-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0870-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0870-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0870-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0870-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="e0870-106">no Um ponteiro para o local inicial da imagem a ser validada como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e0870-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="e0870-107">A imagem já deve estar carregada na memória.</span><span class="sxs-lookup"><span data-stu-id="e0870-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="e0870-108">no O nome do arquivo da imagem.</span><span class="sxs-lookup"><span data-stu-id="e0870-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0870-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e0870-109">Return Value</span></span>  
 <span data-ttu-id="e0870-110">Essa função retorna os valores padrão `E_INVALIDARG` , `E_OUTOFMEMORY` , `E_UNEXPECTED` e `E_FAIL` , bem como os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0870-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="e0870-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e0870-111">Return value</span></span>|<span data-ttu-id="e0870-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0870-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="e0870-113">A imagem é inválida.</span><span class="sxs-lookup"><span data-stu-id="e0870-113">The image is invalid.</span></span> <span data-ttu-id="e0870-114">Esse valor tem o HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="e0870-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="e0870-115">A imagem é válida.</span><span class="sxs-lookup"><span data-stu-id="e0870-115">The image is valid.</span></span> <span data-ttu-id="e0870-116">Esse valor tem o HRESULT 0x00000000l.</span><span class="sxs-lookup"><span data-stu-id="e0870-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0870-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0870-117">Remarks</span></span>  
 <span data-ttu-id="e0870-118">No Windows XP e versões posteriores, o carregador do sistema operacional verifica módulos gerenciados examinando o bit do diretório do descritor COM no cabeçalho COFF (Common Object File Format).</span><span class="sxs-lookup"><span data-stu-id="e0870-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="e0870-119">Um bit definido indica um módulo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e0870-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="e0870-120">Se o carregador detectar um módulo gerenciado, ele carregará o MsCorEE. dll e `_CorValidateImage` as chamadas, que executarão as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="e0870-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="e0870-121">Confirma que a imagem é um módulo gerenciado válido.</span><span class="sxs-lookup"><span data-stu-id="e0870-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="e0870-122">Altera o ponto de entrada na imagem para um ponto de entrada no Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e0870-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="e0870-123">Para versões de 64 bits do Windows, o modifica a imagem que está na memória transformando-a de PE32 para PE32 + Format.</span><span class="sxs-lookup"><span data-stu-id="e0870-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="e0870-124">Retorna ao carregador quando as imagens de módulo gerenciado são carregadas.</span><span class="sxs-lookup"><span data-stu-id="e0870-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="e0870-125">Para imagens executáveis, o carregador do sistema operacional chama a função [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) , independentemente do ponto de entrada especificado no executável.</span><span class="sxs-lookup"><span data-stu-id="e0870-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="e0870-126">Para imagens de assembly de DLL, o carregador chama a função [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="e0870-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="e0870-127">`_CorExeMain`ou `_CorDllMain` executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="e0870-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="e0870-128">Inicializa o CLR.</span><span class="sxs-lookup"><span data-stu-id="e0870-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="e0870-129">Localiza o ponto de entrada gerenciado do cabeçalho CLR do assembly.</span><span class="sxs-lookup"><span data-stu-id="e0870-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="e0870-130">Inicia a execução.</span><span class="sxs-lookup"><span data-stu-id="e0870-130">Begins execution.</span></span>  
  
 <span data-ttu-id="e0870-131">O carregador chama a função [_CorImageUnloading](corimageunloading-function.md) quando as imagens de módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="e0870-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="e0870-132">No entanto, essa função não executa nenhuma ação; Ele apenas retorna.</span><span class="sxs-lookup"><span data-stu-id="e0870-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0870-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0870-133">Requirements</span></span>  
 <span data-ttu-id="e0870-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0870-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0870-135">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e0870-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0870-136">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0870-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0870-137">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0870-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0870-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="e0870-138">See also</span></span>

- [<span data-ttu-id="e0870-139">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="e0870-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
