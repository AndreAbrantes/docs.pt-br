---
title: Usando variação em delegações (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 00e11d4ce755c8c75b73023fec14d95ebc96b4fe
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595269"
---
# <a name="using-variance-in-delegates-c"></a>Usando variação em delegações (C#)
Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método. A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado. A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.  
  
## <a name="example-1-covariance"></a>Exemplo 1: Covariância  
  
### <a name="description"></a>DESCRIÇÃO  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado. O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.  
  
### <a name="code"></a>Código  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a>Exemplo 2: Contravariância  
  
### <a name="description"></a>DESCRIÇÃO  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado. Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados. Por exemplo, você pode criar um manipulador de eventos que aceita um parâmetro de entrada `EventArgs` e usá-lo com um evento `Button.MouseClick` que envia um tipo `MouseEventArgs` como um parâmetro e também com um evento `TextBox.KeyDown` que envia um parâmetro `KeyEventArgs`.  
  
### <a name="code"></a>Código  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Variação em delegados (C#)](./variance-in-delegates.md)
- [Usando variação para delegados genéricos Func e Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
