---
title: Analisando cadeias de caracteres no .NET
description: Analisando cadeias de caracteres no .NET
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.lasthandoff: 03/03/2017

---

# <a name="parsing-strings-in-net"></a>Analisando cadeias de caracteres no .NET

Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base. Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora. O método usado com mais frequência para executar uma operação de análise é o método `Parse`. Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam. Assim como a formatação usa um objeto que implementa a interface [IFormatProvider](xref:System.IFormatProvider) para fornecer informações de formatação sensíveis à cultura, a análise também usa um objeto que implementa a interface [IFormatProvider](xref:System.IFormatProvider) para determinar como interpretar uma representação de cadeia de caracteres. Para obter mais informações, consulte [Tipos de formatação no .NET](formatting-types.md).

## <a name="in-this-section"></a>Nesta seção

[Analisando cadeias de caracteres numéricas no .NET](parsing-numeric.md) – Descreve como converter cadeias de caracteres em tipos numéricos no .NET.

[Analisando cadeias de caracteres de data e hora no .NET](parsing-datetime.md) – Descreve como converter cadeias de caracteres em tipos`DateTime` no .NET.

[Analisando outras cadeias de caracteres no .NET](parsing-other.md) – Descreve como converter cadeias de caracteres em tipos [Char](xref:System.Char), [Boolean](xref:System.Boolean) e [Enum](xref:System.Enum).

[Tipos de formatação no .NET](formatting-types.md) – Descreve os conceitos básicos de formatação, como especificadores de formato e provedores de formato.

[Conversão de tipo no .NET](type-conversion.md) – Descreve como converter tipos.

[Trabalhando com tipos base no .NET](index.md) – Descreve operações comuns que você pode executar em tipos base do .NET.


