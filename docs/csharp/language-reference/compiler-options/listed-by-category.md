---
title: Opções do compilador de C# listadas por categoria
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972715"
---
# <a name="c-compiler-options-listed-by-category"></a>Opções do compilador de C# listadas por categoria

As opções do compilador a seguir são classificadas por categoria. Para obter uma lista alfabética, consulte [Opções do compilador C# listadas em ordem alfabética](listed-alphabetically.md).

## <a name="optimization"></a>Optimization

|Opção|Finalidade|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Especifica o tamanho das seções no arquivo de saída.|
|[-otimizar](optimize-compiler-option.md)|Habilita/desabilita otimizações.|

## <a name="output-files"></a>Arquivos de saída

|Opção|Finalidade|
|------------|-------------|
|[-determinista](deterministic-compiler-option.md)|Faz com que o compilador gere um assembly de conteúdo binário idêntico entre compilações se as entradas são idênticas.|
|[-doc](doc-compiler-option.md)|Especifica um arquivo XML em que os comentários da documentação processados devem ser gravados.|
|[-fora](out-compiler-option.md)|Especifica o arquivo de saída.|
|[-pathmap](pathmap-compiler-option.md)|Especificar um mapeamento para os nomes de caminho de origem emitidos pelo compilador|
|[-pdb](pdb-compiler-option.md)|Especifica o nome de arquivo e a localização do arquivo .pdb.|
|[-plataforma](platform-compiler-option.md)|Especifique a plataforma de saída.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Especifique uma linguagem para a saída do compilador.|
|[-refout](refout-compiler-option.md)|Gere um assembly de referência além de um assembly principal.|
|[-refonly](refonly-compiler-option.md)|Gere um assembly de referência em vez de um assembly principal.|
|[-alvo](target-compiler-option.md)|Especifica o formato do arquivo de saída usando uma das cinco opções: [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md) ou [-target:winmdobj](target-winmdobj-compiler-option.md).|
|/modulename:\<string>|Especificar o nome do módulo de origem|

## <a name="net-framework-assemblies"></a>Assemblies do .NET Framework

|Opção|Finalidade|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Especifica um ou mais módulos para fazerem parte deste assembly.|
|[-sinal de atraso](delaysign-compiler-option.md)|Instrui o compilador a adicionar a chave pública, mas a deixar o assembly não assinado.|
|[-contêiner de chaves](keycontainer-compiler-option.md)|Especifica o nome do contêiner da chave de criptografia.|
|[-arquivo-chave](keyfile-compiler-option.md)|Especifica o nome de arquivo que contém a chave de criptografia.|
|[-lib](lib-compiler-option.md)|Especifica a localização dos conjuntos referenciados por meio de [referência](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Instrui o compilador a não importar a biblioteca padrão (mscorlib.dll).|
|[-sinal público](publicsign-compiler-option.md)|Aplicar uma chave pública sem assinar o assembly, mas definir o bit no assembly indicando que o assembly está assinado.|
|[-referência](reference-compiler-option.md)|Importa metadados de um arquivo que contém um assembly.|
|-analyzer|Executar os analisadores com basse nesse assembly (forma abreviada: /a)|
|-additionalfile|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|
|-embed|Insere todos os arquivos de origem no PDB.|
|-embed:\<file list>|Insere arquivos específicos no PDB.|
## <a name="debuggingerror-checking"></a>Verificação de depuração/erros

|Opção|Finalidade|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|
|[-verificado](checked-compiler-option.md)|Especifica se o aritmético inteiro que estoura os limites do tipo de dados causará uma exceção em tempo de execução.|
|[-depuração](debug-compiler-option.md)|Instrua o compilador a emitir informações de depuração.|
|[-Relatório de erros](errorreport-compiler-option.md)|Define o comportamento de relatório de erros.|
|[-fullpaths](fullpaths-compiler-option.md)|Especifica o caminho absoluto para o arquivo na saída do compilador.|
|[-nowarn](nowarn-compiler-option.md)|Suprime a geração de avisos especificados do compilador.|
|[-avisar](warn-compiler-option.md)|Define o nível de aviso.|
|[-warnaserror](warnaserror-compiler-option.md)|Promove avisos a erros.|
|-ruleset:\<file>|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|

## <a name="preprocessor"></a>Pré-processador

|Opção|Finalidade|
|------------|-------------|
|[-definir](define-compiler-option.md)|Define símbolos do pré-processador.|

## <a name="resources"></a>Recursos

|Opção|Finalidade|
|------------|-------------|
|[-link](link-compiler-option.md)|Disponibiliza informações de tipo COM em assemblies especificados para o projeto.|
|[-linkresource](linkresource-compiler-option.md)|Cria um link a um recurso gerenciado.|
|[-recurso](resource-compiler-option.md)|Insere um recurso do .NET Framework no arquivo de saída.|
|[-win32icon](win32icon-compiler-option.md)|Especifica um arquivo .ico a ser inserido no arquivo de saída.|
|[-win32res](win32res-compiler-option.md)|Especifica um recurso Win32 a ser inserido no arquivo de saída.|

## <a name="miscellaneous"></a>Diversos

|Opção|Finalidade|
|------------|-------------|
|[@](response-file-compiler-option.md)|Especifica um arquivo de resposta.|
|[-?](help-compiler-option.md)|Lista as opções de compilador para stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Especifica o endereço básico preferencial no qual uma DLL será carregada.|
|[-página de código](codepage-compiler-option.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|
|[-ajuda](help-compiler-option.md)|Lista as opções de compilador para stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Especifica que o arquivo executável dá suporte a uma ASLR (Address Space Layout Randomization).|
|[-langversion](langversion-compiler-option.md)|Especificar a versão da linguagem: padrão, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 ou mais recente |
|[-principal](main-compiler-option.md)|Especifica a localização do método **Principal**.|
|[-noconfig](noconfig-compiler-option.md)|Instrui o compilador a não compilar com o csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Suprime as informações da faixa do compilador.|
|[-remaldição](recurse-compiler-option.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|
|[-versão do subsistema](subsystemversion-compiler-option.md)|Especifica a versão mínima do subsistema que o arquivo executável pode usar.|
|[-Inseguro](unsafe-compiler-option.md)|Habilita a compilação de código que usa a palavra-chave [unsafe](../keywords/unsafe.md).|
|[-utf8output](utf8output-compiler-option.md)|Exibe a saída do compilador usando a codificação UTF-8.|
|-parallel[+&#124;-]|Especifica se deve o build simultâneo deve ser usado (+).|
|-checksumalgorithm:\<alg>|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|

## <a name="obsolete-options"></a>Opções obsoletas

|Opção|Finalidade|
|---|---|
|-incremental|Habilita a compilação incremental.|

## <a name="see-also"></a>Confira também

- [C# Opções de compilador](index.md)
- [Opções do compilador C# listadas em ordem alfabética](listed-alphabetically.md)
- [Como configurar variáveis de ambiente para a linha de comando do Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
