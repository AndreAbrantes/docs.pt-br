---
title: Assemblies e o cache de assembly global (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
ms.openlocfilehash: 6d1692d6b62e1f1f3a8f979d3de242003f034ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644245"
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Assemblies e o cache de assembly global (Visual Basic)
Os assemblies formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para um aplicativo baseado em .NET Framework. Os assemblies tomam a forma de um arquivo executável (.exe) ou de biblioteca de link dinâmico (.dll) e são os blocos de construção do .NET Framework. Eles oferecem ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo. Você pode pensar em um assembly como uma coleção de tipos e recursos que formam uma unidade lógica de funcionalidade e são criados para trabalharem juntos.  
  
 Os assemblies podem conter um ou mais módulos. Por exemplo, projetos maiores podem ser planejados de forma que vários desenvolvedores individuais trabalhem em módulos separados, todos juntos para criar um único assembly. Para obter mais informações sobre os módulos, consulte o tópico [Como compilar um Assembly de vários arquivos](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Os assemblies têm as seguintes propriedades:  
  
-   Assemblies são implementados como arquivos .dll ou .exe.  
  
-   Você pode compartilhar um assembly entre aplicativos colocando-o no cache de assembly global. Os assemblies devem ter nome forte antes de serem colocados no cache de assembly global. Para obter mais informações, consulte [Assemblies com nome forte](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Os assemblies serão carregados na memória somente se forem necessários. Se não forem usados, eles não serão carregados. Isso significa que os assemblies podem ser uma maneira eficiente de gerenciar recursos em projetos grandes.  
  
-   Você pode obter informações programaticamente sobre um assembly usando reflexão. Para obter mais informações, consulte [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Se deseja carregar um assembly somente para inspecioná-lo, use um método como <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifesto de um assembly  
 Dentro de todo assembly está um *manifesto do assembly*. Semelhante a um sumário, o manifesto do assembly contém o seguinte:  
  
-   A identidade do assembly (seu nome e versão).  
  
-   Uma tabela de arquivo que descreve todos os outros arquivos que compõem o assembly, por exemplo, quaisquer outros assemblies que você criou que seu arquivo .dll ou .exe depende, ou até mesmo arquivos bitmap ou Leiame.  
  
-   Um *lista de referências de assembly*, que é uma lista de todas as dependências externas, .dlls ou outros arquivos que seu aplicativo precisa e que podem ter sido criados por outra pessoa. As referências de assembly contêm referências a objetos globais e privados. Objetos globais residem no cache de assembly global, uma área disponível para outros aplicativos, um pouco semelhante ao diretório do System32. O namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType> é um exemplo de um assembly no cache de assembly global. Objetos privados devem estar em um diretório no mesmo nível ou abaixo do diretório no qual seu aplicativo está instalado.  
  
 Como os assemblies contêm informações sobre conteúdo, versão e dependências, os aplicativos criados com o Visual Basic não dependem de valores do Registro do Windows para funcionar corretamente. Os assemblies reduzem conflitos de .dll e tornam seus aplicativos mais confiáveis e mais fáceis de implantar. Em muitos casos, você pode instalar um aplicativo baseado em .NET simplesmente copiando seus arquivos para o computador de destino.  
  
 Para obter mais informações, consulte [Manifesto do assembly](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Adicionando uma referência a um assembly  
 Para usar um assembly, você deve adicionar uma referência a ele. Em seguida, use a [instrução Imports](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para escolher o namespace dos itens que você deseja usar. Quando um assembly é referenciado e importado, todas as classes acessíveis, propriedades, métodos e outros membros de seus namespaces estão disponíveis para o seu aplicativo como se seus códigos fossem parte de seu arquivo de origem.  
  
## <a name="creating-an-assembly"></a>Criando um assembly  
 Compile o aplicativo ao criá-lo da linha de comando usando o compilador de linha de comando. Para obter detalhes sobre como compilar assemblies da linha de comando, consulte [Compilando da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Para criar um assembly no Visual Studio, no menu **Compilar**, escolha **Compilar**.  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies no Common Language Runtime](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Assemblies amigáveis (Visual Basic)](friend-assemblies.md)  
 [Como: compartilhar um Assembly com outros aplicativos (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)  
 [Como: carregar e descarregar Assemblies (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [Como: determinar se um arquivo é um Assembly (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)  
 [Como: criar e usar Assemblies usando a linha de comando (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [Passo a passo: inserindo informações de tipo dos Microsoft Office Assemblies no Visual Studio (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
