---
title: Temporizadores de thread (C#)
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 30037b5b6d798796e7f76fa045f882b7f335e0d7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="thread-timers-c"></a><span data-ttu-id="7efeb-102">Temporizadores de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="7efeb-102">Thread Timers (C#)</span></span>
<span data-ttu-id="7efeb-103">A classe <xref:System.Threading.Timer?displayProperty=fullName> é útil para executar periodicamente uma tarefa em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="7efeb-103">The <xref:System.Threading.Timer?displayProperty=fullName> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="7efeb-104">Por exemplo, você pode usar um temporizador de thread para verificar o status e a integridade de um banco de dados ou para fazer backup de arquivos críticos.</span><span class="sxs-lookup"><span data-stu-id="7efeb-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="7efeb-105">Exemplo de temporizador de thread</span><span class="sxs-lookup"><span data-stu-id="7efeb-105">Thread Timer Example</span></span>  
 <span data-ttu-id="7efeb-106">O exemplo a seguir inicia uma tarefa a cada dois segundos e usa um sinalizador para iniciar o método <xref:System.IDisposable.Dispose%2A> que interrompe o temporizador.</span><span class="sxs-lookup"><span data-stu-id="7efeb-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="7efeb-107">Este exemplo posta o status na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="7efeb-107">This example posts status to the output window.</span></span>  
  
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
  
 <span data-ttu-id="7efeb-108">Temporizadores de thread são particularmente úteis quando o objeto <xref:System.Windows.Forms.Timer?displayProperty=fullName> não está disponível, assim como quando você está desenvolvendo aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="7efeb-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=fullName> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efeb-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7efeb-109">See Also</span></span>  
 <span data-ttu-id="7efeb-110"><xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="7efeb-110"><xref:System.Threading></span></span>   
 [<span data-ttu-id="7efeb-111">Aplicativos com multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="7efeb-111">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)

