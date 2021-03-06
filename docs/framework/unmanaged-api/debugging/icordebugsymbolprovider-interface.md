---
title: Interface ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: ff1f39be3d3db43f70cfa4a0711a3f42c180bc1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672078"
---
# <a name="icordebugsymbolprovider-interface"></a>Interface ICorDebugSymbolProvider

Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|DESCRIÇÃO|  
|------------|-----------------|  
|[Método GetAssemblyImageBytes](icordebugsymbolprovider-getassemblyimagebytes-method.md)|Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.|  
|[Método GetAssemblyImageMetadata](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Retorna os metadados de um assembly mesclado.|  
|[Método GetCodeRange](icordebugsymbolprovider-getcoderange-method.md)|Obtém o endereço inicial e o tamanho do método de acordo com um endereço virtual relativo (RVA) em um método.|  
|[Método GetInstanceFieldSymbols](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Obtém os símbolos de campo de instância que correspondem a uma assinatura de TypeSpec.|  
|[Método GetMergedAssemblyRecords](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Obtém os registros de símbolo de todos os assemblies mesclados.|  
|[Método GetMethodLocalSymbols](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.|  
|[Método GetMethodParameterSymbols](icordebugsymbolprovider-getmethodparametersymbols-method.md)|Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.|  
|[Método GetMethodProps](icordebugsymbolprovider-getmethodprops-method.md)|Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.|  
|[Método GetObjectSize](icordebugsymbolprovider-getobjectsize-method.md)|Retorna o tamanho do objeto de um objeto com base em sua assinatura de TypeSpec.|  
|[Método GetStaticFieldSymbols](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Obtém os símbolos de campo estático que correspondem a uma assinatura de TypeSpec.|  
|[Método GetTypeProps](icordebugsymbolprovider-gettypeprops-method.md)|Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
