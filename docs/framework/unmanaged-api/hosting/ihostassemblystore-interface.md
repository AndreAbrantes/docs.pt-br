---
title: Interface IHostAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: 4b2fed963d2d0ebec54e5f7a4d95cba26c1bac1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680931"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="6a02a-102">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="6a02a-102">IHostAssemblyStore Interface</span></span>

<span data-ttu-id="6a02a-103">Fornece métodos que permitem que um host carregue assemblies e módulos independentemente do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6a02a-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a02a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6a02a-104">Methods</span></span>  
  
|<span data-ttu-id="6a02a-105">Método</span><span class="sxs-lookup"><span data-stu-id="6a02a-105">Method</span></span>|<span data-ttu-id="6a02a-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6a02a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a02a-107">Método ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="6a02a-107">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="6a02a-108">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) retornado de uma chamada para [IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a02a-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="6a02a-109">Método ProvideModule</span><span class="sxs-lookup"><span data-stu-id="6a02a-109">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="6a02a-110">Resolve um módulo dentro de um assembly ou um arquivo de recurso vinculado (não incorporado).</span><span class="sxs-lookup"><span data-stu-id="6a02a-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a02a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a02a-111">Remarks</span></span>  

 <span data-ttu-id="6a02a-112">`IHostAssemblyStore` fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="6a02a-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="6a02a-113">O host carrega assemblies retornando `IStream` instâncias que apontam diretamente nos bytes.</span><span class="sxs-lookup"><span data-stu-id="6a02a-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="6a02a-114">O CLR determina se um host foi implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização.</span><span class="sxs-lookup"><span data-stu-id="6a02a-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="6a02a-115">Isso permite que o host, por exemplo, controle a associação a assemblies de usuário, mas dependa do tempo de execução para associar a assemblies de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a02a-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a02a-116">No fornecimento de uma implementação do `IHostAssemblyStore` , o host especifica sua intenção de resolver todos os assemblies que não são referenciados pelo `ICLRAssemblyReferenceList` retornado de `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="6a02a-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a02a-117">A versão 2,0 do .NET Framework não fornece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo utilitário do [gerador de imagem nativa (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="6a02a-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a02a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a02a-118">Requirements</span></span>  

 <span data-ttu-id="6a02a-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a02a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a02a-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a02a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a02a-121">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a02a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a02a-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a02a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a02a-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="6a02a-123">See also</span></span>

- [<span data-ttu-id="6a02a-124">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6a02a-124">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6a02a-125">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="6a02a-125">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="6a02a-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6a02a-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
