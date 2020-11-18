---
title: Afetar o namespace da expansão de referência de entidade para novos elementos e atributos recipiente de nós
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 8ef86f05d2b39639ad5faae792eb9b2854ff0673
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830162"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="8a86b-102">Afetar o namespace da expansão de referência de entidade para novos elementos e atributos recipiente de nós</span><span class="sxs-lookup"><span data-stu-id="8a86b-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="8a86b-103">Porque o conteúdo de uma declaração de entidade pode conter qualquer coisa, há uma chance de que o conteúdo pode conter um elemento como `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="8a86b-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="8a86b-104">Quando XML é analisado, `&aname;` não é expandido com o conteúdo de substituição em tempo de análise.</span><span class="sxs-lookup"><span data-stu-id="8a86b-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="8a86b-105">A expansão XML não é feita porque a resolução de namespace para o elemento não pode ocorrer até que o nó é colocado no documento.</span><span class="sxs-lookup"><span data-stu-id="8a86b-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="8a86b-106">Até esse momento, eles não há nenhum conhecimento de namespace que está no escopo.</span><span class="sxs-lookup"><span data-stu-id="8a86b-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="8a86b-107">Quando o nó é colocado no documento, então a resolução do namespace ocorre, e o conteúdo de entidade resultante é analisado em seus nós apropriadas.</span><span class="sxs-lookup"><span data-stu-id="8a86b-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a86b-108">Uma vez que a expansão ocorre em um nó recém-criado de referência de entidade, nunca repete.</span><span class="sxs-lookup"><span data-stu-id="8a86b-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="8a86b-109">Portanto, namespaces utilizados no texto de substituição para o elemento são associadas no momento em que o nó pai é definido.</span><span class="sxs-lookup"><span data-stu-id="8a86b-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="8a86b-110">No entanto, o namespace pode ser alterado para nós existentes de referência de entidade quando você o remove e inserir em outro lugar, ou em nós de referência de entidade que são clonados com o método **CloneNode**.</span><span class="sxs-lookup"><span data-stu-id="8a86b-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a86b-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="8a86b-111">See also</span></span>

- [<span data-ttu-id="8a86b-112">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="8a86b-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
