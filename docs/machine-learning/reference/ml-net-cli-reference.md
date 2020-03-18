---
title: ML.NET referência de comando CLI
description: Visão geral, exemplos e referência para o comando de treinamento automático na ferramenta de CLI do ML.NET.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848919"
---
# <a name="the-mlnet-cli-command-reference"></a>A referência de comando ML.NET CLI

O comando `auto-train` é o principal comando fornecido pela ferramenta de CLI do ML.NET. O comando permite gerar uma boa qualidade ML.NET modelo usando aprendizado de máquina automatizado (AutoML), bem como o exemplo de código C# para executar/marcar esse modelo. Além disso, o código C# para treinar o modelo é gerado para você pesquisar o algoritmo e as configurações do modelo.

> [!NOTE]
> Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.

## <a name="overview"></a>Visão geral

Exemplo de uso:

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

O comando `mlnet auto-train` gera os seguintes ativos:

- Um modelo serializado. zip ("melhor modelo") pronto para uso.
- C# código para executar/marcar que gerou modelo.
- C# código com o código de treinamento usado para gerar esse modelo.

Os dois primeiros ativos podem ser usados diretamente em seus aplicativos de usuário final (ASP.NET aplicativo web Core, serviços, aplicativo de desktop e muito mais) para fazer previsões com o modelo.

O terceiro ativo, o código de treinamento, mostra o que ML.NET código de API foi usado pela CLI para treinar o modelo gerado, para que você possa investigar o algoritmo específico e as configurações do modelo.

## <a name="examples"></a>Exemplos

O comando CLI mais simples para um problema de classificação binária (O AutoML infere a maior parte da configuração a partir dos dados fornecidos):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Outro comando simples da CLI para um problema de regressão:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Crie e treine um modelo de classificação binária com um conjunto de dados de treinamento, um conjunto de dados de teste e ainda mais argumentos explícitos de personalização:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Opções de comando

`mlnet auto-train`treina vários modelos com base no conjunto de dados fornecido e finalmente seleciona o melhor modelo, salva-o como um arquivo serializado .zip plus gera código C# relacionado para pontuação e treinamento.

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Opções de entrada inválidas fazem com que a ferramenta CLI emita uma lista de entradas válidas e uma mensagem de erro.

## <a name="task"></a>Tarefa

`--task | --mltask | -T` (string)

Uma única cadeia de caracteres fornecendo o problema de ML a resolver. Por exemplo, qualquer uma das tarefas a seguir (a CLI eventualmente dará suporte a todas as tarefas compatíveis com o AutoML):

- `regression` – escolha se o modelo do ML será usado para prever um valor numérico
- `binary-classification` – escolha se o resultado do modelo de ML terá dois valores boolianos categóricos possíveis (0 ou 1).
- `multiclass-classification` – escolha se o resultado do modelo de ML terá vários valores boolianos categóricos possíveis.

Uma tarefa de ML deve ser fornecida neste argumento.

## <a name="dataset"></a>Dataset

`--dataset | -d` (string)

Esse argumento fornece o caminho do arquivo para uma das seguintes opções:

- *A: Todo o arquivo do conjunto de dados:* Se usar essa opção e `--test-dataset` o `--validation-dataset`usuário não estiver fornecendo e, em seguida, a validação cruzada (k-fold, etc.) ou abordagens automatizadas de divisão de dados serão usadas internamente para validar o modelo. Nesse caso, o usuário precisará apenas fornecer o caminho do arquivo do conjunto de dados.

- *B: O arquivo do conjunto de dados de treinamento:* Se o usuário também estiver fornecendo `--test-dataset` conjuntos `--validation-dataset`de dados `--dataset` para validação do modelo (usando e opcionalmente), então o argumento significa ter apenas o "conjunto de dados de treinamento". Por exemplo, ao usar uma abordagem de 80-20% para validar a qualidade do modelo e obter métricas de precisão, o "conjunto de dados treinamento" terá 80% dos dados e o "conjunto de dados de teste" terá 20% dos dados.

## <a name="test-dataset"></a>Conjunto de dados de teste

`--test-dataset | -t` (string)

Caminho do arquivo que aponta para o arquivo de conjunto de dados de teste, por exemplo, ao usar uma abordagem de 80-20% ao realizar validações regulares para obter métricas de precisão.

Ao usar `--test-dataset`, `--dataset` também é necessária.

O argumento `--test-dataset` é opcional, a menos que o --validation-dataset seja usado. Nesse caso, o usuário precisa usar os três argumentos.

## <a name="validation-dataset"></a>Conjunto de dados de validação

`--validation-dataset | -v` (string)

Caminho do arquivo apontando para o arquivo de conjunto de dados de validação. O conjunto de dados de validação é opcional em qualquer caso.

Se usar um `validation dataset`, o comportamento deverá ser:

- Os argumentos `test-dataset` e `--dataset` também são necessários.

- O conjunto de dados `validation-dataset` é usado para estimar o erro de previsão para a seleção de modelo.

- O `test-dataset` é usado para a avaliação do erro de generalização do modelo final escolhido. O ideal é que o conjunto de teste seja mantido em um "cofre" e seja levado somente no final da análise de dados.

Basicamente, ao usar um `validation dataset` mais o `test dataset`, a fase de validação é dividida em duas partes:

1. Na primeira parte, você apenas examina seus modelos e seleciona a abordagem com melhor desempenho usando os dados de validação (=validation)
2. Em seguida, você pode estimar a precisão da abordagem selecionada (=test).

