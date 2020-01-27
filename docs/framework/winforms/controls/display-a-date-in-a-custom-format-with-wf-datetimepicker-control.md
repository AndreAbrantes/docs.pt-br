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
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="751e4-102">Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="751e4-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="751e4-103">O controle de <xref:System.Windows.Forms.DateTimePicker> de Windows Forms oferece flexibilidade na formatação da exibição de datas e horas no controle.</span><span class="sxs-lookup"><span data-stu-id="751e4-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="751e4-104">A propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> permite que você selecione formatos predefinidos, listados na <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="751e4-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="751e4-105">Se nenhuma delas for adequada para suas finalidades, você poderá criar seu próprio estilo de formato usando caracteres de formato listados em <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="751e4-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="751e4-106">Para exibir um formato personalizado</span><span class="sxs-lookup"><span data-stu-id="751e4-106">To display a custom format</span></span>  
  
1. <span data-ttu-id="751e4-107">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="751e4-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="751e4-108">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> como uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="751e4-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="751e4-109">Para adicionar texto ao valor formatado</span><span class="sxs-lookup"><span data-stu-id="751e4-109">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="751e4-110">Use aspas simples para incluir qualquer caractere que não seja um caractere de formato como "M" ou um delimitador como ":".</span><span class="sxs-lookup"><span data-stu-id="751e4-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="751e4-111">Por exemplo, a cadeia de formato a seguir exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="751e4-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="751e4-112">Dependendo da configuração de cultura, todos os caracteres que não estiverem entre aspas simples poderão ser alterados.</span><span class="sxs-lookup"><span data-stu-id="751e4-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="751e4-113">Por exemplo, a cadeia de formato acima exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="751e4-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="751e4-114">Observe que a primeira vírgula é colocada entre aspas simples, porque não se pretende que ela seja um caractere delimitador como em "hh:mm:ss".</span><span class="sxs-lookup"><span data-stu-id="751e4-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="751e4-115">Em outra cultura, o formato pode ser exibido como "hoje é: 05.30.31 sexta-feira, 02 de março de 2012".</span><span class="sxs-lookup"><span data-stu-id="751e4-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751e4-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="751e4-116">See also</span></span>

- [<span data-ttu-id="751e4-117">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="751e4-117">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="751e4-118">Como definir e retornar datas com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="751e4-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
