---
title: Método IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 3c59114f78af1aa8705318af093e47d4f03a82ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699138"
---
# <a name="ivalidatorvalidate-method"></a>Método IValidator::Validate

Valida o executável portátil (PE) ou o arquivo. MSIL (Microsoft Intermediate Language) especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `veh`  
 no Um ponteiro para uma `IVEHandler` instância que manipula erros de validação.  
  
 `pAppDomain`  
 no Um ponteiro para o domínio do aplicativo no qual o arquivo é carregado.  
  
 `ulFlags`  
 no Uma combinação de bits de valor [ValidatorFlags](validatorflags-enumeration.md) , que indica as validações que devem ser executadas.  
  
 `ulMaxError`  
 no O número máximo de erros a serem permitidos antes de sair da validação.  
  
 `token`  
 no Não usado.  
  
 `fileName`  
 no Uma cadeia de caracteres que especifica o nome do arquivo a ser validado.  
  
 `pe`  
 no Um ponteiro para o buffer de memória no qual o arquivo está armazenado.  
  
 `ulSize`  
 no O tamanho, em bytes, do arquivo a ser validado.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator. idl, IValidator. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
