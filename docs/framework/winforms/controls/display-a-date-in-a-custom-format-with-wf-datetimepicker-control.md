---
title: Exibir uma data em um formato personalizado com o controle DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745940"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms
O controle de <xref:System.Windows.Forms.DateTimePicker> de Windows Forms oferece flexibilidade na formatação da exibição de datas e horas no controle. A propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> permite que você selecione formatos predefinidos, listados na <xref:System.Windows.Forms.DateTimePickerFormat>. Se nenhuma delas for adequada para suas finalidades, você poderá criar seu próprio estilo de formato usando caracteres de formato listados em <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Para exibir um formato personalizado  
  
1. Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como `DateTimePickerFormat.Custom`.  
  
2. Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> como uma cadeia de caracteres de formato.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>Para adicionar texto ao valor formatado  
  
1. Use aspas simples para incluir qualquer caractere que não seja um caractere de formato como "M" ou um delimitador como ":". Por exemplo, a cadeia de formato a seguir exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos).  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     Dependendo da configuração de cultura, todos os caracteres que não estiverem entre aspas simples poderão ser alterados. Por exemplo, a cadeia de formato acima exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos). Observe que a primeira vírgula é colocada entre aspas simples, porque não se pretende que ela seja um caractere delimitador como em "hh:mm:ss". Em outra cultura, o formato pode ser exibido como "hoje é: 05.30.31 sexta-feira, 02 de março de 2012".  
  
## <a name="see-also"></a>Consulte também

- [Controle DateTimePicker](datetimepicker-control-windows-forms.md)
- [Como definir e retornar datas com o controle DateTimePicker dos Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
