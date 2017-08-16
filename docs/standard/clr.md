---
title: Common Language Runtime (CLR) | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
caps.latest.revision: 24
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 69b30d2e6d3b92e33d6bc827fa1a8de6298e6a1f
ms.contentlocale: pt-br
ms.lasthandoff: 05/11/2017

---
# <a name="common-language-runtime-clr"></a>CLR (Common Language Runtime)
O .NET Framework fornece um ambiente de tempo de execução chamado Common Language Runtime, que executa o código e fornece serviços que facilitam o processo de desenvolvimento.  
  
 Compiladores e ferramentas expõem as funcionalidades do Common Language Runtime e permitem que você grave um código que se beneficia desse ambiente de execução gerenciado. O código que você desenvolve com um compilador de linguagem que visa o tempo de execução é chamado de código gerenciado. Ele aproveita recursos como integração em qualquer idioma, tratamento de exceções em qualquer idioma, segurança aprimorada, suporte a controle de versão e implantação, um modelo simplificado para interação entre componentes, além de serviços de depuração e criação de perfil.  
  
> [!NOTE]
>  Compiladores e ferramentas podem produzir saída que o Common Language Runtime pode consumir porque o sistema de tipos, o formato dos metadados e o ambiente de tempo de execução (o sistema virtual de execução) são todos definidos por um padrão público, a especificação Common Language Infrastructure ECMA. Para obter mais informações, consulte [Especificações ECMA C# e Common Language Infrastructure](http://go.microsoft.com/fwlink/?LinkId=99212).  
  
 Para habilitar o tempo de execução para fornecer serviços de código gerenciado, os compiladores de linguagem devem emitir metadados que descrevam os tipos, os membros e as referências em seu código. Os metadados são armazenados com o código. Todo arquivo PE (Portable Executable) do Common Language Runtime carregável contém metadados. O tempo de execução usa metadados para localizar e carregar classes, dispor instâncias na memória, resolver invocações de método, gerar código nativo, impor segurança e definir limites de contexto do tempo de execução.  
  
 O tempo de execução identifica automaticamente o layout de objeto e gerencia referências a objetos, liberando-os quando eles não estão sendo mais usados. Objetos cujos tempos de vida são gerenciados dessa forma são chamados de dados gerenciados. A coleta de lixo elimina perdas de memória, bem como alguns outros erros de programação comuns. Se o código for gerenciado, você poderá usar dados gerenciados, dados não gerenciados ou ambos no seu aplicativo do .NET Framework. Como os compiladores de linguagem fornecem seus próprios tipos, como tipos primitivos, você talvez sem sempre saiba (ou precise saber) se os dados estão sendo gerenciados.  
  
 O Common Language Runtime facilita a criação de componentes e aplicativos cujos objetos interagem entre linguagens. Objetos gravados em linguagens diferentes podem se comunicar entre si e seus comportamentos podem estar totalmente integrados. Por exemplo, você pode definir uma classe e usar uma linguagem diferente para derivar uma classe da classe original ou chamar um método na classe original. Você também pode passar uma instância de uma classe para um método de uma classe gravado em uma linguagem diferente. Essa integração em qualquer idioma é possível porque os compiladores de linguagens e ferramentas que segmentam o tempo de execução usam um Common Type System definido pelo tempo de execução e seguem as regras do tempo de execução para definir novos tipos, bem como para criar, usar, manter e associar a tipos.  
  
 Como parte de seus metadados, todos os componentes gerenciados transportam informações sobre os componentes e os recursos com base nos quais eles foram compilados. O tempo de execução usa essas informações para garantir que o componente ou o aplicativo tenha as versões especificadas de tudo o que precisa, o que torna seu código menos suscetível à interrupção devido a alguma dependência não atendida. As informações de registro e os dados de estado não são mais armazenados no registro onde pode ser difícil estabelecer e mantê-los. Em vez de isso, as informações sobre os tipos que você define (e suas dependências) são armazenadas com o código como metadados, fazendo com que as tarefas de replicação do componente e remoção sejam muito menos complicadas.  
  
 Compiladores de linguagens e ferramentas expõem a funcionalidade do tempo de execução da maneira como seriam úteis e intuitivas para desenvolvedores. Isso significa que alguns recursos do tempo de execução devem ser mais perceptíveis em um ambiente do que em outro. Como usa o tempo de execução depende de quais compiladores de linguagem ou ferramentas você usa. Por exemplo, se for um desenvolvedor do Visual Basic, você poderá observar que, com o Common Language Runtime, a linguagem do Visual Basic tem mais recursos orientados a objeto do que antes. O tempo de execução oferece os seguintes benefícios:  
  
-   Melhorias de desempenho.  
  
-   A possibilidade de usar facilmente componentes desenvolvidos em outras linguagens.  
  
-   Tipos extensíveis fornecidos por uma biblioteca de classes.  
  
-   Recursos de linguagem como herança, interfaces e sobrecarga para programação orientada ao objeto.  
  
-   Suporte a threading livre explícito que permite a criação de aplicativos multithread, escalonáveis.  
  
-   Suporte ao tratamento de exceções estruturado.  
  
-   Suporte a atributos personalizados.  
  
-   Coleta de lixo.  
  
-   Uso de delegados em vez de ponteiros de função para maior segurança e segurança de tipos. Para saber mais sobre representantes, veja [Common Type System](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="versions-of-the-common-language-runtime"></a>Versões do Common Language Runtime  
 O número de versão do .NET Framework não corresponde necessariamente ao número de versão do CLR que ele inclui. A tabela a seguir mostra como os dois números de versão se correlacionam.  
  
|Versão do .NET Framework|Inclui versão do CLR|  
|----------------------------|--------------------------|  
|1.0|1.0|  
|1.1|1.1|  
|2.0|2.0|  
|3.0|2.0|  
|3.5|2.0|  
|4|4|  
|4.5 (incluindo 4.5.1 e 4.5.2)|4|  
|4.6 (incluindo 4.6.1 e 4.6.2)|4|
|4.7|4|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Processo de execução gerenciada](../../docs/standard/managed-execution-process.md)|Descreve as etapas obrigatórias para usufruir o Common Language Runtime.|  
|[Gerenciamento Automático de Memória](../../docs/standard/automatic-memory-management.md)|Descreve como o coletor de lixo aloca e libera memória.|  
|[NIB: Visão geral do .NET Framework](http://msdn.microsoft.com/en-us/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|Descreve os conceitos-chave do .NET Framework, como Common Type System, interoperabilidade entre linguagens, execução gerenciada, domínios de aplicativos e assemblies.|  
|[Common Type System](../../docs/standard/base-types/common-type-system.md)|Descreve como os tipos são declarados, usados e gerenciados no tempo de execução para dar suporte à integração entre linguagens.|  
  
## <a name="see-also"></a>Consulte também  
 [Versões e dependências](../../docs/framework/migration-guide/versions-and-dependencies.md)
