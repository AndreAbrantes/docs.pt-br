---
title: Tipos anuláveis estruturados (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202257"
---
# <a name="nullable-structured-types-entity-sql"></a>Tipos anuláveis estruturados (Entity SQL)

Uma instância de `null` de um tipo estruturada é uma instância que não existe. Isso é diferente de uma instância existente em que todas as propriedades têm valores de `null` .  
  
 Este tópico descreve os tipos estruturados anulável, incluindo que os tipos são anulável e que os padrões de código gerenciar instâncias de `null` de tipos anuláveis estruturados.  
  
## <a name="kinds-of-nullable-structured-types"></a>Tipos de tipos estruturados anulável  

 Existem três tipos de tipos anuláveis de framework:  
  
- Tipos de linha.  
  
- Tipos complexos.  
  
- Tipos de entidade.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Os padrões de código que gerenciar instâncias nulos Structured tipo  

 Os seguintes cenários gerenciar instâncias de `null` :  
  
- Na forma `null` como um tipo estruturada:  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Upcasting de um tipo base para um tipo derivado:  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Externo join à condição falsa:  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --ou  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --ou  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Desreferenciando uma referência de `null` :  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Obtendo ANYELEMENT de uma coleção vazia:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Verificar instâncias de `null` de tipos estruturados:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Veja também

- [Visão geral da Entity SQL](entity-sql-overview.md)
