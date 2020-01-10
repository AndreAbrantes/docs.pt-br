---
title: Aprendizado de máquina automatizado com o ML.NET
description: Visão geral do treinamento e seleção automáticos de modelos
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c6c369dc0b0375f180d33d85ef320ddb24102f3e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740101"
---
# <a name="automated-machine-learning-with-mlnet"></a>Aprendizado de máquina automatizado com o ML.NET

O aprendizado de máquina automatizado é um recurso do ML.NET que executa a seleção e treinamento automáticos de modelos. Você especifica a tarefa de aprendizado de máquina e fornece um conjunto de dados. O ML automatizado escolhe o modelo com as melhores métricas. Ele produz:

- um arquivo de modelo que pode ser carregado em seu aplicativo de previsão
- código do aplicativo para fazer previsões
- o código-fonte usado para seleção de recursos e o treinamento do modelo (para entender o modelo)

> [!NOTE]
> Esse recurso está atualmente em versão prévia e o material pode estar sujeito a alterações.

O ML automatizado é atualmente limitado a [tarefas](resources/tasks.md) de aprendizado de máquina de classificação binária, classificação multiclasse e regressão. As outras tarefas de aprendizado de máquina terão suporte em versões futuras.

Há três maneiras de usar o ML automatizado:

1. Com uma interface gráfica do usuário, com o [construtor de modelo do ML.NET](automate-training-with-model-builder.md)
1. Na linha de comando, com a [CLI do ML.NET](automate-training-with-cli.md)
1. Por meio de um aplicativo com a [API de ML automatizada](how-to-guides/how-to-use-the-automl-api.md)
