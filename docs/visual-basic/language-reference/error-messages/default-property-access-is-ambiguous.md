---
title: O acesso à propriedade padrão é ambíguo entre os membros de interface herdada '<defaultpropertyname>' da interface '<interfacename1>' e '<defaultpropertyname>' da interface '<interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: b7c4c9c75de1b3777f34a70470b89f323a5699f9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162057"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>BC30686: o acesso à propriedade padrão é ambíguo entre os membros da interface herdada ' \<defaultpropertyname> ' da interface ' \<interfacename1> ' e ' \<defaultpropertyname> ' da interface ' \<interfacename2> '

Uma interface herda de duas interfaces, cada uma delas declara uma propriedade padrão com o mesmo nome. O compilador não pode resolver um acesso a essa propriedade padrão sem qualificação. O exemplo a seguir ilustra isto.

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

Quando você especifica `testObj(1)` , o compilador tenta resolvê-lo para a propriedade padrão. No entanto, há duas propriedades padrão possíveis devido às interfaces herdadas, portanto, o compilador sinaliza esse erro.

**ID do erro:** BC30686

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Evite herdar todos os membros com o mesmo nome. No exemplo anterior, se `testObj` não precisar de nenhum dos membros de, digamos, `Iface2` e, em seguida, declare-o da seguinte maneira:

  ```vb
  Dim testObj As Iface1
  ```

  \-ou-

- Implemente a interface herdada em uma classe. Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes. No entanto, apenas uma delas pode ser a propriedade padrão da classe de implementação. O exemplo a seguir ilustra isto.

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a>Veja também

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
