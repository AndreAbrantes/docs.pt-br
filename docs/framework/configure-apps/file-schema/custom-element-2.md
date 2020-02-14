---
title: Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215491"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler

Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp; **\<sectionname >**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | DESCRIÇÃO |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | DESCRIÇÃO |
| --- | ----------- |
| [ **\<adicionar >** ](add-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>  | Adiciona configurações de aplicativo personalizadas. |
| [ **\<remover >** ](remove-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> | Remove uma configuração definida anteriormente. |
| [ **\<limpar >** ](clear-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> | Limpa todas as configurações definidas anteriormente em uma seção. |

## <a name="remarks"></a>Comentários

O elemento **\<sectionname >** é um elemento personalizado definido por uma **seção\<>** marca no elemento **\<configSections >** .

A tabela a seguir mostra o tipo de objeto que o método ConfigurationSettings. GetConfig retorna para cada manipulador de seção de configuração:

| Manipulador da seção de configuração                        | Tipo de retorno                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como declarar seções que usam as classes <xref:System.Configuration.DictionarySectionHandler> e <xref:System.Configuration.NameValueSectionHandler>.

O primeiro elemento personalizado é **\<dictionarySample >** , que contém as configurações lidas pela classe <xref:System.Configuration.DictionarySectionHandler> no assembly `System.dll`. O segundo elemento personalizado é **\<> myseção**, que contém as configurações lidas pela classe <xref:System.Configuration.NameValueSectionHandler> no assembly `System.dll`.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
