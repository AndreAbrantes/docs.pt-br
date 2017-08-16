---
title: "Padrões assíncronos de programação | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a8a89b8987eaff4d94f5e620c45b551b7be682d8
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="asynchronous-programming-patterns"></a>Padrões de programação assíncrona
O .NET Framework fornece três padrões para executar operações assíncronas:  
  
-   Padrão do Modelo de Programação Assíncrono (APM) (também chamado de padrão <xref:System.IAsyncResult>), em que operações assíncronas requerem os métodos `Begin` e `End` (por exemplo, `BeginWrite` e `EndWrite` para operações de gravação assíncronas). Esse padrão não é mais recomendado para implantação nova. Para saber mais, veja [APM (Modelo Assíncrono de Programação)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
-   Padrão Assíncrono (EAP) baseado em eventos, que requer um método que tenha o sufixo `Async` e também requer um ou mais eventos, tipos de delegado do manipulador de eventos e tipos derivados de `EventArg`. O EAP foi introduzido no .NET Framework 2.0. Ele não é mais recomendável para implantação nova. Para saber mais, confira [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
-   Padrão Assíncrono baseado em tarefa (TAP), que usa um único método para representar o início e a conclusão de uma operação assíncrona. O TAP foi introduzido no .NET Framework 4 e é a abordagem recomendada para programação assíncrona no .NET Framework. As palavras-chave [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) no #C e os operadores [Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) no Visual Basic Language adicionam suporte à linguagem para TAP. Para saber mais, confira [Padrão assíncrono baseado em tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Comparando padrões  
 Para obter uma comparação rápida de como os três padrões modelam as operações assíncronas, considere um método `Read` que lê uma quantidade especificada de dados em um buffer fornecido começando em um deslocamento especificado:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
 O equivalente do APM desse método poderia expor os métodos `BeginRead` e `EndRead`:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
 O equivalente do EAP poderia expor o seguinte conjunto de tipos e membros:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
 O equivalente do TAP poderia expor o único método `ReadAsync` a seguir:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
 Para obter uma discussão abrangente de TAP, APM e EAP, consulte os links fornecidos na próxima seção.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[APM (Modelo Assíncrono de Programação)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)|Descreve o modelo herdado que usa a interface <xref:System.IAsyncResult> para fornecer comportamento assíncrono. Esse modelo não é mais recomendado para implantação nova.|  
|[EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)|Descreve o modelo herdado baseado em eventos para fornecer comportamento assíncrono. Esse modelo não é mais recomendado para implantação nova.|  
|[TAP (Padrão Assíncrono Baseado em Tarefa)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Descreve o novo padrão assíncrono baseado no namespace <xref:System.Threading.Tasks>. Esse modelo é a abordagem recomendada para programação assíncrona no .NET Framework 4 e versões posteriores.|
