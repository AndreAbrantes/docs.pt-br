---
title: "Programação com funcional. Programação imperativa (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 6a1f3b57-00e6-447d-9906-74c7c4d5d85c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7fd7a2defabe2d03b658977cc0106e3bbf985202
ms.lasthandoff: 03/13/2017


---
# <a name="functional-programming-vs-imperative-programming-visual-basic"></a>Programação com funcional. Programação imperativa (Visual Basic)
Este tópico compara e contrasta programação funcional com programação (procedural) imperativa mais tradicional.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Programação com funcional. Programação imperativa  
 O *programação funcional* paradigma explicitamente foi criado para oferecer suporte a uma abordagem funcional pura a resolução de problemas. Programação funcional é uma forma de *programação declarativa*. Por outro lado, a maioria dos idiomas principais, incluindo orientada a objeto (OOP) linguagens de programação como c#, Visual Basic, C++ e Java, foram projetados para suportar primeiro *imperativa* programação (procedural).  
  
 Com uma abordagem imperativa, um desenvolvedor escreve o código que descreve detalhadamente exigente as etapas que o computador deve executar para fazer o objetivo. Às vezes, isso é conhecido como *algorítmica* de programação. Por outro lado, uma abordagem funcional envolve compõem o problema como um conjunto de funções a ser executadas. Você define cuidadosamente entrada a cada função, e o que cada função retorna. A tabela a seguir descreve algumas das diferenças gerais entre essas duas abordagens.  
  
|Característica|Abordagem imperativa|Abordagem funcional|  
|--------------------|-------------------------|-------------------------|  
|Foco do programador|Como executar tarefas (algoritmos) e como controlar alterações no estado.|Informações que é desejada e que transformações são necessárias.|  
|Alterações de estado|Importante.|Inexistente.|  
|Ordem de execução|Importante.|Baixa importância.|  
|Controle de fluxo primária|Loop, condições, e chamadas de função (método).|Chamadas de função, incluindo a recursão.|  
|Unidade principal de manipulação|Instâncias das classes ou estruturas.|Funções como objetos de primeira classe e coleções de dados.|  
  
 Embora a maioria das linguagens sejam criados para oferecer suporte a um paradigma específico de programação, vários idiomas gerais é flexível o suficiente para suportar várias paradigma. Por exemplo, a maioria das linguagens que contêm ponteiros de função podem ser usados para oferecer suporte digna de crédito programação funcional. Além disso, o Visual Basic inclui extensões de linguagem explícitas para dar suporte à programação funcional, incluindo expressões lambda e Inferência de tipos. A tecnologia LINQ é um formulário de programação declarativa, funcional.  
  
## <a name="functional-programming-using-xslt"></a>Programação funcional usando XSLT  
 Muitos desenvolvedores XSLT estão familiarizados com a abordagem funcional pura. A maioria de modo eficiente desenvolver uma folha de estilos XSLT é manipular cada modelo como uma transformação isolado, passível de composição. A ordem de execução de- é completamente sublinhado. XSLT não permite efeitos colaterais (exceto mecanismos de escape para executar o código procedural pode gerar os efeitos colaterais que resultam na impureza funcional). No entanto, embora XSLT é uma ferramenta eficaz, algumas de suas características não são ótimas. Por exemplo, expressar construções de programação em XML torna o código relativamente detalhado, e portanto difícil manter. Além disso, confiança pesada na recursão para o controle de fluxo pode resultar em código que é difícil de ler. Para obter mais informações sobre XSLT, consulte [transformações XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03).  
  
 No entanto, XSLT provou o valor de usar uma abordagem funcional pura para transformar XML de uma forma para outra. Programação funcional pura com LINQ to XML é semelhante de várias maneiras a fonte. No entanto, as construções de programação introduzidas por LINQ to XML e Visual Basic permitem que você escrever transformações e puras que são mais legíveis e sustentável de fonte.  
  
## <a name="advantages-of-pure-functions"></a>Vantagens de funções puras  
 O principal motivo para implementar transformações e como funções puras é que as funções puras são passível de composição: isto é, independentemente e sem estado. Essas características trazem um número de benefícios, incluindo o seguinte:  
  
-   Legibilidade e sustentabilidade aumentadas. Isso ocorre porque cada função é criada para realizar uma tarefa específica determinada seus argumentos. A função não confiar em qualquer estado externo.  
  
-   Desenvolvimento reiterative mais fácil. Porque o código é mais fácil refatorar, alterações no design são geralmente mais fácil de implementar. Por exemplo, suponha o escrever uma transformação complicada, e realize-o em que qualquer código é repetido várias vezes na transformação. Se você refatora com um método puro, você pode chamar o método puro na vontade sem se preocupar sobre efeitos colaterais.  
  
-   Teste e depuração mais fácil. Como as funções puras podem acessar mais facilmente seja testado no isolamento, você pode escrever código de teste que chama a função pura com valores típicos, caso válidos de borda casos, e inválidas de borda.  
  
## <a name="transitioning-for-oop-developers"></a>Fazer a transição para OOP desenvolvedores  
 Em programação orientada a objeto tradicional (OOP), a maioria dos desenvolvedores estão acostumados a programação estilo obrigatório/procedural. Para alternar a ficar em um estilo funcional puro, eles precisam fazer uma transição no seu pensamento e a abordagem ao desenvolvimento.  
  
 Para resolver problemas, OOP hierarquias de classe de design de desenvolvedores, centram-se sobre encapsulamento apropriada, e pensam-se em termos de contratos de classe. O comportamento e o estado dos tipos de objeto são primordiais, e os recursos de linguagem, como classes, interfaces, herança, herança e polimorfismo, são fornecidos para resolver esses interesses.  
  
 Por outro lado, a programação funcional aproxima problemas computacionais como um exercício a avaliação de transformações e puras de coleções de dados. Programação funcional evita o estado e dados mutáveis, e sublinha ao aplicativo de funções.  
  
 Felizmente, o Visual Basic não requerem o pulo completo para programação funcional, porque ele oferece suporte a métodos de programação imperativos e funcionais. Um desenvolvedor pode escolher qual abordagem é a mais adequado para um cenário específico. De fato, os programas combinam geralmente as duas abordagens.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações e puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Transformações XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)   
 [Refatoração em funções puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
