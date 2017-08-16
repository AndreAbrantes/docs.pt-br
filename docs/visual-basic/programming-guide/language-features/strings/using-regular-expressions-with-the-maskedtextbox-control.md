---
title: "Usando expressões regulares com o controle MaskedTextBox no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
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
ms.openlocfilehash: 15d8f131aa834321fcf7e8ca633929385c666e6a
ms.lasthandoff: 03/13/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Usando expressões regulares com o controle MaskedTextBox no Visual Basic
Este exemplo demonstra como converter expressões regulares simples para trabalhar com o <xref:System.Windows.Forms.MaskedTextBox>controle.</xref:System.Windows.Forms.MaskedTextBox>  
  
## <a name="description-of-the-masking-language"></a>Descrição da linguagem máscara  
 O padrão <xref:System.Windows.Forms.MaskedTextBox>linguagem máscara é baseada na usada pelo `Masked Edit` controlar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 e deve ser familiar aos usuários migrando desta plataforma.</xref:System.Windows.Forms.MaskedTextBox>  
  
 O <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>propriedade o <xref:System.Windows.Forms.MaskedTextBox>controle especifica qual máscara de entrada usar.</xref:System.Windows.Forms.MaskedTextBox> </xref:System.Windows.Forms.MaskedTextBox.Mask%2A> A máscara deve ser uma cadeia de caracteres composta de um ou mais elementos de máscara da seguinte tabela.  
  
|Elemento de mascaramento|Descrição|Elemento de expressão regular|  
|---------------------|-----------------|--------------------------------|  
|0|Qualquer dígito único entre 0 e 9. Entrada obrigatória.|\d|  
|9|Dígito ou espaço. Entrada opcional.|[ \d]?|  
|#|Dígito ou espaço. Entrada opcional. Se a posição é deixada vazia na máscara, ele será renderizado como um espaço. Sinal de adição (+) e menos (-) são permitidos.|[ \d+-]?|  
|L|Letra ASCII. Entrada obrigatória.|[a-zA-Z]|  
|?|Letra ASCII. Entrada opcional.|[a-zA-Z]?|  
|&|Caractere. Entrada obrigatória.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo]}|  
|C|Caractere. Entrada opcional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|Um|Alfanumérico. Entrada opcional.|\W|  
|.|Local apropriado para decimal.|Não disponível.|  
|,|Espaço reservado apropriado milhares.|Não disponível.|  
|:|Separador de tempo apropriado.|Não disponível.|  
|/|Separador de data apropriado.|Não disponível.|  
|$|Símbolo de moeda apropriado.|Não disponível.|  
|\<|Converte todos os caracteres em minúsculas.|Não disponível.|  
|>|Converte todos os caracteres em maiusculas.|Não disponível.|  
|&#124;|Desfaz um turno anterior para cima ou baixo.|Não disponível.|  
|\|Ignora um caractere de máscara, transformando-a em um literal. "\\\\" é a sequência de escape para uma barra invertida.|\|  
|Todos os outros caracteres.|Literais. Todos os elementos não máscara serão exibido como eles próprios no <xref:System.Windows.Forms.MaskedTextBox>.</xref:System.Windows.Forms.MaskedTextBox>|Todos os outros caracteres.|  
  
 O decimal (.), milhares (,), tempo (:), data (/) e padrão de símbolos de moeda ($) para exibir os símbolos, conforme definido pela cultura do aplicativo. Você pode forçá-los a mostrar símbolos de outra localização usando a <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>propriedade.</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>  
  
## <a name="regular-expressions-and-masks"></a>Expressões regulares e máscaras  
 Embora você possa usar expressões regulares e máscaras para validar a entrada do usuário, elas não são completamente equivalentes. Expressões regulares podem expressar padrões mais complexos que máscaras, mas máscaras podem expressar a mesma informação mais sucintamente e em um formato localmente relevante.  
  
 A tabela a seguir compara quatro expressões regulares e a máscara equivalente para cada.  
  
|Expressão regular|Máscara|Observações|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O `/` caractere na máscara é um separador de data lógica, e ela será exibida para o usuário como o separador de data apropriado para a cultura atual do aplicativo.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data (dia, abreviação de mês e ano) no formato americano em que a abreviação de mês de três letras é exibida com uma letra maiuscula inicial seguida de duas letras minúsculas.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Telefone nos EUA, código de área opcional. Se o usuário não deseja entrar os caracteres opcionais, ela pode inserir espaços ou coloque o ponteiro do mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor de moeda no intervalo de 0 a 999999. Caracteres decimais, moeda e milésimos serão substituídos em tempo de execução por seus equivalentes de cultura específica.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [Controle MaskedTextBox](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)
