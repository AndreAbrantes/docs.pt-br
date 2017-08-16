---
title: 'Passo a passo: Chamando APIs do Windows (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls, walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement, declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5001ccebb0a5b8cadd4e856342601506cf1d033f
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Instruções passo a passo: chamando APIs do Windows (Visual Basic)
APIs do Windows são bibliotecas de vínculo dinâmico (DLLs) que fazem parte do sistema operacional Windows. Você pode usá-los para executar tarefas quando é difícil escrever procedimentos equivalentes de sua preferência. Por exemplo, o Windows fornece uma função chamada `FlashWindowEx` que permite que você crie a barra de título para um aplicativo alternativo entre tonalidades claras e escuras.  
  
 A vantagem de usar APIs do Windows em seu código é que elas podem economizar tempo de desenvolvimento porque eles contêm dezenas de funções úteis que já estão gravadas e esperando para ser usado. A desvantagem é que APIs do Windows pode ser difícil trabalhar com e implacável quando as coisas dão errado.  
  
 APIs do Windows representam uma categoria especial de interoperabilidade. APIs do Windows não usar código gerenciado, não têm interno bibliotecas de tipos e usar tipos de dados que são diferentes daqueles usados com o Visual Studio. Devido a essas diferenças, e como APIs do Windows não são objetos COM, interoperabilidade com APIs do Windows e o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] é realizada usando a plataforma invoke, ou PInvoke. Invocação de plataforma é um serviço que permite que código gerenciado para chamar funções não gerenciadas implementadas em DLLs. Para obter mais informações, consulte [consumindo funções de DLL não gerenciada](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045). Você pode usar PInvoke em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usando o `Declare` instrução ou aplicar o `DllImport` atributo a um procedimento vazio.  
  
 Chamadas de API do Windows foram uma parte importante da [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programação no passado, mas raramente são necessárias com [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]. Sempre que possível, você deve usar código gerenciado do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] para executar tarefas, em vez de chamadas de API do Windows. Este passo a passo fornece informações sobre as situações nas quais o uso APIs do Windows é necessária.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="api-calls-using-declare"></a>Chamadas de API usando Declare  
 É a maneira mais comum de chamar APIs do Windows usando o `Declare` instrução.  
  
#### <a name="to-declare-a-dll-procedure"></a>Para declarar um procedimento DLL  
  
1.  Determine o nome da função que você deseja chamar, mais seus argumentos, tipos de argumento e retornar o valor, bem como o nome e o local da DLL que contém.  
  
    > [!NOTE]
    >  Para obter informações completas sobre as APIs do Windows, consulte a documentação do SDK do Win32 na API do Windows Platform SDK. Para obter mais informações sobre as constantes que usam APIs do Windows, examine os arquivos de cabeçalho, como Windows. h incluído no SDK da plataforma.  
  
2.  Abra um novo projeto de aplicativo do Windows clicando em **novo** no **arquivo** menu e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
3.  Selecione **Windows Application** da lista de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelos de projeto. O novo projeto é exibido.  
  
