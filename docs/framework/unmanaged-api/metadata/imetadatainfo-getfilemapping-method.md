---
title: Método IMetaDataInfo::GetFileMapping
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 8823f3cc016072d3f20100c29532459da5e97492
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682382"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="b8a44-102">Método IMetaDataInfo::GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="b8a44-102">IMetaDataInfo::GetFileMapping Method</span></span>

<span data-ttu-id="b8a44-103">Obtém a região de memória do arquivo mapeado e o tipo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b8a44-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8a44-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8a44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8a44-105">Parameters</span></span>  

 `ppvData`  
 <span data-ttu-id="b8a44-106">fora Um ponteiro para o início do arquivo mapeado.</span><span class="sxs-lookup"><span data-stu-id="b8a44-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b8a44-107">fora O tamanho da região mapeada.</span><span class="sxs-lookup"><span data-stu-id="b8a44-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="b8a44-108">Se `pdwMappingType` for `fmFlat` , esse é o tamanho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="b8a44-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="b8a44-109">fora Um valor [CorFileMapping](corfilemapping-enumeration.md) que indica o tipo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b8a44-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="b8a44-110">A implementação atual do Common Language Runtime (CLR) sempre retorna `fmFlat` .</span><span class="sxs-lookup"><span data-stu-id="b8a44-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="b8a44-111">Outros valores são reservados para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="b8a44-111">Other values are reserved for future use.</span></span> <span data-ttu-id="b8a44-112">No entanto, você sempre deve verificar o valor retornado, pois outros valores podem ser habilitados em versões futuras ou versões de serviço.</span><span class="sxs-lookup"><span data-stu-id="b8a44-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8a44-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b8a44-113">Return Value</span></span>  
  
|<span data-ttu-id="b8a44-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8a44-114">HRESULT</span></span>|<span data-ttu-id="b8a44-115">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="b8a44-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b8a44-116">Todas as saídas são preenchidas.</span><span class="sxs-lookup"><span data-stu-id="b8a44-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b8a44-117">NULL foi passado como um valor de argumento.</span><span class="sxs-lookup"><span data-stu-id="b8a44-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="b8a44-118">A implementação do CLR não pode fornecer informações sobre a região da memória.</span><span class="sxs-lookup"><span data-stu-id="b8a44-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="b8a44-119">Isso pode ocorrer pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="b8a44-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="b8a44-120">-O escopo de metadados foi aberto com `ofWrite` o `ofCopyMemory` sinalizador ou.</span><span class="sxs-lookup"><span data-stu-id="b8a44-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="b8a44-121">-O escopo de metadados foi aberto sem o `ofReadOnly` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="b8a44-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="b8a44-122">-O método [IMetaDataDispenser:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) foi usado para abrir apenas a parte de metadados do arquivo.</span><span class="sxs-lookup"><span data-stu-id="b8a44-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="b8a44-123">-O arquivo não é um arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="b8a44-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="b8a44-124">**Observação:**  Essas condições dependem da implementação do CLR e provavelmente serão diminuídas em versões futuras do CLR.</span><span class="sxs-lookup"><span data-stu-id="b8a44-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8a44-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8a44-125">Remarks</span></span>  

 <span data-ttu-id="b8a44-126">A memória que `ppvData` aponta para é válida somente contanto que o escopo de metadados subjacente esteja aberto.</span><span class="sxs-lookup"><span data-stu-id="b8a44-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="b8a44-127">Para que esse método funcione, ao mapear os metadados de um arquivo em disco para a memória chamando o método [IMetaDataDispenser:: OpenScope](imetadatadispenser-openscope-method.md) , você deve especificar o `ofReadOnly` sinalizador e não deve especificar o `ofWrite` `ofCopyMemory` sinalizador ou.</span><span class="sxs-lookup"><span data-stu-id="b8a44-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="b8a44-128">A escolha do tipo de mapeamento de arquivo para cada escopo é específica para uma determinada implementação do CLR.</span><span class="sxs-lookup"><span data-stu-id="b8a44-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="b8a44-129">Ele não pode ser definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b8a44-129">It cannot be set by the user.</span></span> <span data-ttu-id="b8a44-130">A implementação atual do CLR sempre retorna `fmFlat` no `pdwMappingType` , mas isso pode ser alterado em versões futuras do CLR ou em futuras versões de serviço de determinada versão.</span><span class="sxs-lookup"><span data-stu-id="b8a44-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="b8a44-131">Você sempre deve verificar o valor retornado em `pdwMappingType` , pois tipos diferentes terão layouts e deslocamentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b8a44-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="b8a44-132">Não há suporte para a passagem de NULL para qualquer um dos três parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b8a44-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="b8a44-133">O método retorna `E_INVALIDARG` e nenhuma das saídas é preenchida.</span><span class="sxs-lookup"><span data-stu-id="b8a44-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="b8a44-134">Ignorar o tipo de mapeamento ou o tamanho da região pode resultar em um encerramento anormal do programa.</span><span class="sxs-lookup"><span data-stu-id="b8a44-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a44-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8a44-135">Requirements</span></span>  

 <span data-ttu-id="b8a44-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8a44-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a44-137">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8a44-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8a44-138">**Biblioteca:** Usado como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8a44-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8a44-139">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a44-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a44-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8a44-140">See also</span></span>

- [<span data-ttu-id="b8a44-141">Interface IMetaDataInfo</span><span class="sxs-lookup"><span data-stu-id="b8a44-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="b8a44-142">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="b8a44-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