Portanto, a separação dos dados pode ser 80/10/10 ou 75/15/10. Por exemplo: 

- O arquivo `training-dataset` deve ter 75% dos dados.
- O arquivo `validation-dataset` deve ter 15% dos dados.
- O arquivo `test-dataset` deve ter 10% dos dados.

Em qualquer caso, essas porcentagens serão decididas pelo usuário usando a CLI que fornecerá os arquivos já dividido.

## <a name="label-column-name"></a>Nome da coluna do rótulo

`--label-column-name | -n` (string)

Com este argumento, uma coluna de destino/objetivo específica (a variável que você deseja prever) pode ser especificada usando o nome da coluna definido no cabeçalho do conjunto de dados.

Esse argumento é usado somente para tarefas de ML supervisionadas, tais como um *problema de classificação*. Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.

## <a name="label-column-index"></a>Índice da coluna de rótulos

`--label-column-index | -i` (int)

Com este argumento, uma coluna de destino/objetivo específico (a variável que você deseja prever) pode ser especificada usando o índice numérico da coluna no arquivo do conjunto de dados (os valores de coluna de índice começam em 1).

*Nota:* Se o usuário também `--label-column-name`estiver `--label-column-name` usando o , é o que está sendo usado.

Esse argumento é usado apenas para a tarefa de ML supervisionada, tal como um *problema de classificação*. Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.

## <a name="ignore-columns"></a>Ignorar colunas

`--ignore-columns | -I` (string)

Com este argumento, você pode ignorar as colunas existentes no arquivo de conjunto de dados para que elas não sejam carregadas e usadas pelos processos de treinamento.

Especifique os nomes de colunas que você deseja ignorar. Use ',' (vírgula com espaço) ou ' ' (espaço) para separar vários nomes de coluna. Você pode usar aspas para nomes de coluna que contêm espaço em branco (por exemplo, "usuário logado").

Exemplo:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Tem cabeçalho

`--has-header | -h` (bool)

Especifique se os arquivos de conjunto de dados têm uma linha de cabeçalho.
Os valores possíveis são:

- `true`
- `false`

O valor padrão será `true` se esse argumento não for especificado pelo usuário.

Para usar o argumento `--label-column-name`, você precisa ter um cabeçalho no arquivo de conjunto de dados e `--has-header` definido como `true` (o que ocorre por padrão).

## <a name="max-exploration-time"></a>Tempo máximo de exploração

`--max-exploration-time | -x` (string)

Por padrão, o tempo máximo de exploração é de 30 minutos.

Esse argumento define o tempo máximo (em segundos) para o processo explorar vários treinadores e configurações. O tempo configurado poderá ser excedido se o tempo fornecido for muito curto (digamos, dois segundos) para uma única iteração. Nesse caso, o tempo real é o tempo necessário para produzir uma configuração de modelo em uma única iteração.

O tempo necessário para iterações pode variar, dependendo do tamanho do conjunto de dados.

## <a name="cache"></a>Cache

`--cache | -c` (string)

Se você usar o armazenamento em cache, o conjunto de dados de treinamento inteiro será carregado na memória.

Para conjuntos de dados pequenos e médios, usar o cache pode melhorar drasticamente o desempenho de treinamento, o que significa que o tempo de treinamento pode ser menor do que quando você não usa o cache.

No entanto, para grandes conjuntos de dados, carregar todos os dados na memória pode ter um efeito negativo, pois você poderá ficar com memória insuficiente. Ao treinar com arquivos de conjunto de dados grandes sem usar o cache, o ML.NET transmitirá partes de dados da unidade quando ele precisar carregar mais dados durante o treinamento.

É possível especificar os seguintes valores:

`on`: Forças cache a ser usado durante o treinamento.
`off`: Forças cache não devem ser usados durante o treinamento.
`auto`: Dependendo da heurística AutoML, o cache será usado ou não. Em geral, conjuntos de dados pequenos/médios usarão o cache e grandes conjuntos de dados não usarão o cache se você usar a escolha `auto`.

Se você não especificar o parâmetro `--cache`, a configuração de cache `auto` será usada por padrão.

## <a name="name"></a>Nome

`--name | -N` (string)

O nome para a solução ou projeto de saída criado. Se nenhum nome for especificado, o nome `sample-{mltask}` será usado.

O arquivo de modelo do ML.NET (arquivo zip) também receberá o mesmo nome.

## <a name="output-path"></a>Caminho de saída

`--output-path | -o` (string)

Local/pasta raiz para colocar a saída gerada. O padrão é o diretório atual.

## <a name="verbosity"></a>Detalhamento

`--verbosity | -V` (string)

Define o nível de detalhamento da saída padrão.

Valores permitidos são:

- `q[uiet]`
- `m[inimal]` (por padrão)
- `diag[nostic]` (nível de informações de registro em log)

Por padrão, a ferramenta da CLI deve mostrar alguns comentários mínimos (mínimo) quando estiver funcionando, por exemplo, mencionar que ela está funcionando e, se possível, quanto tempo falta ou que percentual do tempo foi concluído.

## <a name="help"></a>Ajuda

`-h|--help`

Imprime uma ajuda para o comando com uma descrição para o parâmetro de cada comando.

## <a name="see-also"></a>Confira também

- [Como instalar a ferramenta de CLI do ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Visão geral da ML.NET CLI](../automate-training-with-cli.md)
- [Tutorial: Analise o sentimento usando o ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Telemetria na CLI do ML.NET](../resources/ml-net-cli-telemetry.md)
