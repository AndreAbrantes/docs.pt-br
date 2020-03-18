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
# <a name="covariance-and-contravariance-c"></a>Covariância e contravariância (C#)
No C#, a covariância e a contravariância habilitam a conversão de referência implícita para tipos de matriz, tipos de delegados e argumentos de tipo genérico. A covariância preserva a compatibilidade de atribuição, e a contravariância reverte.  
  
 O código a seguir demonstra a diferença entre a compatibilidade da atribuição, a covariância e a contravariância.  
  
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
  
 A covariância para matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo menos derivado. Mas essa operação não é fortemente tipada, conforme mostrado no exemplo de código a seguir.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 O suporte de covariância e contravariância aos grupos de método permite a correspondência de assinaturas de método com tipos de delegados. Isso permite atribuir a delegados não apenas os métodos que têm correspondência de assinaturas, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo delegado. Para obter mais informações, consulte [Variância em delegados (C#)](./variance-in-delegates.md) e [Usando variância em delegados (C#)](./using-variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra o suporte da covariância e da contravariância para grupos de método.  
  
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
  
 No .NET Framework 4 ou mais recente, o C# dá suporte à covariância e á contravariância em interfaces e delegados genéricos e permite a conversão implícita de parâmetros de tipo genérico. Para obter mais informações, consulte [Variação em interfaces genéricas (C#)](./variance-in-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Uma interface ou delegado genérico será chamado *variante* se seus parâmetros genéricos forem declarados covariantes ou contravariantes. O C# permite que você crie suas próprias interfaces variantes e delegados. Para obter mais informações, consulte [Criando interfaces genéricas variantes (C#)](./creating-variant-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tópicos Relacionados  
  
|Title|Descrição|  
|-----------|-----------------|  
|[Variância em interfaces genéricas (C#)](./variance-in-generic-interfaces.md)|Discute a covariância e a contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.|  
|[Criando interfaces genéricas variáveis (C#)](./creating-variant-generic-interfaces.md)|Mostra como criar interfaces variantes personalizadas.|  
|[Usando variação em interfaces para Coleções Genéricas (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Mostra como o suporte de covariância e contravariância nas interfaces <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601> pode ajudar na reutilização do código.|  
|[Variação em delegados (C#)](./variance-in-delegates.md)|Discute a covariância e a contravariância em interfaces genéricas e não genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.|  
|[Usando variação em delegados (C#)](./using-variance-in-delegates.md)|Mostra como usar o suporte de covariância e contravariância em delegados não genéricos para corresponder às assinaturas de método com tipos delegados.|  
|[Usando variação para delegados genéricos Func e Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Mostra como o suporte de covariância e contravariância nos delegados `Func` e `Action` pode ajudar na reutilização do código.|
