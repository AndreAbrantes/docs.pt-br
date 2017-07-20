---
title: Manifesto do assembly | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 58098e2107fcab96f82677094e50529fafba98e5
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="assembly-manifest"></a>Manifesto de um assembly
Cada assembly, seja estático ou dinâmico, contém uma coleção de dados que descreve como os elementos do assembly se relacionam. O manifesto do assembly contém esses metadados do assembly. O manifesto de um assembly contém todos os metadados necessários para especificar os requisitos de versão e a identidade de segurança, além de todos os metadados necessários para definir o escopo do assembly e resolver referências a recursos e classes. O manifesto do assembly pode ser armazenado em um arquivo PE (.exe ou .dll) com código MSIL (Microsoft Intermediate Language) ou em um arquivo PE autônomo que contém somente informações do manifesto do assembly.  
  
 A ilustração a seguir mostra as diferentes maneiras nas quais o manifesto pode se armazenado.  
  
 ![Um assembly de arquivo único](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")  
Tipos de assemblies  
  
 Para um assembly com um arquivo associado, o manifesto é incorporado ao arquivo PE para formar um assembly de arquivo único. Você pode criar um assembly de vários arquivos com um arquivo de manifesto autônomo ou com o manifesto incorporado a um dos arquivos PE do assembly.  
  
 Cada manifesto de um assembly executa as seguintes funções:  
  
-   Enumera os arquivos que compõem o assembly.  
  
-   Determina como as referências a tipos e recursos do assembly são mapeadas para arquivos que contenham suas declarações e implementações.  
  
-   Enumera outros assemblies dos quais o assembly depende.  
  
-   Fornece um nível de indireção entre consumidores do assembly e detalhes da implementação do assembly.  
  
-   Renderiza o assembly autodescritivo.  
  
## <a name="assembly-manifest-contents"></a>Conteúdo do manifesto do assembly  
 A tabela a seguir mostra as informações contidas no manifesto do assembly. Os primeiros quatro itens — informações sobre o nome, o número de versão, a cultura e o nome forte do assembly — compõem a identidade do assembly.  
  
|Informações|Descrição|  
|-----------------|-----------------|  
|Nome do assembly|Uma cadeia de caracteres de texto especificando o nome do assembly.|  
|Número de versão|Um número de versão principal e secundário, além de um número de revisão e de compilação. O Common Language Runtime usa esses números para impor uma política de versões.|  
|Cultura|Informações sobre a cultura ou a linguagem compatível com o assembly. Essas informações só devem ser usadas para designar um assembly como um assembly satélite contendo informações específicas de cultura ou de linguagem. (Um assembly com informações de cultura é automaticamente considerado um assembly satélite.)|  
|Informações sobre nome forte|A chave pública do editor, caso tenha sido dado ao assembly um nome forte.|  
|Lista de todos os arquivos no assembly|Um hash de cada arquivo contido no assembly e um nome de arquivo. Observe que todos os arquivos que compõem o assembly devem estar no mesmo diretório que o arquivo que contém o manifesto do assembly.|  
|Informações de referência de tipo|Informações usadas pelo ambiente de execução para mapear a referência de um tipo para o arquivo que contém sua declaração e implementação. Usado em tipos que são exportados do assembly.|  
|Informações sobre assemblies referenciados|Uma lista de outros assemblies que são referenciados estaticamente pelo assembly. Cada referência inclui o nome do assembly dependente, metadados do assembly (versão, cultura, sistema operacional etc.) e chave pública, caso o assembly possua um nome forte.|  
  
 Você pode adicionar ou alterar informações do manifesto do assembly usando os atributos do assembly em seu código. Você pode alterar informações sobre versão e atributos informativos, incluindo marca comercial, direitos autorais, produto, empresa e versão informativa. Para obter uma lista completa dos atributos do assembly, confira [Configuração de atributos de assembly](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conteúdo do assembly](../../../docs/framework/app-domains/assembly-contents.md)   
 [Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md)   
 [Criação de assemblies satélite](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)   
 [Assemblies de nomes fortes](../../../docs/framework/app-domains/strong-named-assemblies.md)
