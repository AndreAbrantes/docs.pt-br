---
title: "Construtores de instância (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 5c579c28c6b298cc0aefe0cb9eb41993b84a23d8
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="instance-constructors-c-programming-guide"></a>Construtores de instâncias (Guia de Programação em C#)
Os construtores de instância são usados para criar e inicializar quaisquer variáveis de membro de instância quando você usa a expressão [new](../../../csharp/language-reference/keywords/new.md) para criar um objeto de uma [classe](../../../csharp/language-reference/keywords/class.md). Para inicializar uma classe [estática](../../../csharp/language-reference/keywords/static.md) ou variáveis estáticas em uma classe não estática, é necessário definir um construtor estático. Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 O exemplo a seguir mostra um construtor de instância:  
  
 [!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Para maior clareza, essa classe contém campos públicos. O uso de campos públicos não é uma prática de programação recomendada, porque permite que qualquer acesso de programa não restrito e não verificado a trabalhos internos de um objeto. Geralmente os membros de dados devem ser privados e devem ser acessados apenas por meio de propriedades e métodos de classe.  
  
 Esse construtor de instância é chamado sempre que um objeto com base na classe `CoOrds` é criado. Um construtor como este, que não usa nenhum argumento, é chamado um *construtor padrão*. No entanto, geralmente é útil fornecer construtores adicionais. Por exemplo, podemos adicionar um construtor à classe `CoOrds` que nos permite especificar os valores iniciais para os membros de dados:  
  
 [!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Isso permite que objetos `CoOrd` sejam criados com os valores iniciais padrão ou específicos, como este:  
  
 [!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Se uma classe não tem um construtor, um construtor padrão é gerado automaticamente e os valores padrão são usados para inicializar os campos de objeto. Por exemplo, um [int](../../../csharp/language-reference/keywords/int.md) é inicializada como 0. Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md). Portanto, como construtor padrão da classe `CoOrds` inicializa todos os membros de dados como zero, ele pode ser totalmente removido sem alterar a maneira como a classe funciona. Um exemplo completo que usa vários construtores é fornecido no Exemplo 1 posteriormente neste tópico e um exemplo de um construtor gerado automaticamente é fornecido no Exemplo 2.  
  
 Construtores de instância também podem ser usados para chamar os construtores de instância de classes base. O construtor de classe pode invocar o construtor da classe base por meio do inicializador, da seguinte maneira:  
  
 [!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Neste exemplo, a classe `Circle` passa valores que representam o raio e a altura do construtor fornecido pelo `Shape` do qual `Circle` é derivado. Um exemplo completo que usa `Shape` e `Circle` é exibido neste tópico como Exemplo 3.  
  
## <a name="example-1"></a>Exemplo 1  
 O exemplo a seguir demonstra uma classe com dois construtores de classe, um sem argumentos e outro com dois argumentos.  
  
 [!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Exemplo 2  
 Neste exemplo, a classe `Person` não tem nenhum construtor. Nesse caso, um construtor padrão é fornecido automaticamente e os campos são inicializados com seus valores padrão.  
  
 [!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Observe que o valor padrão de `age` é `0` e o valor padrão de `name` é `null`. Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Exemplo 3:  
 O exemplo a seguir demonstra como usar o inicializador de classe base. A classe `Circle` é derivada da classe geral `Shape` e a classe `Cylinder` é derivada da classe `Circle`. O construtor em cada classe derivada está usando seu inicializador de classe base.  
  
 [!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Para obter mais exemplos sobre a invocação de construtores de classe base, consulte [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) e [base](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [static](../../../csharp/language-reference/keywords/static.md)