4.  Adicione o seguinte `Declare` função para a classe ou módulo no qual você deseja usar a DLL:  
  
     [!code-vb[VbVbalrInterop n º&9;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Partes da instrução Declare  
 O `Declare` instrução inclui os seguintes elementos.  
  
#### <a name="auto-modifier"></a>Modificador auto  
 O `Auto` modificador instrui o runtime a converter a cadeia de caracteres com base no nome do método de acordo com regras de tempo de execução de linguagem comum (ou alias se especificado).  
  
#### <a name="lib-and-alias-keywords"></a>Palavras-chave lib e Alias  
 O nome após o `Function` palavra-chave é o nome que seu programa usa para acessar a função importada. Pode ser o mesmo que o nome real da função que você está chamando, ou você pode usar qualquer nome válido de procedimento e, em seguida, utilize o `Alias` palavra-chave para especificar o nome real da função que você está chamando.  
  
 Especifique o `Lib` palavra-chave, seguido do nome e local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para arquivos localizados nos diretórios do sistema Windows.  
  
 Use o `Alias` palavra-chave se o nome da função que você está chamando não é válido [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] nome do procedimento ou está em conflito com o nome de outros itens em seu aplicativo. `Alias`indica o nome da função que está sendo chamado.  
  
#### <a name="argument-and-data-type-declarations"></a>Argumento e declarações de tipo de dados  
 Declare os argumentos e seus tipos de dados. Esta parte pode ser desafiadora porque os tipos de dados que o Windows usa não correspondem aos tipos de dados do Visual Studio. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz muito do trabalho ao converter argumentos para tipos de dados compatíveis, um processo chamado *empacotamento*. Você pode controlar explicitamente como argumentos são empacotados usando o <xref:System.Runtime.InteropServices.MarshalAsAttribute>atributo definido no <xref:System.Runtime.InteropServices>namespace.</xref:System.Runtime.InteropServices> </xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
> [!NOTE]
>  Versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permitido declarar parâmetros `As Any`, que significa que os dados de qualquer dado tipo pode ser usado. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]requer que você use um tipo de dados específico para todas as `Declare` instruções.  
  
#### <a name="windows-api-constants"></a>Constantes de API do Windows  
 Alguns argumentos são combinações de constantes. Por exemplo, o `MessageBox` API mostrado neste passo a passo aceita um argumento integer chamado `Typ` que controla como a caixa de mensagem é exibida. Você pode determinar o valor numérico de constantes examinando o `#define` instruções no arquivo WinUser. H. Os valores numéricos geralmente são mostrados em hexadecimal, portanto você pode usar uma calculadora para adicioná-los e converter em decimal. Por exemplo, se você desejar combinar as constantes para o estilo de exclamação `MB_ICONEXCLAMATION` 0x00000030 e Sim/não estilo `MB_YESNO` 0x00000004, você pode adicionar os números e obter um resultado de 0x00000034, ou 52 decimal. Embora você possa usar diretamente o resultado decimal, é melhor declarar esses valores como constantes em seu aplicativo e combiná-los usando o `Or` operador.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Para declarar constantes para chamadas de API do Windows  
  
1.  Consulte a documentação para a função do Windows que você está chamando. Determine o nome de constantes que são usadas e o nome do arquivo. h que contém os valores numéricos para constantes.  
  
2.  Use um editor de texto, como o bloco de notas, para exibir o conteúdo do arquivo de cabeçalho (. h) e localizar os valores associados às constantes que você está usando. Por exemplo, o `MessageBox` API usa a constante `MB_ICONQUESTION` para mostrar um ponto de interrogação na caixa de mensagem. A definição de `MB_ICONQUESTION` está na WinUser. H e aparece da seguinte maneira:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Adicionar equivalente `Const` instruções à sua classe ou módulo para tornar essas constantes disponíveis para seu aplicativo. Por exemplo:  
  
     [!code-vb[VbVbalrInterop n º&11;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>Para chamar o procedimento DLL  
  
1.  Adicione um botão chamado `Button1` para a inicialização do formulário para o seu projeto e, em seguida, clique duas vezes nele para exibir seu código. O manipulador de eventos para o botão é exibido.  
  
2.  Adicione código para o `Click` manipulador de eventos para o botão é adicionado, para chamar o procedimento e forneça os argumentos apropriados:  
  
     [!code-vb[VbVbalrInterop&#12;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Execute o projeto pressionando F5. A caixa de mensagem é exibida com as **Sim** e **não** botões de resposta. Clique em qualquer um.  
  
#### <a name="data-marshaling"></a>Marshaling de dados  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]automaticamente converte os tipos de dados de parâmetros e valores de retorno para chamadas de API do Windows, mas você podem usar o `MarshalAs` atributo para especificar os tipos de dados não gerenciados que esperam uma API explicitamente. Para obter mais informações sobre empacotamento de interoperabilidade, consulte [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Para usar Declare e MarshalAs em uma chamada de API  
  
1.  Determinar o nome da função que você deseja chamar, mais seus argumentos, tipos de dados, e o valor de retorno.  
  
2.  Para simplificar o acesso para o `MarshalAs` de atributo, adicione um `Imports` à parte superior do código para a classe ou módulo, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Adicione um protótipo de função para a função importada para a classe ou módulo que você está usando e aplica o `MarshalAs` atributo aos parâmetros ou valor de retorno. No exemplo a seguir, uma chamada de API que espera que o tipo `void*` é empacotada como `AsAny`:  
  
     [!code-vb[VbVbalrInterop&#14;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>Chamadas de API usando DllImport  
 O `DllImport` atributo fornece uma segunda maneira para chamar funções em DLLs sem bibliotecas de tipos. `DllImport`é aproximadamente equivalente a usar um `Declare` instrução mas oferece mais controle sobre como as funções são chamadas.  
  
 Você pode usar `DllImport` com a API do Windows a maioria das chamadas, desde a chamada se refira a um compartilhado (às vezes chamado de *estático*) método. Você não pode usar os métodos que requerem uma instância de uma classe. Ao contrário de `Declare` instruções, `DllImport` chamadas não é possível usar o `MarshalAs` atributo.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Para chamar uma API do Windows usando o atributo DllImport  
  
1.  Abra um novo projeto de aplicativo do Windows clicando em **novo** no **arquivo** menu e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione **Windows Application** da lista de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelos de projeto. O novo projeto é exibido.  
  
3.  Adicione um botão chamado `Button2` para o formulário de inicialização.  
  
4.  Clique duas vezes em `Button2` para abrir o modo de exibição de código para o formulário.  
  
5.  Para simplificar o acesso ao `DllImport`, adicione um `Imports` à parte superior do código para a classe de formulário de inicialização:  
  
     [!code-vb[VbVbalrInterop&13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Declarar uma função vazia que precede o `End Class` instrução para o formulário e nomeie a função `MoveFile`.  
  
7.  Aplicar o `Public` e `Shared` modificadores à função de declaração e definir parâmetros para `MoveFile` com base nos argumentos que função API do Windows usa:  
  
     [!code-vb[VbVbalrInterop n º&16;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Sua função pode ter qualquer nome válido de procedimento; o `DllImport` atributo especifica o nome na DLL. Ele também trata interoperabilidade de empacotamento para os parâmetros e a API usa tipos de valores de retorno, assim você pode escolher os tipos de dados do Visual Studio que são semelhantes aos dados.  
  
8.  Aplicar o `DllImport` atributo à função vazia. O primeiro parâmetro é o nome e o local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para arquivos localizados nos diretórios do sistema Windows. O segundo parâmetro é um argumento nomeado que especifica o nome da função da API do Windows. Neste exemplo, o `DllImport` atributo força chamadas para `MoveFile` sejam encaminhados para `MoveFileW` em KERNEL32. DLL. O `MoveFileW` método copia um arquivo do caminho de `src` para o caminho `dst`.  
  
     [!code-vb[17 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Adicione código para o `Button2_Click` manipulador de eventos para chamar a função:  
  
     [!code-vb[VbVbalrInterop n º&18;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Crie um arquivo chamado Test. txt e coloque-na pasta C:\Tmp em seu disco rígido. Crie a pasta Tmp, se necessário.  
  
11. Pressione F5 para iniciar o aplicativo. O formulário principal é exibido.  
  
12. Clique em **Button2**. A mensagem "o arquivo foi movido com êxito" será exibida se o arquivo pode ser movido.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Automático](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Criando protótipos em código gerenciado](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)   
 [Empacotamento de um delegado como um método de retorno de chamada](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)
