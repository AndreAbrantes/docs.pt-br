---
title: Covariância e contravariância (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169864"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="a3d60-102">Covariância e contravariância (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="a3d60-103">No C#, a covariância e a contravariância habilitam a conversão de referência implícita para tipos de matriz, tipos de delegados e argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a3d60-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="a3d60-104">A covariância preserva a compatibilidade de atribuição, e a contravariância reverte.</span><span class="sxs-lookup"><span data-stu-id="a3d60-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="a3d60-105">O código a seguir demonstra a diferença entre a compatibilidade da atribuição, a covariância e a contravariância.</span><span class="sxs-lookup"><span data-stu-id="a3d60-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="a3d60-106">A covariância para matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo menos derivado.</span><span class="sxs-lookup"><span data-stu-id="a3d60-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="a3d60-107">Mas essa operação não é fortemente tipada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3d60-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="a3d60-108">O suporte de covariância e contravariância aos grupos de método permite a correspondência de assinaturas de método com tipos de delegados.</span><span class="sxs-lookup"><span data-stu-id="a3d60-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="a3d60-109">Isso permite atribuir a delegados não apenas os métodos que têm correspondência de assinaturas, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="a3d60-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="a3d60-110">Para obter mais informações, consulte [Variância em delegados (C#)](./variance-in-delegates.md) e [Usando variância em delegados (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a3d60-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="a3d60-111">O exemplo de código a seguir mostra o suporte da covariância e da contravariância para grupos de método.</span><span class="sxs-lookup"><span data-stu-id="a3d60-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="a3d60-112">No .NET Framework 4 ou mais recente, o C# dá suporte à covariância e á contravariância em interfaces e delegados genéricos e permite a conversão implícita de parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a3d60-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="a3d60-113">Para obter mais informações, consulte [Variação em interfaces genéricas (C#)](./variance-in-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a3d60-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="a3d60-114">O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="a3d60-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="a3d60-115">Uma interface ou delegado genérico será chamado *variante* se seus parâmetros genéricos forem declarados covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="a3d60-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="a3d60-116">O C# permite que você crie suas próprias interfaces variantes e delegados.</span><span class="sxs-lookup"><span data-stu-id="a3d60-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="a3d60-117">Para obter mais informações, consulte [Criando interfaces genéricas variantes (C#)](./creating-variant-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a3d60-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="a3d60-118">Tópicos Relacionados</span><span class="sxs-lookup"><span data-stu-id="a3d60-118">Related Topics</span></span>  
  
|<span data-ttu-id="a3d60-119">Title</span><span class="sxs-lookup"><span data-stu-id="a3d60-119">Title</span></span>|<span data-ttu-id="a3d60-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d60-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a3d60-121">Variância em interfaces genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="a3d60-122">Discute a covariância e a contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3d60-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="a3d60-123">Criando interfaces genéricas variáveis (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="a3d60-124">Mostra como criar interfaces variantes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a3d60-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="a3d60-125">Usando variação em interfaces para Coleções Genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="a3d60-126">Mostra como o suporte de covariância e contravariância nas interfaces <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601> pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="a3d60-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="a3d60-127">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="a3d60-128">Discute a covariância e a contravariância em interfaces genéricas e não genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3d60-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="a3d60-129">Usando variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="a3d60-130">Mostra como usar o suporte de covariância e contravariância em delegados não genéricos para corresponder às assinaturas de método com tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="a3d60-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="a3d60-131">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="a3d60-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="a3d60-132">Mostra como o suporte de covariância e contravariância nos delegados `Func` e `Action` pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="a3d60-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
