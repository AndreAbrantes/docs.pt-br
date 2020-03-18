---
title: Como analisar cadeias de caracteres no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084311"
---
# <a name="parsing-strings-in-net"></a>Como analisar cadeias de caracteres no .NET
Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base. Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora. O método usado com mais frequência para executar uma operação de análise é o método `Parse`. Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam. Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres. Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Parsing Numeric Strings](../../../docs/standard/base-types/parsing-numeric.md)  
 Descreve como converter cadeias de caracteres em tipos numéricos do .NET.  
  
 [Analisando cadeias de caracteres de data e hora](../../../docs/standard/base-types/parsing-datetime.md)  
 Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.  
  
 [Analisando outras cadeias de caracteres](../../../docs/standard/base-types/parsing-other.md)  
 Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Formatar tipos](../../../docs/standard/base-types/formatting-types.md)  
 Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.  
  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)  
 Descreve como converter tipos.  
  
 [Tipos base](../../../docs/standard/base-types/index.md)  
 Descreve as operações comuns que você pode executar em tipos de base do .NET.
