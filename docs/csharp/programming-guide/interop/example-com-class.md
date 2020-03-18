---
title: Exemplo de classe COM – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712072"
---
# <a name="example-com-class-c-programming-guide"></a>Exemplo de classe COM (Guia de Programação em C#)
A seguir está um exemplo de uma classe que você poderia expor como um objeto COM. Depois que esse código é colocado em um arquivo .cs e adicionado ao seu projeto, defina a propriedade **Registrar para interoperabilidade COM** como **True**. Para obter mais informações, consulte [Como registrar um componente para interoperabilidade COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 A exposição de objetos do Visual C# para COM requer a declaração de uma interface de classe, de uma interface de eventos se necessário e da própria classe. Os membros de classe devem seguir estas regras para ficarem visíveis ao COM:  
  
- A classe deve ser pública.  
  
- As propriedades, os métodos e os eventos devem ser públicos.  
  
- As propriedades e os métodos devem ser declarados na interface de classe.  
  
- Os eventos devem ser declarados na interface de eventos.  
  
 Os outros membros públicos na classe que não forem declarados nessas interfaces não estarão visíveis para o COM, mas eles estarão visíveis para outros objetos do .NET Framework.  
  
 Para expor propriedades e métodos ao COM, você deve declará-los na interface de classe e marcá-los com um atributo `DispId` e implementá-los na classe. A ordem na qual os membros são declarados na interface é a ordem usada para a vtable do COM.  
  
 Para expor eventos de sua classe, você deve declará-los na interface de eventos e marcá-los com um atributo `DispId`. A classe não deve implementar essa interface.  
  
 A classe implementa a interface de classe. Ela pode implementar mais de uma interface, mas a primeira implementação será a interface de classe padrão. Implemente os métodos e propriedades expostos ao COM aqui. Eles devem ser marcados como públicos e devem corresponder às declarações na interface de classe. Além disso, declare aqui os eventos acionados pela classe. Eles devem ser marcados como públicos e devem corresponder às declarações na interface de eventos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Interoperabilidade](./index.md)
- [Página de Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
