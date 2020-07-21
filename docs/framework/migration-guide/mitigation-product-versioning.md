---
title: 'Mitigação: Controle de versão de produto'
description: Neste artigo, saiba como .NET Framework o controle de versão do produto 4,6 e posterior foi alterado de versões anteriores.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475392"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="cc030-103">Mitigação: Controle de versão de produto</span><span class="sxs-lookup"><span data-stu-id="cc030-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="cc030-104">Na .NET Framework 4.6 e posterior, o controle de versão do produto foi alterado em relação às versões anteriores do .NET Framework (o .NET Framework 4, 4,5, 4.5.1 e 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="cc030-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="cc030-105">Alterações no controle de versão de produto</span><span class="sxs-lookup"><span data-stu-id="cc030-105">Product versioning changes</span></span>

<span data-ttu-id="cc030-106">Veja a seguir as alterações em detalhes:</span><span class="sxs-lookup"><span data-stu-id="cc030-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="cc030-107">O valor da entrada `Version` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` foi alterado para `4.6.`*xxxxx* para o .NET Framework 4.6 e suas versões pontuais, e para `4.7.`*xxxxx* para o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="cc030-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="cc030-108">No .NET Framework 4.5, 4.5.1 e 4.5.2, ele tinha o formato `4.5.`*xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="cc030-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="cc030-109">O controle de versão de arquivo e produto para arquivos do .NET Framework foi alterado do esquema de controle de versão anterior de `4.0.30319.x` para o de `4.6.X.0` para o .NET Framework 4.6 e suas versões pontuais, e para o de `4.7.X.0` para o .NET Framework 4.7 e suas versões pontuais.</span><span class="sxs-lookup"><span data-stu-id="cc030-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="cc030-110">Você pode ver esses novos valores ao exibir as **Propriedades** do arquivo depois de clicar com o botão direito do mouse em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cc030-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="cc030-111">Os atributos <xref:System.Reflection.AssemblyFileVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute> para assemblies gerenciados têm valores de <xref:System.Version> no formulário `4.6.X.0` para o .NET Framework 4.6 e suas versões pontuais, e `4.7.X.0` para o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="cc030-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="cc030-112">A partir do .NET Framework 4.6, a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> retorna a cadeia de caracteres de versão fixa `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="cc030-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="cc030-113">No .NET Framework 4, 4.5, 4.5.1 e 4.5.2, ela retorna as cadeias de caracteres de versão no formato `4.0.30319.xxxxx`, em que `xxxxx` é menor que 42000 (por exemplo, "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="cc030-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="cc030-114">Não é recomendável criar nova dependência de código de aplicativo na propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cc030-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="cc030-115">Como lidar com as alterações de controle de versão de produto</span><span class="sxs-lookup"><span data-stu-id="cc030-115">Handling the product versioning changes</span></span>

<span data-ttu-id="cc030-116">Em geral, os aplicativos devem depender das técnicas recomendadas para detecção de itens como a versão de runtime do .NET Framework e o diretório de instalação:</span><span class="sxs-lookup"><span data-stu-id="cc030-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="cc030-117">Para detectar a versão de runtime do .NET Framework, confira [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md) (Como determinar quais versões do .NET Framework estão instaladas).</span><span class="sxs-lookup"><span data-stu-id="cc030-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="cc030-118">Para determinar o caminho de instalação do .NET Framework, use o valor da entrada `InstallPath` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.</span><span class="sxs-lookup"><span data-stu-id="cc030-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="cc030-119">O nome da subchave é `NET Framework Setup`, e não `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="cc030-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="cc030-120">Para determinar o caminho do diretório do Common Language Runtime do .NET Framework, chame o método <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cc030-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="cc030-121">Para obter a versão do CLR, chame o método <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cc030-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="cc030-122">Para o .NET Framework 4 e suas versões pontuais (o .NET Framework 4.5, 4.5.1, 4.5.2 e o .NET Framework 4.6, 4.6.1, 4.6.2 e 4.7), ele retorna a cadeia de caracteres `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="cc030-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc030-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc030-123">See also</span></span>

- [<span data-ttu-id="cc030-124">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="cc030-124">Application compatibility</span></span>](application-compatibility.md)
