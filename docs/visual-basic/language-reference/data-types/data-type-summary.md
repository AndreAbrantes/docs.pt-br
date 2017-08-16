---
title: Tipo de dados de resumo (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Boolean data type, supported types in Visual Basic
- storage, order of storage
- data types [Visual Basic], Visual Basic
- Single data type, supported types in Visual Basic
- notation, scientific
- memory requirements, data types
- user-defined data types, Visual Basic
- Date data type, Visual Basic
- Visual Basic, data types
- storage, allocation
- Integer data type, Visual Basic data types
- storage, space
- Variant data types, supported types in Visual Basic
- Char data type, Visual Basic data types
- intrinsic data types
- memory consumption, data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type, supported types in Visual Basic
- String data type, Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type, Visual Basic data types
- Byte data type, Visual Basic data types
- Object data type, supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: 22
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
ms.openlocfilehash: 78e3451fecd81577ae90e1d5e97547224380784d
ms.lasthandoff: 03/13/2017

---
# <a name="data-type-summary-visual-basic"></a>Resumo do tipo de dados (Visual Basic)
A tabela a seguir mostra os tipos de dados do Visual Basic, seus tipos common language runtime suporte, a alocação de armazenamento nominal e os intervalos de valor.  
  
|Tipo do Visual Basic|Estrutura do tipo Common language runtime|Alocação de armazenamento nominal|Intervalo de valores|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean></xref:System.Boolean>|Depende de implementação de plataforma|`True` ou `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte></xref:System.Byte>|1 byte|0 a 255 (não assinado)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) (um único caractere)|<xref:System.Char></xref:System.Char>|2 bytes|0 a 65535 (não assinado)|  
|[Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime></xref:System.DateTime>|8 bytes|0:00:00 (meia-noite) em 1º de janeiro de 0001 até 11:59:59 PM em 31 de dezembro de 9999|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal></xref:System.Decimal>|16 bytes|0 a + /-79.228.162.514.264.337.593.543.950.335 (+ /-7.9... E + 28) <sup>†</sup> sem nenhum ponto decimal; 0 a + /-7.9228162514264337593543950335 com 28 casas à direita do decimal;<br /><br /> menor número diferente de zero é + /-0,0000000000000000000000000001 (+ /-1E-28) <sup>†</sup>|  
|[Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) (precisão dupla ponto flutuante)|<xref:System.Double></xref:System.Double>|8 bytes|-1,&79769;313486231570E +&308; até -&4;.94065645841246544 e-324 <sup>†</sup> para valores negativos;<br /><br /> 4.94065645841246544 e-324 1.79769313486231570 e + 308 <sup>†</sup> para valores positivos|  
|[Número inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32></xref:System.Int32>|4 bytes|-2.147.483.648 a 2.147.483.647 (assinado)|  
|[Longo](../../../visual-basic/language-reference/data-types/long-data-type.md) (inteiro longo)|<xref:System.Int64></xref:System.Int64>|8 bytes|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2... E + 18 <sup>†</sup>) (assinado)|  
|[Objeto](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>(classe)</xref:System.Object>|4 bytes na plataforma de 32 bits<br /><br /> 8 bytes na plataforma de 64 bits|Qualquer tipo pode ser armazenado em uma variável de tipo`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte></xref:System.SByte>|1 byte|-128 a 127 (assinado)|  
|[Curto](../../../visual-basic/language-reference/data-types/short-data-type.md) (inteiro curto)|<xref:System.Int16></xref:System.Int16>|2 bytes|-32.768 a 32.767 (assinado)|  
|[Único](../../../visual-basic/language-reference/data-types/single-data-type.md) (único ponto flutuante de precisão)|<xref:System.Single></xref:System.Single>|4 bytes|-3,&40282;35E +&38; a -&1;,&40129;8E-45 <sup>†</sup> para valores negativos;<br /><br /> 1, 401298E-45 a 3, 4028235E + 38 <sup>†</sup> para valores positivos|  
|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) (comprimento variável)|<xref:System.String>(classe)</xref:System.String>|Depende de implementação de plataforma|0 a aproximadamente 2 bilhões de caracteres Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32></xref:System.UInt32>|4 bytes|0 a 4.294.967.295 (não assinado)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64></xref:System.UInt64>|8 bytes|0 e 18.446.744.073.709.551.615 (1.8... E + 19 <sup>†</sup>) (não assinado)|  
|[Definido pelo usuário](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (estrutura)|(herda de <xref:System.ValueType>)</xref:System.ValueType>|Depende de implementação de plataforma|Cada membro da estrutura tem um intervalo determinado pelo seu tipo de dados e independentes dos intervalos dos outros membros|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16></xref:System.UInt16>|2 bytes|0 a 65.535 (não assinado)|  
  
 <sup>†</sup> Na *notação científica*, "E" se refere a uma potência de 10. Para 3.56E + 2 significa 3,56 x 10<sup>2</sup> ou 356 e 3.56E-2 significa 3,56 / 10<sup>2</sup> ou 0.0356.  
  
> [!NOTE]
>  Cadeias de caracteres que contém texto, use o <xref:Microsoft.VisualBasic.Strings.StrConv%2A>função para converter do formato de texto de um para outro.</xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
  
 Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação usando um caractere de tipo. Consulte [digitar caracteres](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Consumo de memória  
 Quando você declarar um tipo de dados elementar, não é seguro pressupor que seu consumo de memória é o mesmo que a alocação de armazenamento nominal. Isso ocorre devido a considerações a seguir:  
  
-   **Atribuição de armazenamento.** O common language runtime pode atribuir o armazenamento com base nas características da plataforma na qual seu aplicativo está em execução atuais. Se a memória está quase cheia, ele pode pack seus elementos declarados como intimamente juntos possível. Em outros casos ele poderá alinhar os endereços de memória limites de hardware natural para otimizar o desempenho.  
  
-   **Largura da plataforma.** Atribuição de armazenamento em uma plataforma de 64 bits é diferente de atribuição em uma plataforma de 32 bits.  
  
### <a name="composite-data-types"></a>Tipos de dados compostos  
 As mesmas considerações se aplicam a cada membro de um tipo de dados compostos, como uma estrutura ou uma matriz. Você não pode depender simplesmente somar as alocações de armazenamento nominais de membros do tipo. Além disso, existem outras considerações, como o seguinte:  
  
-   **Sobrecarga.** Alguns tipos compostos têm requisitos de memória adicional. Por exemplo, uma matriz usa memória extra para o próprio array e também para cada dimensão. Em uma plataforma de 32 bits, essa sobrecarga é atualmente 12 bytes mais de 8 bytes para cada dimensão. Em uma plataforma de 64 bits, esse requisito é duplicado.  
  
-   **Layout de armazenamento.** Você não pode presumir que a ordem de armazenamento em memória é o mesmo que a ordem da declaração. Você não pode fazer suposições sobre o alinhamento de bytes, como um limite de 2 ou 4 bytes. Se você estiver definindo uma classe ou estrutura e você precisa controlar o layout de armazenamento de seus membros, você pode aplicar o <xref:System.Runtime.InteropServices.StructLayoutAttribute>de atributo para a classe ou estrutura.</xref:System.Runtime.InteropServices.StructLayoutAttribute>  
  
### <a name="object-overhead"></a>Sobrecarga de objeto  
 Um `Object` referindo-se a todos os dados elementares ou compostos tipo usa 4 bytes, além dos dados contidos no tipo de dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A></xref:Microsoft.VisualBasic.Strings.StrConv%2A>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute></xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
