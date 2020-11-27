---
title: Especificando um ponto de entrada
description: Saiba como especificar um ponto de entrada, que identifica o local de uma função em uma DLL. Você pode renomear a função mapeando o ponto de entrada para outro nome.
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: d5c6b651b3b5f19eea8e61bc17da92158be87957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266357"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="71f12-104">Especificando um ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="71f12-104">Specifying an Entry Point</span></span>

<span data-ttu-id="71f12-105">Um ponto de entrada identifica o local de uma função em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="71f12-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="71f12-106">Em um projeto gerenciado, o nome original ou o ponto de entrada ordinal de uma função de destino identifica essa função no limite de interoperação.</span><span class="sxs-lookup"><span data-stu-id="71f12-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="71f12-107">Além disso, é possível mapear o ponto de entrada para um nome diferente, renomeando a função efetivamente.</span><span class="sxs-lookup"><span data-stu-id="71f12-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="71f12-108">Veja a seguir uma lista de possíveis motivos para renomear uma função de DLL:</span><span class="sxs-lookup"><span data-stu-id="71f12-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="71f12-109">Para evitar o uso de nomes de função de API que diferenciam maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="71f12-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="71f12-110">Para estar em conformidade com os padrões de nomenclatura existentes</span><span class="sxs-lookup"><span data-stu-id="71f12-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="71f12-111">Para acomodar funções que usam tipos de dados diferentes (declarando várias versões da mesma função de DLL)</span><span class="sxs-lookup"><span data-stu-id="71f12-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="71f12-112">Para simplificar o uso de APIs que contêm versões ANSI e Unicode</span><span class="sxs-lookup"><span data-stu-id="71f12-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="71f12-113">Este tópico demonstra como renomear uma função de DLL em um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="71f12-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="71f12-114">Renomeando uma função no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71f12-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="71f12-115">O Visual Basic usa a palavra-chave **Function** na instrução **Declare** para definir o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="71f12-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="71f12-116">O exemplo a seguir mostra uma declaração básica.</span><span class="sxs-lookup"><span data-stu-id="71f12-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="71f12-117">É possível substituir o ponto de entrada **MessageBox** por **MsgBox** incluindo a palavra-chave **Alias** na definição, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="71f12-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="71f12-118">Nos dois exemplos, a palavra-chave **Auto** elimina a necessidade de especificar a versão do conjunto de caracteres do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="71f12-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="71f12-119">Para obter mais informações sobre como selecionar um conjunto de caracteres, consulte [Especificando um conjunto de caracteres](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="71f12-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="71f12-120">Renomeando uma função no C# e C++</span><span class="sxs-lookup"><span data-stu-id="71f12-120">Renaming a Function in C# and C++</span></span>  

 <span data-ttu-id="71f12-121">É possível usar o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> para especificar uma função de DLL por nome ou ordinal.</span><span class="sxs-lookup"><span data-stu-id="71f12-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="71f12-122">Se o nome da função na definição de método for o mesmo do ponto de entrada na DLL, você não precisará identificar explicitamente a função com o campo **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="71f12-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="71f12-123">Caso contrário, use um dos seguintes formatos de atributo para indicar um nome ou um ordinal:</span><span class="sxs-lookup"><span data-stu-id="71f12-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="71f12-124">Observe que é necessário prefixar um ordinal com o sinal de cerquilha (#).</span><span class="sxs-lookup"><span data-stu-id="71f12-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="71f12-125">O exemplo a seguir demonstra como substituir **MessageBoxA** por **MsgBox** no código usando o campo **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="71f12-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="71f12-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="71f12-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="71f12-127">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="71f12-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="71f12-128">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="71f12-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="71f12-129">Marshaling de dados com invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="71f12-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
