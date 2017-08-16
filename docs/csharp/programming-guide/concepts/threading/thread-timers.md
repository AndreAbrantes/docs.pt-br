---
title: Temporizadores de thread (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f91fde1340772c62f7779a2503bfb79aba7c3fb
ms.lasthandoff: 03/13/2017

---
# <a name="thread-timers-c"></a>Temporizadores de thread (C#)
A classe <xref:System.Threading.Timer?displayProperty=fullName> é útil para executar periodicamente uma tarefa em um thread separado. Por exemplo, você pode usar um temporizador de thread para verificar o status e a integridade de um banco de dados ou para fazer backup de arquivos críticos.  
  
## <a name="thread-timer-example"></a>Exemplo de temporizador de thread  
 O exemplo a seguir inicia uma tarefa a cada dois segundos e usa um sinalizador para iniciar o método <xref:System.IDisposable.Dispose%2A> que interrompe o temporizador. Este exemplo posta o status na janela de saída.  
  
```csharp  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 Temporizadores de thread são particularmente úteis quando o objeto <xref:System.Windows.Forms.Timer?displayProperty=fullName> está indisponível, como quando você está desenvolvendo aplicativos de console.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading>   
 [Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)
