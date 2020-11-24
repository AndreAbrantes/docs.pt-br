---
title: Enumeração CorNativeType
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: 95bbb0cc2f223cfa96e1314ed28f46016c81a2fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687691"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="d64fb-102">Enumeração CorNativeType</span><span class="sxs-lookup"><span data-stu-id="d64fb-102">CorNativeType Enumeration</span></span>

<span data-ttu-id="d64fb-103">Contém valores que descrevem os tipos nativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="d64fb-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d64fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d64fb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="d64fb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d64fb-105">Members</span></span>  
  
|<span data-ttu-id="d64fb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d64fb-106">Member</span></span>|<span data-ttu-id="d64fb-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="d64fb-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="d64fb-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="d64fb-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="d64fb-110">Um valor booliano de 4 bytes, em que TRUE é diferente de zero e FALSE é zero.</span><span class="sxs-lookup"><span data-stu-id="d64fb-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="d64fb-111">Um valor inteiro de 8 bits assinado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="d64fb-112">Um valor inteiro de 8 bits não assinado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="d64fb-113">Um valor inteiro de 16 bits assinado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="d64fb-114">Um valor inteiro sem sinal de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="d64fb-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="d64fb-115">Um valor inteiro de 32 bits com sinal.</span><span class="sxs-lookup"><span data-stu-id="d64fb-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="d64fb-116">Um valor inteiro de 32 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="d64fb-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="d64fb-117">Um valor inteiro de 64 bits assinado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="d64fb-118">Um valor inteiro de 64 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="d64fb-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="d64fb-119">Um valor numérico de ponto flutuante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="d64fb-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="d64fb-120">Um valor numérico de ponto flutuante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="d64fb-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="d64fb-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="d64fb-122">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="d64fb-123">Um tipo COM numérico que corresponde ao tipo gerenciado <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="d64fb-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="d64fb-124">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="d64fb-125">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="d64fb-126">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="d64fb-127">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="d64fb-128">Um valor de cadeia de caracteres LPSTR.</span><span class="sxs-lookup"><span data-stu-id="d64fb-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="d64fb-129">Um valor de cadeia de caracteres LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="d64fb-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="d64fb-130">Um valor de cadeia de caracteres do LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="d64fb-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="d64fb-131">Um valor de cadeia de caracteres fixo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="d64fb-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="d64fb-132">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="d64fb-133">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="d64fb-134">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="d64fb-135">Um valor de estrutura nativa.</span><span class="sxs-lookup"><span data-stu-id="d64fb-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="d64fb-136">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="d64fb-137">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="d64fb-138">Um valor de matriz de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="d64fb-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="d64fb-139">Um valor inteiro de 16 bits com sinal nativo.</span><span class="sxs-lookup"><span data-stu-id="d64fb-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="d64fb-140">Um valor inteiro nativo de 16 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="d64fb-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="d64fb-141">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d64fb-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="d64fb-142">Use NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="d64fb-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="d64fb-143">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="d64fb-144">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="d64fb-145">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="d64fb-146">Selecione BSTR ou ANSIBSTR dependendo da plataforma.</span><span class="sxs-lookup"><span data-stu-id="d64fb-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="d64fb-147">Um valor booliano de 2 bytes, em que TRUE é-1 e FALSE é zero.</span><span class="sxs-lookup"><span data-stu-id="d64fb-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="d64fb-148">Um ponteiro de função.</span><span class="sxs-lookup"><span data-stu-id="d64fb-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="d64fb-149">Uma referência a qualquer tipo nativo.</span><span class="sxs-lookup"><span data-stu-id="d64fb-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="d64fb-150">Uma referência a uma matriz com membros de um tipo não especificado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="d64fb-151">Um ponteiro de inteiro de 32 bits para uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="d64fb-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="d64fb-152">Um tipo nativo do marshaler personalizado.</span><span class="sxs-lookup"><span data-stu-id="d64fb-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="d64fb-153">Isso deve ser seguido por uma cadeia de caracteres do seguinte formato: "nome do tipo nativo/0Custom do tipo de marshaler nome/0Optional cookie/0" ou "{GUID do tipo nativo}/0Custom nome do tipo do marshaler/0Optional cookie/0"</span><span class="sxs-lookup"><span data-stu-id="d64fb-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="d64fb-154">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="d64fb-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="d64fb-155">Com ELEMENT_TYPE_I4 esse tipo é mapeado para VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d64fb-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="d64fb-156">Um `IInspectable` tipo nativo.</span><span class="sxs-lookup"><span data-stu-id="d64fb-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="d64fb-157">Um nativo `HString` .</span><span class="sxs-lookup"><span data-stu-id="d64fb-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="d64fb-158">Um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="d64fb-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d64fb-159">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d64fb-159">Requirements</span></span>  

 <span data-ttu-id="d64fb-160">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d64fb-160">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d64fb-161">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d64fb-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d64fb-162">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d64fb-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64fb-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="d64fb-163">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="d64fb-164">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d64fb-164">Metadata Enumerations</span></span>](metadata-enumerations.md)
