---
title: Interface IMetaDataConverter
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 74804cdc9dc04c3ede5cc26a6310dbb3948cd78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729480"
---
# <a name="imetadataconverter-interface"></a>Interface IMetaDataConverter

Fornece métodos para mapear bibliotecas de tipos para suas assinaturas de metadados e para converter de uma para a outra.  
  
## <a name="methods"></a>Métodos  
  
|Método|DESCRIÇÃO|  
|------------|-----------------|  
|[Método GetMetaDataFromTypeInfo](imetadataconverter-getmetadatafromtypeinfo-method.md)|Obtém um ponteiro para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados para a biblioteca de tipos referenciada pela `ITypeInfo` instância especificada.|  
|[Método GetMetaDataFromTypeLib](imetadataconverter-getmetadatafromtypelib-method.md)|Obtém um ponteiro para uma `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pela `ITypeLib` instância especificada.|  
|[Método GetTypeLibFromMetaData](imetadataconverter-gettypelibfrommetadata-method.md)|Obtém um ponteiro para uma `ITypeLib` instância que representa a biblioteca de tipos que tem o módulo e os nomes de biblioteca especificados.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso no MsCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interfaces de metadados](metadata-interfaces.md)
- [Interface IMetaDataImport](imetadataimport-interface.md)
