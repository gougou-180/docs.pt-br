---
title: declarar e gerar eventos
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345097"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Instruções passo a passo: declarando e acionando eventos (Visual Basic)
Este tutorial demonstra como declarar e gerar eventos para uma classe chamada `Widget`. Depois de concluir as etapas, talvez você queira ler o tópico complementar, [Walkthrough: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.  
  
## <a name="the-widget-class"></a>A classe Widget  
 Suponha que, por enquanto, você tenha uma classe de `Widget`. Sua classe de `Widget` tem um método que pode levar muito tempo para ser executado e você deseja que seu aplicativo seja capaz de colocar algum tipo de indicador de conclusão.  
  
 É claro que você pode fazer com que o objeto `Widget` mostre uma caixa de diálogo de porcentagem concluída, mas, em seguida, você estaria preso a essa caixa de diálogo em todos os projetos nos quais usou a classe `Widget`. Um bom princípio do design de objeto é permitir que o aplicativo que usa um objeto manipule a interface do usuário — a menos que a finalidade do objeto seja gerenciar um formulário ou caixa de diálogo.  
  
 A finalidade do `Widget` é executar outras tarefas, portanto, é melhor adicionar um evento de `PercentDone` e permitir que o procedimento que chama os métodos de `Widget`manipule esse evento e exiba as atualizações de status. O evento `PercentDone` também pode fornecer um mecanismo para cancelar a tarefa.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Para criar o exemplo de código para este tópico  
  
1. Abra um novo projeto de aplicativo do Windows Visual Basic e crie um formulário chamado `Form1`.  
  
2. Adicione dois botões e um rótulo a `Form1`.  
  
3. Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Object|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Tarefa de início|  
    |`Button2`|`Text`|Cancel|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. No menu **projeto** , escolha **Adicionar classe** para adicionar uma classe chamada `Widget.vb` ao projeto.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Para declarar um evento para a classe Widget  
  
- Use a palavra-chave `Event` para declarar um evento na classe `Widget`. Observe que um evento pode ter argumentos `ByVal` e `ByRef`, como o evento de `PercentDone` de `Widget`demonstra:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Quando o objeto de chamada recebe um evento `PercentDone`, o argumento `Percent` contém a porcentagem da tarefa concluída. O argumento `Cancel` pode ser definido como `True` para cancelar o método que gerou o evento.  
  
> [!NOTE]
> Você pode declarar argumentos de evento da mesma forma como faz argumentos de procedimentos, com as seguintes exceções: os eventos não podem ter argumentos `Optional` ou `ParamArray`, e os eventos não têm valores de retorno.  
  
 O evento `PercentDone` é gerado pelo método `LongTask` da classe `Widget`. `LongTask` usa dois argumentos: o período de tempo que o método pretende a fazer funcionar e o intervalo de tempo mínimo antes de `LongTask` pausa para gerar o evento de `PercentDone`.  
  
#### <a name="to-raise-the-percentdone-event"></a>Para gerar o evento PercentDone  
  
1. Para simplificar o acesso à propriedade `Timer` usada por essa classe, adicione uma instrução `Imports` à parte superior da seção de declarações do seu módulo de classe, acima da instrução `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Adicione o seguinte código à classe `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Quando o aplicativo chama o método `LongTask`, a classe `Widget` gera o evento `PercentDone` a cada `MinimumInterval` segundos. Quando o evento retorna, `LongTask` verifica se o argumento `Cancel` foi definido como `True`.  
  
 Alguns isenções de responsabilidade são necessários aqui. Para simplificar, o procedimento `LongTask` pressupõe que você saiba com antecedência quanto tempo a tarefa levará. Esse é quase nunca o caso. Dividir tarefas em partes de tamanho par pode ser difícil e, muitas vezes, o que mais importa para os usuários é simplesmente a quantidade de tempo que o passa antes de receber uma indicação de que algo está acontecendo.  
  
 Você pode ter extratado outra falha neste exemplo. A propriedade `Timer` retorna o número de segundos que passaram desde a meia-noite; Portanto, o aplicativo ficará preso se ele for iniciado logo antes da meia-noite. Uma abordagem mais cuidadosa para medir o tempo teria condições de limite como essa em consideração ou evitá-las completamente, usando propriedades como `Now`.  
  
 Agora que a classe `Widget` pode gerar eventos, você pode ir para o próximo passo a passos. [Walkthrough: manipular eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de eventos ao evento `PercentDone`.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Instruções passo a passo: tratando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
