---
title: Estratégia de segurança e engenharia
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: 57ee0c8242c0bca1b2c76e7751ed25f6a889c264
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741841"
---
# <a name="wpf-security-strategy---security-engineering"></a>Estratégia de segurança do WPF - engenharia de segurança
A Computação Confiável é uma iniciativa da Microsoft para garantir a produção de código seguro. Um elemento fundamental da iniciativa de computação confiável é o Microsoft Security Development Lifecycle (SDL). O SDL é uma prática de engenharia usada em conjunto com processos de engenharia padrão para facilitar a entrega de código seguro. O SDL consiste em dez fases que combinam as práticas recomendadas com a formalização, a mensurável e a estrutura adicional, incluindo:  
  
- Análise de projeto de segurança  
  
- Verificações de qualidade baseadas em ferramenta  
  
- Testes de penetração  
  
- Análise final de segurança  
  
- Gerenciamento de segurança do produto pós-lançamento  
  
## <a name="wpf-specifics"></a>Aspectos específicos do WPF  
 A equipe de engenharia de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplica e estende o SDL, a combinação do que inclui os seguintes aspectos principais:  
  
 [Modelagem de ameaças](#threat_modeling)  
  
 [Ferramentas de edição e análise de segurança](#tools)  
  
 [Técnicas de teste](#techniques)  
  
 [Gerenciamento de código crítico](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelagem de ameaças  
 A modelagem de ameaças é um componente fundamental do SDL e é usada para criar o perfil de um sistema para determinar possíveis vulnerabilidades de segurança. Após as vulnerabilidades serem identificadas, a modelagem de ameaças também garante que as atenuações apropriadas estejam em vigor.  
  
 De modo geral, a modelagem de ameaças envolve as seguintes etapas principais, usando uma mercearia como exemplo:  
  
1. **Identificando ativos**. Os ativos de uma mercearia podem incluir funcionários, um cofre, caixas e o inventário.  
  
2. **Enumerando pontos de entrada**. Os pontos de entrada de uma mercearia podem incluir as portas da frente e de trás, janelas, a estação de carga e as unidades de ar-condicionado.  
  
3. **Investigando ataques contra ativos usando pontos de entrada**. Um possível ataque poderia ter como alvo o ativo *cofre* de uma mercearia por meio do ponto de entrada *ar-condicionado*; a unidade de ar-condicionado poderia ser removida para permitir que o cofre seja passado por ela e retirado da mercearia.  
  
 A modelagem de ameaças é aplicada no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] e inclui o seguinte:  
  
- Como o analisador [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] lê arquivos, mapeia texto para classes de modelo de objeto correspondentes e cria o código real.  
  
- Como um identificador de janela (hWnd) é criado, envia mensagens e é usado para renderizar o conteúdo de uma janela.  
  
- Como a vinculação de dados obtém recursos e interage com o sistema.  
  
 Esses modelos de ameaças são importantes para identificar requisitos de design de segurança e reduções de ameaças durante o processo de desenvolvimento.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Ferramentas de edição e análise de código-fonte  
 Além dos elementos de revisão de código de segurança manual do SDL, a equipe de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usa várias ferramentas para análise de origem e edições associadas para diminuir as vulnerabilidades de segurança. Uma ampla variedade de ferramentas de código são usadas e incluem o seguinte:  
  
- **FXCop**: encontra problemas comuns de segurança no código gerenciado, que vão desde as regras de herança ao uso da segurança do acesso de código e a como interoperar com segurança com código não gerenciado. Consulte [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefix/Prefast**: localiza vulnerabilidades de segurança e problemas comuns de segurança em código não gerenciado, como saturações de buffer, problemas com cadeias de formatação e verificação de erros.  
  
- **APIs banidas**: pesquisa o código-fonte para identificar usos acidentais de funções que são conhecidas por causar problemas de segurança, como `strcpy`. Depois de identificado, essas funções são substituídas por alternativas que são mais seguras.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Técnicas de teste  
 O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usa uma variedade de técnicas teste de segurança que incluem:  
  
- **Teste de whitebox**: os testadores exibem o código-fonte e criam testes de exploração.
  
- **Testes caixa preta**: os testadores tentam localizar falhas de segurança examinando as API e os recursos e, em seguida, tentam atacar o produto.  
  
- **Regressão de problemas de segurança de outros produtos**: quando for relevante, problemas de segurança de produtos relacionados serão testados. Por exemplo, as variantes apropriadas de aproximadamente 60 problemas de segurança para o Internet Explorer foram identificadas e tentaram sua aplicabilidade a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
- **Testes de penetração baseados em ferramentas por meio de fuzzing de arquivos**: fuzzing de arquivos é a exploração do intervalo de entradas de um leitor de arquivos por meio de uma variedade de entradas. Um exemplo de uso dessa técnica no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] é para verificar se há falhas no código de decodificação de imagens.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Gerenciamento de código crítico  
 Para aplicativos de navegador XAML (XBAPs), o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] cria uma área restrita de segurança usando .NET Framework suporte para marcação e acompanhamento de código de segurança crítica que eleva privilégios (consulte **metodologia de segurança crítica** na [estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)). Considerando os altos requisitos de qualidade da segurança em códigos críticos para a segurança, esse código recebe um nível adicional de auditoria de segurança e controle de gerenciamento de código-fonte. Aproximadamente 5% a 10% do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consiste em código crítico para a segurança, que é revisado por uma equipe de revisão dedicada. O código-fonte e o processo de check-in são gerenciados acompanhando o código crítico para segurança e mapeando cada entidade crítica (isto é, um método que contém código crítico) quanto ao seu estado de aprovação. O estado de aprovação inclui os nomes de um ou mais revisores. Cada build diária de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compara o código crítico com o dos builds anteriores para verificar se há alterações não aprovadas. Se um engenheiro modificar o código crítico sem a aprovação da equipe de revisão, isso será identificado e corrigido imediatamente. Esse processo permite a aplicação e a manutenção de um nível especialmente alto de investigação do código na área restrita [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Veja também

- [Security](security-wpf.md)
- [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Computação confiável](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Segurança no .NET](../../standard/security/index.md)
