---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540077"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="8930d-101">Instalar a ferramenta global</span><span class="sxs-lookup"><span data-stu-id="8930d-101">Install the global tool</span></span>

<span data-ttu-id="8930d-102">Os ativos de pacote devem ser instalados em um local protegido usando a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="8930d-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="8930d-103">Essa separação evita o compartilhamento de um ambiente de usuário restrito com um ambiente com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="8930d-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8930d-104">`/usr/local/share/dotnet-tools` será criado com a permissão `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="8930d-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="8930d-105">Se o diretório já existir, use o comando `ls -l` para verificar se o usuário restrito não tem permissão para editar o diretório.</span><span class="sxs-lookup"><span data-stu-id="8930d-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="8930d-106">Nesse caso, use o comando `sudo chmod o-w -R /usr/share/dotnet-tools` para remover o acesso.</span><span class="sxs-lookup"><span data-stu-id="8930d-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="8930d-107">Executar a ferramenta global</span><span class="sxs-lookup"><span data-stu-id="8930d-107">Run the global tool</span></span>

<span data-ttu-id="8930d-108">**Opção 1** Usar o caminho completo com o sudo:</span><span class="sxs-lookup"><span data-stu-id="8930d-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="8930d-109">**Opção 2** Adicionar o link do símbolo da ferramenta, uma vez por ferramenta:</span><span class="sxs-lookup"><span data-stu-id="8930d-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="8930d-110">E execute com:</span><span class="sxs-lookup"><span data-stu-id="8930d-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="8930d-111">Desinstalar a ferramenta global</span><span class="sxs-lookup"><span data-stu-id="8930d-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8930d-112">Se tiver feito um link de símbolo, você também precisará removê-lo:</span><span class="sxs-lookup"><span data-stu-id="8930d-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
