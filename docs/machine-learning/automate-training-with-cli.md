---
title: Automatizar o treinamento de modelos com a CLI do ML.NET
description: Descubra como usar a ferramenta de CLI do ML.NET para treinar automaticamente o melhor modelo da linha de comando.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185892"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatizar o treinamento de modelos com a CLI do ML.NET

A ML.NET CLI automatiza a geração de modelos para desenvolvedores .NET.

Para usar a API do ML.NET por si só (sem a CLI de AutoML do ML.NET), você precisa escolher um treinador (implementação de um algoritmo de aprendizado de máquina para uma tarefa específica) e o conjunto de transformações de dados (engenharia de recursos) para aplicar aos seus dados. O pipeline ideal variará para cada conjunto de dados e selecionar o algoritmo ideal entre todas as opções aumenta a complexidade. Além disso, cada algoritmo tem um conjunto de hiperparâmetros a serem ajustados. Portanto, você pode passar semanas e até meses em otimização de modelos de machine learning na tentativa de encontrar as combinações de engenharia de recursos, algoritmos de aprendizado e hiperparâmetros.

A CLI ML.NET simplifica esse processo usando o AutoML (Machine Learning) automatizado.

> [!NOTE]
> Este tópico refere-se à **CLI** do ML.NET e ao **AutoML** do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>O que é a interface de linha de comando ML.NET (CLI)?

O ML.NET CLI é uma [ferramenta .NET Core](../core/tools/global-tools.md). Uma vez instalado, você lhe dá uma tarefa de aprendizado de máquina e um conjunto de dados de treinamento, e ele gera um modelo ML.NET, bem como o código C# para executar para usar o modelo em seu aplicativo.

Como mostrado na figura a seguir, é simples gerar um modelo de alta qualidade ML.NET (modelo serializado .zip file) mais o código c# da amostra para executar/marcar esse modelo. Além disso, o código C# para criar/treinar esse modelo também é gerado, de modo que você pode pesquisar e iterar pelo algoritmo e pelas configurações usados para esse "melhor modelo" gerado.

![Imagem](media/automate-training-with-cli/cli-high-level-process.png "Motor AutoML funcionando dentro do ML.NET CLI")

Você pode gerar esses ativos de seus próprios conjuntos de dados sem codificação por conta própria, portanto, ele também melhorará a sua produtividade, mesmo se você já conhecer o ML.NET.

Atualmente, as tarefas de ML compatíveis com a CLI do ML.NET são:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Futuro: outras tarefas de aprendizado de máquina, tais como `recommendation`, `ranking`, `anomaly-detection` e `clustering`

Exemplo de uso:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

Você pode executá-los do mesmo modo que no *Windows PowerShell*, no *bash do macOS/Linux ou no *CMD do Windows*. No entanto, o preenchimento automático de tabela (sugestões de parâmetro) não funcionará no *CMD do Windows*.

## <a name="output-assets-generated"></a>Ativos de saída gerados

O comando `auto-train` da CLI gera os seguintes ativos na pasta de saída:

- Um modelo .zip serializado ("melhor modelo") pronto para uso voltado à execução de previsões.
- Solução em C# com:
  - Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).
  - Código C# com o código de treinamento usado para gerar esse modelo (para fins de aprendizado ou retreinamento de modelo).
- Arquivo de log com informações de todas as iterações/varreduras entre vários algoritmos avaliados, incluindo sua configuração/pipeline detalhado.

Os primeiros dois ativos podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da área de trabalho etc.) para fazer previsões com esse modelo de ML gerado.

O terceiro ativo, o código de treinamento, mostra a você qual código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, de modo que você pode treinar novamente seu modelo e investigar e iterar em quais hiperparâmetros e treinador/algoritmo específicos foram selecionados pela CLI e AutoML nos bastidores.

## <a name="understanding-the-quality-of-the-model"></a>Noções básicas sobre a qualidade do modelo

Quando você gera um "melhor modelo" com a ferramenta CLI, você vê métricas de qualidade (como precisão e R-Squared) conforme apropriado para a tarefa ML que você está mirando.

Aqui essas métricas são resumidas agrupadas pela tarefa ML para que você possa entender a qualidade do seu "melhor modelo" gerado automaticamente.

### <a name="metrics-for-binary-classification-models"></a>Métricas para modelos de classificação binária

A seguir, é exibida a lista de métricas de tarefas de classificação binária de ML para os cinco principais modelos encontrados pela CLI:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

A precisão é uma métrica popular para problemas de classificação, no entanto, a precisão nem sempre é a melhor métrica para selecionar o melhor modelo a partir do explicado nas referências a seguir. Há casos em que você precisa avaliar a qualidade do seu modelo com métricas adicionais.

Para explorar e entender as métricas que são saídas pela CLI, consulte [Métricas de avaliação para classificação binária](resources/metrics.md#evaluation-metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Métricas para modelos de classificação multiclasse

A seguir é exibida a lista de métricas de tarefas de ML de classificação multiclasse para os cinco principais modelos encontrados pela CLI:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Para explorar e entender as métricas que são saídas pela CLI, consulte [Métricas de avaliação para classificação multiclasse](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Métricas para modelos de regressão e recomendação

Um modelo de regressão se ajustará bem aos dados se as diferenças entre os valores observados e os previstos do modelo forem pequenas e sem desvio. A regressão pode ser avaliada com certas métricas.

Você verá uma lista semelhante de métricas para os melhores modelos de qualidade encontrados pela CLI. Neste caso em particular, relacionados a uma tarefa de ML de regressão:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Para explorar e entender as métricas que são saídas pela CLI, consulte [Métricas de avaliação para regressão](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Confira também

- [Como instalar a ferramenta de CLI do ML.NET](how-to-guides/install-ml-net-cli.md)
- [Tutorial: Analise o sentimento usando o ML.NET CLI](tutorials/sentiment-analysis-cli.md)
- [Referência de comandos da CLI do ML.NET](reference/ml-net-cli-reference.md)
- [Telemetria na CLI do ML.NET](resources/ml-net-cli-telemetry.md)
