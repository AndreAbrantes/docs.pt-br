---
title: "Comando dotnet-remove package – CLI do .NET Core"
description: "O comando de pacote dotnet-remove fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto."
keywords: dotnet-remove, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a3fef846d5850e2c2a158ccd1f30a84e8f23f793
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-remove-package"></a>Pacote dotnet-remove

## <a name="name"></a>Nome

`dotnet-remove package` – remove a referência de pacote de um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando irá procurar um no diretório atual.

`PACKAGE_NAME`

A referência de pacote a ser removida.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:

`dotnet remove package Newtonsoft.Json`

