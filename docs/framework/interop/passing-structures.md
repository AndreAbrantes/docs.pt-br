---
title: Passando estruturas
description: Entenda como passar estruturas e classes para funções não gerenciadas. Saiba mais sobre o atributo StructLayoutAttribute, que você usa para definir tipos formatados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: ece5db8fdf803ce2f450ebeaaad66a379cfbf992
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268905"
---
# <a name="passing-structures"></a><span data-ttu-id="a4ea3-104">Passando estruturas</span><span class="sxs-lookup"><span data-stu-id="a4ea3-104">Passing Structures</span></span>

<span data-ttu-id="a4ea3-105">Muitas funções não gerenciadas esperam que você passe, como um parâmetro para a função, membros de estruturas (tipos definidos pelo usuário no Visual Basic) ou membros de classes que são definidas em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="a4ea3-106">Ao passar estruturas ou classes para código não gerenciado usando invocação de plataforma, você deve fornecer informações adicionais para preservar o layout original e o alinhamento.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="a4ea3-107">Este tópico apresenta o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>, que você usa para definir tipos formatados.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="a4ea3-108">Para classes e estruturas gerenciadas, você pode selecionar vários comportamentos de layout previsível fornecidos pela enumeração **LayoutKind**.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="a4ea3-109">Há uma diferença importante entre tipos de estrutura e classe que e central para os conceitos apresentados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="a4ea3-110">Estruturas são tipos de valor e classes são tipos de referência – classes sempre fornecem pelo menos um nível de indireção de memória (um ponteiro para um valor).</span><span class="sxs-lookup"><span data-stu-id="a4ea3-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="a4ea3-111">Essa diferença é importante porque funções não gerenciadas geralmente exigem indireção, conforme mostrado pelas assinaturas na primeira coluna da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="a4ea3-112">A estrutura gerenciada e as declarações de classe nas colunas restantes mostram o grau em que você pode ajustar o nível de indireção na sua declaração. Declarações são fornecidas para o Visual Basic e Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="a4ea3-113">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="a4ea3-113">Unmanaged signature</span></span>|<span data-ttu-id="a4ea3-114">Declaração gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-114">Managed declaration:</span></span> <br /><span data-ttu-id="a4ea3-115">sem indireção</span><span class="sxs-lookup"><span data-stu-id="a4ea3-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="a4ea3-116">Declaração gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-116">Managed declaration:</span></span> <br /><span data-ttu-id="a4ea3-117">um nível de indireção</span><span class="sxs-lookup"><span data-stu-id="a4ea3-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="a4ea3-118">Demanda zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a4ea3-119">Adiciona zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="a4ea3-120">Não é possível porque já existe um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="a4ea3-121">Demanda um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a4ea3-122">Adiciona um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a4ea3-123">Adiciona zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="a4ea3-124">Demanda dois níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="a4ea3-125">Não é possível porque **ByRef** **ByRef** ou `ref` `ref` não pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a4ea3-126">Adiciona um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="a4ea3-127">A tabela descreve as diretrizes a seguir para declarações de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="a4ea3-128">Use uma estrutura passada por valor quando a função não gerenciada não demanda nenhuma indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="a4ea3-129">Use uma estrutura passada por referência ou uma classe passada por valor quando a função não gerenciada demanda um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="a4ea3-130">Use uma classe passada por referência quando a função não gerenciada demanda dois níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="a4ea3-131">Declarando e passando estruturas</span><span class="sxs-lookup"><span data-stu-id="a4ea3-131">Declaring and Passing Structures</span></span>  

 <span data-ttu-id="a4ea3-132">O exemplo a seguir mostra como definir as estruturas `Point` e `Rect` em código gerenciado e passar tipos como parâmetro para a função **PtInRect** no arquivo User32.dll.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="a4ea3-133">**PtInRect** tem a seguinte assinatura não gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="a4ea3-134">Observe que você deve passar a estrutura Rect por referência, pois a função espera um ponteiro para um tipo RECT.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="a4ea3-135">Declarando e passando classes</span><span class="sxs-lookup"><span data-stu-id="a4ea3-135">Declaring and Passing Classes</span></span>  

 <span data-ttu-id="a4ea3-136">Você pode passar membros de uma classe para uma função de DLL não gerenciada, desde que a classe tenha um layout de membro fixo.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="a4ea3-137">O exemplo a seguir demonstra como passar membros da classe `MySystemTime`, que são definidos em ordem sequencial, para o **GetSystemTime** no arquivo User32.dll.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="a4ea3-138">**GetSystemTime** tem a seguinte assinatura não gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="a4ea3-139">Diferentemente dos tipos de valor, classes sempre têm pelo menos um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4ea3-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="a4ea3-140">See also</span></span>

- [<span data-ttu-id="a4ea3-141">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="a4ea3-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
