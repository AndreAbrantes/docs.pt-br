---
title: 'Como: especificar nomes de banco de dados'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 82cb3f8f31af433b0299b4fec742b548d61921e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197151"
---
# <a name="how-to-specify-database-names"></a>Como: especificar nomes de banco de dados

Use a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> em um atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para especificar o nome de uma base de dados quando um nome não é fornecido pela conexão.  
  
 Para exemplos de códigos, consulte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Para especificar o nome de base de dados  
  
1. Adicione o atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para a declaração de classe para o base de dados.  
  
2. Adicione a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ao atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> .  
  
3. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> o nome que você deseja especificar.  
  
## <a name="see-also"></a>Veja também

- [Modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Como: personalizar classes de entidade usando o editor de códigos](how-to-customize-entity-classes-by-using-the-code-editor.md)
