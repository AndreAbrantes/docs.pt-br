---
title: "Programação paralela no .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 6a163776f358691c0f61c90dce98c15bebe4052a
ms.lasthandoff: 04/08/2017

---
# <a name="parallel-programming-in-the-net-framework"></a>Programação paralela no .NET Framework
Muitos computadores pessoais e estações de trabalho possuem dois ou quatro núcleos (ou seja, CPUs) que permite a execução de vários threads ao mesmo tempo. Em um futuro próximo, espera-se que os computadores possuam um número de núcleos significativamente maior. Para tirar proveito do hardware de hoje e do futuro, você pode paralelizar seu código para distribuir o trabalho entre vários processadores. No passado, a paralelização exigia a manipulação em baixo nível de threads e de bloqueios. O [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] e o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] aprimoram o suporte à programação paralela fornecendo um novo tempo de execução, novos tipos de biblioteca de classes e novas ferramentas de diagnóstico. Esses recursos simplificam o desenvolvimento paralelo para que você possa escrever código paralelo eficiente, refinado e dimensionável em uma linguagem natural sem precisar trabalhar diretamente com threads ou o pool de threads. A ilustração a seguir oferece uma visão geral de alto nível da arquitetura de programação em paralelo do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 ![Arquitetura de programação paralela .NET](../../../docs/standard/parallel-programming/media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Tecnologia|Descrição|  
|----------------|-----------------|  
|[TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fornece documentação para a classe <xref:System.Threading.Tasks.Parallel?displayProperty=fullName>, que inclui versões paralelas dos loops `For` e `ForEach`, bem como para a classe <xref:System.Threading.Tasks.Task?displayProperty=fullName>, que representa a maneira preferida de expressar operações assíncronas.|  
|[PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Uma implementação paralela do LINQ em Objects que melhora significativamente o desempenho em muitos cenários.|  
|[Estruturas de dados para programação paralela](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Fornece links para a documentação de classes de coleta com threads seguros, tipos de sincronização leves e tipos para inicialização lenta.|  
|[Ferramentas de diagnóstico paralelo](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Fornece links para a documentação de janelas do depurador do Visual Studio para tarefas e pilhas paralelas, bem como o [Visualizador Simultâneo](http://msdn.microsoft.com/library/ae5879a0-1e1a-455a-ba72-148e57f59289), que consiste em um conjunto de exibições no Criador de Perfil do [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] que você pode usar para depurar e ajustar o desempenho do código paralelo.|  
|[Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Descreve como os particionadores funcionam e como configurar os particionadores padrão ou criar um novo particionador.|  
|[Agendadores de tarefas](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Descreve como os agendadores funcionam e como os agendadores padrão podem ser configurados.|  
|[Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Fornece uma visão geral das expressões lambda em C# e Visual Basic e mostra como elas são usadas em PLINQ e na Biblioteca Paralela de Tarefas.|  
|[Para leitura adicional](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Fornece links para documentação adicional e recursos de exemplo para a programação paralela no .NET Framework.|  
  
## <a name="see-also"></a>Consulte também  
 [Padrões para programação paralela: noções básicas e aplicação de padrões paralelos com o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=185142)   
 [Amostras de programação paralela com o .NET Framework](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
