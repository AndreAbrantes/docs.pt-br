---
title: Objeto My. Forms | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
dev_langs:
- VB
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
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
ms.openlocfilehash: 9e8422903d02358fcea38b362b111469cc5894e2
ms.lasthandoff: 03/13/2017

---
# <a name="myforms-object"></a>Objeto My.Forms
Fornece propriedades para acessar uma instância de cada Windows form declarado no projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual. O nome da propriedade é igual ao nome do formulário que acessa a propriedade. Para obter informações sobre como adicionar formas a um projeto, consulte [como: adicionar formulários do Windows para um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação. Como o nome da propriedade é o mesmo nome do tipo do formulário, isso permite que você acesse um formulário como se tivesse uma instância padrão. Por exemplo, `My.Forms.Form1.Show` é equivalente a `Form1.Show`.  
  
 O `My.Forms` objeto expõe apenas as formas associadas ao projeto atual. Ele não fornece acesso aos formulários declarado em DLLs referenciados. Para acessar um formulário que fornece uma DLL, você deve usar o nome qualificado do formulário, gravado como *DllName*.* Nome do formulário*.  
  
 Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>propriedade para obter uma coleção de todos os formulários do aplicativo aberto.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
  
 O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual. O nome da propriedade é igual ao nome do formulário que acessa a propriedade e o tipo de propriedade é o mesmo tipo do formulário.  
  
> [!NOTE]
>  Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário é *RootNamespace*_*Namespace*\_*nome do formulário*. Por exemplo, considere dois formulários denominados `Form1.`se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo que foi criada na inicialização. Para todas as outras formas, o `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e armazena. Tentativas subsequentes para acessar essa propriedade retornam essa instância do formulário.  
  
 Você pode descartar um formulário atribuindo `Nothing` para a propriedade desse formulário. A propriedade setter chama o <xref:System.Windows.Forms.Form.Close%2A>método do formulário e, em seguida, atribui `Nothing` para o valor armazenado.</xref:System.Windows.Forms.Form.Close%2A> Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException>exceção.</xref:System.ArgumentException>  
  
 Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador. Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância. No entanto, o compilador Visual Basic trata as propriedades do `My.Forms` diferente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo altera o título do padrão `SidebarMenu` formulário.  
  
 [!code-vb[VbVbalrMyForms n º&2;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve ter um formulário chamado `SidebarMenu`. Para obter mais informações, consulte [como: adicionar formulários do Windows para um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Esse código funciona apenas em um projeto de aplicativo do Windows.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="availability-by-project-type"></a>Disponibilidade por tipo de projeto  
  
|Tipo de projeto|Disponível|  
|---|---|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classes|Não|  
|Aplicativo do Console|Não|  
|Biblioteca de controle do Windows|Não|  
|Biblioteca de Controles da Web|Não|  
|Serviço do Windows|Não|  
|Site|Não|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Form.Close%2A></xref:System.Windows.Forms.Form.Close%2A>   
 [Objetos](../../../visual-basic/language-reference/objects/index.md)   
 [Como: adicionar formulários do Windows a um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)   
 [Operador is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Acessando formulários de aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
