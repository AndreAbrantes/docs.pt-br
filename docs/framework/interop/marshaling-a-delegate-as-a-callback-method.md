---
title: Realizando marshaling de um delegado como um método de retorno de chamada
description: Aprenda a realizar marshaling de um delegado como um método de retorno de chamada. Veja um exemplo de como passar delegados para uma função não gerenciada que é esperada ponteiros de função.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: bf9ef3b9d48c0869dcc96820c3a2fb6fb608479e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618942"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="3ceab-104">Realizando marshaling de um delegado como um método de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="3ceab-104">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="3ceab-105">Este exemplo demonstra como passar delegados para uma função não gerenciada esperando ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="3ceab-105">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="3ceab-106">Um delegado é uma classe que pode conter uma referência a um método e é equivalente a um ponteiro de função fortemente tipada ou a uma função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3ceab-106">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="3ceab-107">Quando você usa um delegado dentro de uma chamada, o Common Language Runtime protege o delegado de sofrer coleta de lixo pela duração da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ceab-107">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="3ceab-108">No entanto, se a função não gerenciada armazena o delegado para uso após a conclusão da chamada, você deve evitar manualmente a coleta de lixo até que a função não gerenciada termine de usar o delegado.</span><span class="sxs-lookup"><span data-stu-id="3ceab-108">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="3ceab-109">Para obter mais informações, consulte a [Amostra de HandleRef](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) e [Amostra de GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ceab-109">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="3ceab-110">A amostra de Callback usa as seguintes funções não gerenciadas, mostradas com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="3ceab-110">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="3ceab-111">`TestCallBack` exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="3ceab-111">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="3ceab-112">`TestCallBack2` exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="3ceab-112">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="3ceab-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) é uma biblioteca personalizada não gerenciada que contém uma implementação para as funções listadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ceab-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="3ceab-114">Neste exemplo, a classe `NativeMethods` contém protótipos gerenciados para os métodos `TestCallBack` e `TestCallBack2`.</span><span class="sxs-lookup"><span data-stu-id="3ceab-114">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="3ceab-115">Ambos os métodos passam um delegado para uma função de retorno de chamada como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3ceab-115">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="3ceab-116">A assinatura do delegado deve corresponder à assinatura do método ao qual ele faz referência.</span><span class="sxs-lookup"><span data-stu-id="3ceab-116">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="3ceab-117">Por exemplo, os delegados `FPtr` e `FPtr2` têm assinaturas que são idênticas aos métodos `DoSomething` e `DoSomething2`.</span><span class="sxs-lookup"><span data-stu-id="3ceab-117">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="3ceab-118">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="3ceab-118">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="3ceab-119">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="3ceab-119">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="3ceab-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ceab-120">See also</span></span>

- <span data-ttu-id="3ceab-121">[Exemplos diversos de marshaling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ceab-121">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="3ceab-122">Tipos de dados de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="3ceab-122">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="3ceab-123">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="3ceab-123">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
