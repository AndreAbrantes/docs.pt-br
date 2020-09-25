---
title: 'Como: resolver conflitos mantendo valores de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191691"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Como: resolver conflitos mantendo valores de banco de dados

Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> para manter os valores localizados na base de dados. Os valores atuais no modelo de objeto são substituídos em seguida. Para obter mais informações, consulte [simultaneidade otimista: visão geral](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados. Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.  
  
## <a name="example"></a>Exemplo  

 Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento. A tabela a seguir mostra a situação.  
  
||Gerente|Assistente|department|  
|------|-------------|---------------|----------------|  
|Estado original de base de dados quando consultado por User1 e por Usuário2.|Alfreds|Maria|Sales|  
|User1 prepara-se para enviar essas alterações.|Alfred||Marketing|  
|Usuário2 já tiver enviado essas alterações.||Mary|Serviço|  
  
 User1 decidir resolver esse conflito com os valores mais recentes de base de dados substitui os valores atuais no modelo de objeto.  
  
 Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, o resultado na base de dados é o seguinte na tabela:  
  
||Gerente|Assistente|department|  
|------|-------------|---------------|----------------|  
|Novo estado após a resolução do conflito.|Alfreds<br /><br /> (original)|Mary<br /><br /> (de Usuário2)|Serviço<br /><br /> (de Usuário2)|  
  
 O código exemplo a seguir mostra como substituir valores atuais no modelo de objeto com os valores de base de dados. (Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Veja também

- [Como: gerenciar conflitos de alteração](how-to-manage-change-conflicts.md)
