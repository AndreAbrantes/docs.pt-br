---
title: Exceções e desempenho
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: e3a7fa0f284ebf028a18cae37c050d7ceda9bb79
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709381"
---
# <a name="exceptions-and-performance"></a>Exceções e desempenho
Uma preocupação comum relacionada às exceções é que, se as exceções forem usadas para o código que falha rotineiramente, o desempenho da implementação será inaceitável. Essa é uma preocupação válida. Quando um membro gera uma exceção, seu desempenho pode ser uma ordem de magnitude mais lenta. No entanto, é possível obter um bom desempenho, atendendo estritamente às diretrizes de exceção que não permitem o uso de códigos de erro. Dois padrões descritos nesta seção sugerem maneiras de fazer isso.

 **X DO NOT** usar códigos de erro devido a questões que exceções podem afetar negativamente o desempenho.

 Para melhorar o desempenho, é possível usar o padrão Tester-doer ou o padrão try-Parse, descrito nas duas próximas seções.

## <a name="tester-doer-pattern"></a>Padrão de teste-doer
 Às vezes, o desempenho de um membro de lançamento de exceção pode ser melhorado ao dividir o membro em dois. Vejamos o método <xref:System.Collections.Generic.ICollection%601.Add%2A> da interface <xref:System.Collections.Generic.ICollection%601>.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 O método `Add` gera se a coleção é somente leitura. Isso pode ser um problema de desempenho em cenários em que a chamada do método deve falhar com frequência. Uma das maneiras de mitigar o problema é testar se a coleção é gravável antes de tentar adicionar um valor.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é chamado de testador. O membro usado para executar uma operação potencialmente de lançamento, o método `Add` em nosso exemplo, é chamado de doer.

 **✓ CONSIDER** o padrão de mal-intencionado Testador de membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.

## <a name="try-parse-pattern"></a>Padrão Experimente-Parse
 Para APIs extremamente sensíveis ao desempenho, um padrão ainda mais rápido do que o padrão testador doer descrito na seção anterior deve ser usado. O padrão chama o ajuste do nome do membro para fazer com que um caso de teste bem definido faça parte da semântica do membro. Por exemplo, <xref:System.DateTime> define um método <xref:System.DateTime.Parse%2A> que gera uma exceção se a análise de uma cadeia de caracteres falhar. Ele também define um método <xref:System.DateTime.TryParse%2A> correspondente que tenta analisar, mas retorna false se a análise não for bem-sucedida e retornar o resultado de uma análise bem-sucedida usando um parâmetro `out`.

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 Ao usar esse padrão, é importante definir a funcionalidade Try em termos estritos. Se o membro falhar por algum motivo além da tentativa definida, o membro ainda deverá lançar uma exceção correspondente.

 **✓ CONSIDER** o padrão de Try-análise para os membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.

 **✓ DO** usam o prefixo "Try" e Boolean tipo de retorno para métodos de implementar esse padrão.

 **✓ DO** fornecem um membro geradoras de exceções para cada membro usando o padrão de análise de Try.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
