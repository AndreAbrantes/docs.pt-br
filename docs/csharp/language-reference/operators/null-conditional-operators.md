---
title: Operadores condicionais nulos (C# e Visual Basic) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 61a093677354ba3a960fb5714963a1205d24ed06
ms.openlocfilehash: 876b7c99ca9249e0a2b9cbd036c38e368228ac9f
ms.contentlocale: pt-br
ms.lasthandoff: 03/25/2017

---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Operadores condicionais nulos (C# e Visual Basic)
Usado para testar a presença de nulos antes de executar uma operação de acesso de membro (`?.`) ou de índice (`?[`).  Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 O último exemplo demonstra que os operadores condicionais nulos estão em curto-circuito.  Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.  Outras operações com menor precedência na expressão continuarão.  Por exemplo, `E` a seguir sempre é executado e as operações `??` e `==` são executadas.  
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.  A maneira antiga requer código semelhante ao seguinte:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 A nova maneira é muito mais simples:  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.  
  
 Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.  Havia muitas situações de análise ambíguas para permitir isso.  
  
## <a name="language-specifications"></a>Especificações da linguagem  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Para obter mais informações, consulte [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [?? (operador de união nula)](null-conditional-operator.md)   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)

