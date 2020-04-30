---
title: Fluxos de trabalho do computador de estado
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 12f6383a52c7eaf0d66ce6680f66a5df0b314dfd
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595930"
---
# <a name="state-machine-workflows"></a>Fluxos de trabalho do computador de estado
Um computador de estado é um paradigma conhecido para programas desenvolvimento. A atividade de <xref:System.Activities.Statements.StateMachine> , juntamente com <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, e outras atividades pode ser usada para criar programas de fluxo de trabalho do computador de estado. Este tópico fornece uma visão geral de criar fluxos de trabalho do computador de estado.  
  
## <a name="state-machine-workflow-overview"></a>Visão geral de fluxo de trabalho do computador de estado  
 Fluxos de trabalho do computador de estado fornecem um estilo modelagem com que você pode modelar seu fluxo de trabalho em uma maneira de baseada. Uma atividade de <xref:System.Activities.Statements.StateMachine> contém os estados e as transições que compõem a lógica do computador de estado, e pode ser usada em qualquer lugar uma atividade pode ser usada. Há várias classes no runtime do computador de estado:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Para criar um fluxo de trabalho de máquina de estado, os <xref:System.Activities.Statements.StateMachine> Estados são adicionados a uma atividade e as transições são usadas para controlar o fluxo entre os Estados. A captura de tela a seguir, da etapa [introdução tutorial](getting-started-tutorial.md) [como criar um fluxo de trabalho de máquina de estado](how-to-create-a-state-machine-workflow.md), mostra um fluxo de trabalho de máquina de estado com três Estados e três transições. **Inicializar destino** é o estado inicial e representa o primeiro estado no fluxo de trabalho. Isso é designado pela linha que a leva para o nó **inicial** . O estado final no fluxo de trabalho é chamado de **FinalState**e representa o ponto no qual o fluxo de trabalho é concluído.  
  
 ![Ilustração que mostra o fluxo de trabalho da máquina de estado concluído.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Um fluxo de trabalho do computador de estado deve ter um e somente um estados iniciais, e pelo menos um estados finais. Cada estado que não é um estado final deve ter pelo menos uma transição. As seções a seguir abordam como criar e configurar de estados e das transições.  
  
## <a name="creating-and-configuring-states"></a>Criando e configurando estados  
 <xref:System.Activities.Statements.State> representa um estado em que um computador de estado pode estar. Para adicionar um <xref:System.Activities.Statements.State> a um fluxo de trabalho, arraste o designer de atividade de **estado** da seção **máquina de estado** da **caixa** de ferramentas <xref:System.Activities.Statements.StateMachine> e solte-o em uma atividade na superfície de designer de fluxo de trabalho do Windows.  
  
 ![Captura de tela da seção máquina de estado da caixa de ferramentas.](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Para configurar um estado como o **estado inicial**, clique com o botão direito do mouse no estado e selecione **definir como estado inicial**. Além disso, se não houver nenhum estado inicial atual, o estado inicial poderá ser designado arrastando-se uma linha do nó **inicial** na parte superior do fluxo de trabalho até o estado desejado. Quando uma <xref:System.Activities.Statements.StateMachine> atividade é descartada no designer de fluxo de trabalho, ela é pré-configurada com um estado inicial chamado **State1**. Um fluxo de trabalho do computador de estado deve ter um e somente um estados iniciais.  
  
 Um estado que representa um estado de terminação em um computador de estado é chamado um estado final. Um estado final é um estado que tem sua propriedade de <xref:System.Activities.Statements.State.IsFinal%2A> definida como `true`, não tem nenhuma atividade de <xref:System.Activities.Statements.State.Exit%2A> , e nenhuma transição que se origina delas. Para adicionar um estado final a um fluxo de trabalho, arraste um designer de atividades **FinalState** da seção **máquina de estado** da **caixa de ferramentas** e <xref:System.Activities.Statements.StateMachine> solte-o em uma atividade na superfície de designer de fluxo de trabalho do Windows. Um fluxo de trabalho do computador de estado deve ter pelo menos um estado final.  
  
### <a name="configuring-entry-and-exit-actions"></a>Configurando ações de entrada e de saída  
 Um estado pode ter <xref:System.Activities.Statements.State.Entry%2A> e uma ação de <xref:System.Activities.Statements.State.Exit%2A> . (O estado de configurado como um estado final pode ter apenas uma ação de entrada). Quando uma instância de fluxo de trabalho entra em um estado, todas as atividades em ação de entrada são executadas. Quando a ação de entrada estiver concluída, disparadores para as transições de estado estão agendados. Quando uma transição para outro estado é confirmada, as atividades em ação de saída são executadas, mesmo se o estado faz a transição de volta ao mesmo estado. Depois que a ação de saída for concluída, as atividades em ação de transição, e executam o novo estado é feito à transição, e suas ações de entrada são agendadas.  
  
> [!NOTE]
> Para depurar um fluxo de trabalho do computador de estado, pontos de interrupção podem ser colocados na atividade e os estados do computador de estado da raiz no fluxo de trabalho do computador de estado. Os pontos de interrupção não podem ser colocados diretamente nas transições, mas podem ser colocados em todas as atividades contidas nos estados e as transições.  
  
## <a name="creating-and-configuring-transitions"></a>Criando e configurando as transições  
 Todos os estados devem ter pelo menos uma transição, exceto para um estado final que não tenha nenhuma transições. Transições podem ser adicionadas após um estado é adicionado a um fluxo de trabalho do computador de estado, ou podem ser criadas como o estado são soltas.  
  
 Para adicionar um <xref:System.Activities.Statements.State> e criar uma transição em uma única etapa, arraste uma atividade de **estado** da seção **máquina de estado** da **caixa de ferramentas** e passe o mouse sobre outro Estado no designer de fluxo de trabalho. Quando <xref:System.Activities.Statements.State> arrastado está sobre um outro <xref:System.Activities.Statements.State>, quatro triângulos aparecerão em torno do outro <xref:System.Activities.Statements.State>. Se <xref:System.Activities.Statements.State> é solto em um dos quatro triângulos, é adicionado ao computador de estado e uma transição é criada de origem <xref:System.Activities.Statements.State> ao destino solto <xref:System.Activities.Statements.State>. Para obter mais informações, consulte o [Designer de atividade de transição](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Para criar uma transição após um estado é adicionado, existem duas opções. A primeira opção é arraste o estado da superfície do designer de fluxo de trabalho e focalizar-lo sobre um estado existente e solte-o em um dos pontos da operação. Isso é muito semelhante ao método descrito na seção anterior. Você pode também passa o mouse sobre o estado desejado de origem, e arraste uma linha para o estado desejado de destino.  
  
> [!NOTE]
> Um único estado em um computador de estado pode ter até 76 transições criadas utilizando o designer de fluxo de trabalho. O limite nas transições para um estado para fluxos de trabalho criados fora de designer é delimitado somente por recursos do sistema.  
  
 Uma transição pode ter <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>, e <xref:System.Activities.Statements.Transition.Action%2A>. <xref:System.Activities.Statements.Transition.Trigger%2A> de uma transição é agendada quando a ação de <xref:System.Activities.Statements.State.Entry%2A> de estado da fonte de transição é concluída. Normalmente <xref:System.Activities.Statements.Transition.Trigger%2A> é uma atividade que espera qualquer tipo de evento ocorra, mas pode ser qualquer atividade, ou nenhuma atividade de todo. Uma vez que a atividade de <xref:System.Activities.Statements.Transition.Trigger%2A> estiver concluída, <xref:System.Activities.Statements.Transition.Condition%2A>, se presentes, é avaliada. Se não houver nenhuma atividade de <xref:System.Activities.Statements.Transition.Trigger%2A> em <xref:System.Activities.Statements.Transition.Condition%2A> é avaliado imediatamente. Se a condição for avaliada como `false`, a transição é cancelada, e quaisquer atividades de <xref:System.Activities.Statements.Transition.Trigger%2A> para faz a transição de estado é reprogramada. Se existem outras transições que compartilham o mesmo estado de origem que a transição atual, essas ações de <xref:System.Activities.Statements.Transition.Trigger%2A> são canceladas e reprogramadas também. Se <xref:System.Activities.Statements.Transition.Condition%2A> avalia a `true`, ou não há nenhuma condição, então a ação de <xref:System.Activities.Statements.State.Exit%2A> de estado de origem é executada, e <xref:System.Activities.Statements.Transition.Action%2A> de transição é executado em seguida. Quando o <xref:System.Activities.Statements.Transition.Action%2A> é concluído, o controle passa para o estado de **destino**  
  
 Faz a transição que compartilham um disparador comum é conhecido como o disparador compartilhado transições. Cada transição em um grupo de transições compartilhadas do disparador tem o mesmo disparador, mas <xref:System.Activities.Statements.Transition.Condition%2A> e uma ação exclusivos. Para adicionar ações adicionais para uma transição e criar uma transição compartilhada, clique no círculo que indica o início de transição desejada e arraste-o para estado desejado. A nova transição compartilhar um disparador mesmo que a transição inicial, mas terá uma condição e uma ação exclusivos. As transições compartilhadas também podem ser criadas de dentro do designer de transição clicando em **Adicionar transição de gatilho compartilhado** na parte inferior do designer de transição e, em seguida, selecionando o estado de destino desejado na lista suspensa **Estados disponíveis para conexão** .  
  
> [!NOTE]
> Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `False` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `False`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados.  
  
 Para obter mais informações sobre como criar fluxos de trabalho de máquina de estado, consulte [como criar um fluxo de trabalho de máquina de estado](how-to-create-a-state-machine-workflow.md), [StateMachine designer de atividade](/visualstudio/workflow-designer/statemachine-activity-designer), designer de atividade de [estado](/visualstudio/workflow-designer/state-activity-designer), [Designer de atividade FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)e designer de atividade de [transição](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologia do computador de estado  
 Esta seção define o vocabulário do computador de estado usado em todo este tópico.  
  
 Estado  
 A unidade básica que compõem um computador de estado. Um computador de estado pode estar em um estado em todas as hora.  
  
 Ação de entrada  
 Uma atividade executada ao inserir no estado  
  
 Ação de saída  
 Uma atividade executada quando deixar o estado  
  
 Transição  
 Direcionada uma relação entre dois estados que representa a resposta completo de um computador de estado para uma ocorrência de um evento de um tipo específico.  
  
 Transição compartilhada  
 Uma transição que compartilhar um estado de origem e o disparador com um ou mais faz a transição, mas tem uma condição e uma ação exclusivos.  
  
 Gatilho  
 Uma atividade disparando que faz com que uma transição ocorre.  
  
 Condição  
 Uma restrição que deve ser avaliada como `true` após o disparador ocorre a transição para que ela seja concluída.  
  
 Ação de transição  
 Uma atividade que é executada ao executar alguma transição.  
  
 Transição condicional  
 Uma transição com uma condição explícita.  
  
 Dica transição  
 Uma transição que transite por de um estado para se.  
  
 Estado Inicial  
 Um estado que representa o ponto de partida do computador de estado.  
  
 Estado final  
 Um estado que representa a conclusão do computador de estado.  
  
## <a name="see-also"></a>Confira também

- [Como criar um fluxo de trabalho de máquina de estado](how-to-create-a-state-machine-workflow.md)
- [Designer de atividade StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)
- [Designer de atividade de estado](/visualstudio/workflow-designer/state-activity-designer)
- [Designer de atividade FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Fazer a transição o designer de atividades](/visualstudio/workflow-designer/transition-activity-designer)
