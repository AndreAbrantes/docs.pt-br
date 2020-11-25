---
title: Enumeração CorSymSearchPolicyAttributes
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 2d5d19fb3fb7c727227827dacbaac2c910ac8b3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725216"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="1646f-102">Enumeração CorSymSearchPolicyAttributes</span><span class="sxs-lookup"><span data-stu-id="1646f-102">CorSymSearchPolicyAttributes Enumeration</span></span>

<span data-ttu-id="1646f-103">Especifica a política a ser usada ao fazer uma pesquisa por um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="1646f-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="1646f-104">Essas constantes são usadas pelos métodos [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3:: GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1646f-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1646f-105">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="1646f-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1646f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1646f-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="1646f-107">Membros</span><span class="sxs-lookup"><span data-stu-id="1646f-107">Members</span></span>  
  
|<span data-ttu-id="1646f-108">Membro</span><span class="sxs-lookup"><span data-stu-id="1646f-108">Member</span></span>|<span data-ttu-id="1646f-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="1646f-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="1646f-110">Consulta o registro em busca de caminhos de pesquisa de símbolo.</span><span class="sxs-lookup"><span data-stu-id="1646f-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="1646f-111">Acessa um servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="1646f-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="1646f-112">Pesquisa o caminho especificado no diretório de depuração.</span><span class="sxs-lookup"><span data-stu-id="1646f-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="1646f-113">Procura o PDB no local onde está o arquivo. exe.</span><span class="sxs-lookup"><span data-stu-id="1646f-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1646f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1646f-114">Requirements</span></span>  

 <span data-ttu-id="1646f-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1646f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1646f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1646f-116">See also</span></span>

- [<span data-ttu-id="1646f-117">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1646f-117">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
