---
title: "Tipos de valor e referência | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: de8016b4b2a5550b32373a41c89a484fa996c596
ms.lasthandoff: 03/13/2017

---
# <a name="value-types-and-reference-types"></a>Tipos de valor e referência
No Visual Basic, os tipos de dados são implementados com base em sua classificação. O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados podem ser classificados de acordo com se uma variável de um determinado tipo armazena seus próprios dados ou um ponteiro para os dados. Se ela armazena seus próprios dados é um *tipo de valor*; se ela contém um ponteiro para os dados em outro lugar da memória é uma *tipo de referência*.  
  
## <a name="value-types"></a>Tipos de valor  
 Um tipo de dados é uma *tipo de valor* se ele mantém os dados dentro sua própria alocação de memória. Tipos de valor incluem o seguinte:  
  
-   Todos os tipos de dados numéricos  
  
-   `Boolean`, `Char` e `Date`  
  
-   Todas as estruturas, mesmo que seus membros são tipos de referência  
  
-   Enumerações, pois seu tipo base é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, ou`ULong`  
  
 Cada estrutura é um tipo de valor, mesmo se ele contiver membros de tipo de referência. Por esse motivo, tipos, como `Char` e `Integer` são implementados por estruturas do .NET Framework.  
  
 Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`. Você também pode usar o `New` palavra-chave para inicializar um tipo de valor. Isso é especialmente útil se o tipo tem um construtor que aceita parâmetros. Um exemplo disso é o <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>construtor, que cria um novo `Decimal` valor a partir das partes fornecidas.</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>  
  
## <a name="reference-types"></a>Tipos de referência  
 A *tipo de referência* contém um ponteiro para outro local da memória que mantém os dados. Tipos de referência incluem o seguinte:  
  
-   `String`  
  
-   Todas as matrizes, mesmo se seus elementos são tipos de valor  
  
-   Tipos de classe, como<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>  
  
-   Delegados  
  
 Uma classe é um *tipo de referência*. Por esse motivo, tipos de referência como `Object` e `String` são suportados pelo [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes. Observe que cada matriz é um tipo de referência, mesmo se seus membros são tipos de valor.  
  
 Como cada tipo de referência representa uma classe base do .NET Framework, você deve usar o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave quando fizer a inicialização. A instrução a seguir inicializa uma matriz.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementos que não são de tipos  
 Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar qualquer um deles como um tipo de dados de um elemento declarado:  
  
-   Namespaces  
  
-   Módulos  
  
-   Eventos  
  
-   Propriedades e procedimentos  
  
-   Variáveis, constantes e campos  
  
## <a name="working-with-the-object-data-type"></a>Trabalhando com o tipo de dados de objeto  
 Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do `Object` tipo de dados. Um `Object` variável sempre contém um ponteiro para os dados, nunca os dados propriamente ditos. No entanto, se você atribuir um tipo de valor para um `Object` variável, ele se comporta como se ele contém os seus próprios dados. Para obter mais informações, consulte [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Você pode descobrir se um `Object` variável está atuando como um tipo de referência ou um tipo de valor, passando-o para o <xref:Microsoft.VisualBasic.Information.IsReference%2A>método o <xref:Microsoft.VisualBasic.Information>classe do <xref:Microsoft.VisualBasic?displayProperty=fullName>namespace.</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.Information> </xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>Retorna `True` se o conteúdo de `Object` variável representa um tipo de referência.</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de valor anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Uso eficiente de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
