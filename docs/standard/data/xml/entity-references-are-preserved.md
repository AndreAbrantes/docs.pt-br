---
title: Referências a entidades são preservadas
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 2cc2fcf3fdc2a89e4f72ae65e6e7385cb83f168c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823830"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="2cfe3-102">Referências a entidades são preservadas</span><span class="sxs-lookup"><span data-stu-id="2cfe3-102">Entity References are Preserved</span></span>
<span data-ttu-id="2cfe3-103">Quando a referência de entidade não é expandida, mas é preservada, o modelo de objeto (DOM) de documento XML cria um nó de **XmlEntityReference** quando encontra uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="2cfe3-104">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="2cfe3-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="2cfe3-105">o DOM cria um nó **XmlEntityReference** quando encontra a referência `&publisher;`.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="2cfe3-106">**XmlEntityReference** contém os nós filho copiados de conteúdo na declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="2cfe3-107">O exemplo de código anterior contém o texto na declaração de entidade. Assim, um nó **XmlText** é criado como o nó filho do nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="2cfe3-108">![Estrutura de árvore para referências de entidade preservadas](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="2cfe3-108">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="2cfe3-109">Estrutura de árvore para as referências de entidade que são preservadas</span><span class="sxs-lookup"><span data-stu-id="2cfe3-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="2cfe3-110">Os nós filho de **XmlEntityReference** são cópias de todos os nós filho criados do nó **XmlEntity** quando a declaração de entidade foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cfe3-111">Os nós copiados de **XmlEntity** não são sempre cópias exatas quando colocados no nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="2cfe3-112">Pode haver namespaces que estão no escopo no nó de referência de entidade, e que afetam a configuração final dos nós filho.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="2cfe3-113">Por padrão, entidades gerais como `&abc;` são preservadas, e nós **XmlEntityReference** são sempre criados.</span><span class="sxs-lookup"><span data-stu-id="2cfe3-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfe3-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="2cfe3-114">See also</span></span>

- [<span data-ttu-id="2cfe3-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="2cfe3-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
