---
title: 'Método IXCLRDataProcess:: GetRuntimeNameByAddress'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270478"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>Método IXCLRDataProcess:: GetRuntimeNameByAddress

Obtém um nome para o endereço fornecido.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a>Parâmetros

`address`\
no Um `CLRDATA_ADDRESS` valor que representa um endereço de código.

`flags`\
no Definido como ' 0 '.

`bufLen`\
no O comprimento do buffer.

`namLen`\
fora Um ponteiro para o número de caracteres retornados.

`namBuf`\
[out, size_is ( `bufLen` )] o buffer de entrada de comprimento `bufLen` que armazena o nome do tempo de execução.

`displacement`\
fora Um `CLRDATA_ADDRESS` ponteiro para o deslocamento de código do símbolo retornado.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao 16º slot da tabela de métodos virtuais.

> [!NOTE]
> Se o buffer não for grande o suficiente para o nome, esse método retornará `S_FALSE` e definirá `nameLen` como o tamanho de buffer necessário.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [os requisitos do sistema](../../get-started/system-requirements.md)\
**Cabeçalho:** None
**Biblioteca:** None
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
