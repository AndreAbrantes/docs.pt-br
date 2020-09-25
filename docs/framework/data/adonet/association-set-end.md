---
title: extremidade do conjunto de associação
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: bd104ffb46cbd02a886ce87822ddc37159961174
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198789"
---
# <a name="association-set-end"></a>extremidade do conjunto de associação

Uma *extremidade de conjunto de associação* identifica o [tipo de entidade](entity-type.md) e a [entidade definida](entity-set.md) no final de um [conjunto de associação](association-set.md). Termina do conjunto de associações são definidas como parte de um conjunto de associações; um conjunto de associações deve ter exatamente duas termina do conjunto de associações.  
  
 Uma definição de final do conjunto de associações contém as informações a seguir:  
  
- Um dos tipos de entidade envolvidos no conjunto de associações. (Obrigatória)  
  
- O conjunto de entidades para o tipo de entidade envolvido no conjunto de associações. (Obrigatória)  
  
## <a name="example"></a>Exemplo  

 O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`.  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-set-end/example-model-three-entity-types.gif)  
  
 O diagrama a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima. Termina do conjunto de associações são conjuntos de entidades de `Books` e de `Publishers` . Bi no `Books` conjunto de entidades representa uma instância do `Book` tipo de entidade em tempo de execução. Da mesma forma, PJ representa uma `Publisher` instância no `Publishers` conjunto de entidades. BiPj representa uma instância da `PublishedBy` associação no conjunto de `PublishedBy` associação.  
  
 ![Captura de tela que mostra um exemplo de conjuntos.](./media/association-set-end/sets-example-association.gif)  
  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL chamada linguagem de definição de esquema conceitual ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) para definir modelos conceituais. CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior. Observe que termina do conjunto de associações são definidas como parte de cada definição do conjunto de associações.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Veja também

- [Conceitos chave do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
