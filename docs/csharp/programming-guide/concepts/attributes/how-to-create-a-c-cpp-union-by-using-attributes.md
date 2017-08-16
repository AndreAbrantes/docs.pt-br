---
title: "Como criar uma união do C-C++ usando atributos (C#) | Microsoft Docs"
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
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
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
ms.openlocfilehash: dd6bc60dfd1c6146d8fa72abdcfc6a00006817aa
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Como criar uma união do C-C++ usando atributos (C#)
Usando atributos, você pode personalizar como structs são dispostos na memória. Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.  
  
## <a name="example"></a>Exemplo  
 Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a>Exemplo  
 A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`. Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Atributos](https://msdn.microsoft.com/library/5x6cd29c)   
 [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Criando atributos personalizados (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
