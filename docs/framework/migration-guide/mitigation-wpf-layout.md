---
title: "Mitigação: layout do WPF | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bb9208e030de676bf18f405d1f1ca0e78308899d
ms.contentlocale: pt-br
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-wpf-layout"></a>Mitigação: layout de WPF
O layout dos controles do WPF pode ser ligeiramente alterado.  
  
## <a name="impact"></a>Impacto  
 Como resultado dessa alteração:  
  
-   A largura ou altura dos elementos pode aumentar ou reduzir em um pixel no máximo.  
  
-   O posicionamento de um objeto pode ser movido até um pixel, no máximo.  
  
-   Os elementos centralizados podem estar vertical ou horizontalmente fora do centro em, no máximo, um pixel.  
  
 Por padrão, esse novo layout é habilitado somente para aplicativos que se destinam ao .NET Framework 4.6.  
  
## <a name="mitigation"></a>Redução  
 Uma vez que essa modificação tende a eliminar a distorção da direita ou da parte inferior dos controles do WPF em DPIs altos, os aplicativos que de destinam a versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6, podem aderir a esse novo comportamento adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Os aplicativos que se destinam ao .NET Framework 4.6, mas querem que os controles do WPF renderizem usando o algoritmo de layout anterior podem fazer isso adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
