---
title: Determinar quais versões do .NET Framework estão instaladas
description: Use o código, regedit.exe ou PowerShell para detectar quais versões do .NET Framework estão instaladas em um computador consultando o registro do Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: f4cb85e346e0043a3f28c48845f574afa89548db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673352"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="caf13-103">Como determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="caf13-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="caf13-104">Os usuários podem [instalar](../install/index.md) e executar várias versões do .NET Framework em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="caf13-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="caf13-105">Ao desenvolver ou implantar seu aplicativo, talvez seja necessário saber quais versões do .NET Framework estão instaladas no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="caf13-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="caf13-106">O registro contém uma lista das versões do .NET Framework instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="caf13-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="caf13-107">.NET Framework consiste em dois componentes principais, que têm a versão separada:</span><span class="sxs-lookup"><span data-stu-id="caf13-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="caf13-108">Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="caf13-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="caf13-109">.NET Framework e os assemblies compartilham o mesmo número de versão.</span><span class="sxs-lookup"><span data-stu-id="caf13-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="caf13-110">Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="caf13-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="caf13-111">O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="caf13-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="caf13-112">Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="caf13-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="caf13-113">Por exemplo, o CLR versão 4.0.30319. *xxxxx* em que *xxxxx* é menor que 42000, dá suporte a .NET Framework versões 4 por meio de 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="caf13-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="caf13-114">A versão do CLR maior ou igual ao 4.0.30319.42000 dá suporte a versões .NET Framework a partir do .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="caf13-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="caf13-115">As ferramentas mantidas pela Comunidade estão disponíveis para ajudar a detectar quais versões do .NET Framework estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="caf13-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="caf13-116">Uma ferramenta de linha de comando .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="caf13-116">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="caf13-117">Um módulo do PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="caf13-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="caf13-118">Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, consulte [como: determinar quais .NET Framework atualizações estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="caf13-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="caf13-119">Detectar .NET Framework 4,5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="caf13-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="caf13-120">A versão do .NET Framework (4,5 e posterior) instalada em um computador está listada no registro em **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="caf13-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="caf13-121">Se a subchave **completa** estiver ausente, .NET Framework 4,5 ou superior não estará instalado.</span><span class="sxs-lookup"><span data-stu-id="caf13-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="caf13-122">A subchave de **instalação do NET Framework** no caminho do registro *não começa com* um ponto.</span><span class="sxs-lookup"><span data-stu-id="caf13-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="caf13-123">O valor da **versão** REG_DWORD no registro representa a versão do .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="caf13-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="caf13-124">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caf13-124">.NET Framework version</span></span> | <span data-ttu-id="caf13-125">Valor da **versão**</span><span class="sxs-lookup"><span data-stu-id="caf13-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="caf13-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="caf13-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="caf13-127">Todos os sistemas operacionais Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="caf13-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="caf13-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="caf13-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="caf13-129">No Windows 8.1 e no Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="caf13-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="caf13-130">Em todos os outros sistemas operacionais Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="caf13-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="caf13-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="caf13-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="caf13-132">Todos os sistemas operacionais Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="caf13-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="caf13-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="caf13-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="caf13-134">No Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="caf13-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="caf13-135">Em todos os outros sistemas operacionais Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="caf13-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="caf13-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="caf13-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="caf13-137">Em sistemas com a Atualização de novembro do Windows 10: 394254</span><span class="sxs-lookup"><span data-stu-id="caf13-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="caf13-138">Em todos os outros sistemas operacionais Windows (incluindo o Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="caf13-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="caf13-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="caf13-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="caf13-140">Na Atualização de Aniversário do Windows 10 e Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="caf13-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="caf13-141">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="caf13-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="caf13-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="caf13-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="caf13-143">No Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="caf13-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="caf13-144">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="caf13-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="caf13-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="caf13-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="caf13-146">Na atualização dos criadores de outono do Windows 10 e do Windows Server, versão 1709:461308</span><span class="sxs-lookup"><span data-stu-id="caf13-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="caf13-147">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="caf13-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="caf13-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="caf13-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="caf13-149">Na atualização do Windows 10 de abril de 2018 e Windows Server, versão 1803:461808</span><span class="sxs-lookup"><span data-stu-id="caf13-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="caf13-150">Em todos os sistemas operacionais Windows, exceto Windows 10 de abril de 2018 atualização e Windows Server, versão 1803:461814</span><span class="sxs-lookup"><span data-stu-id="caf13-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="caf13-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="caf13-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="caf13-152">No Windows 10 maio 2019 atualização e Windows 10 de novembro de 2019 atualização: 528040</span><span class="sxs-lookup"><span data-stu-id="caf13-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="caf13-153">No Windows 10 pode 2020 atualização e atualização de 10 de outubro de 2020 do Windows: 528372</span><span class="sxs-lookup"><span data-stu-id="caf13-153">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="caf13-154">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="caf13-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="caf13-155">Versão mínima</span><span class="sxs-lookup"><span data-stu-id="caf13-155">Minimum version</span></span>

<span data-ttu-id="caf13-156">Para determinar se uma versão *mínima* do .NET Framework está presente, verifique uma versão **REG_DWORD valor** que seja maior ou igual ao valor correspondente listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="caf13-156">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="caf13-157">Por exemplo, se seu aplicativo for executado em .NET Framework 4,8 ou em uma versão posterior, teste para **obter uma versão** REG_DWORD valor *maior ou igual a* 528040.</span><span class="sxs-lookup"><span data-stu-id="caf13-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="caf13-158">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caf13-158">.NET Framework version</span></span> | <span data-ttu-id="caf13-159">Valor mínimo</span><span class="sxs-lookup"><span data-stu-id="caf13-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="caf13-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="caf13-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="caf13-161">378389</span><span class="sxs-lookup"><span data-stu-id="caf13-161">378389</span></span> |
| <span data-ttu-id="caf13-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="caf13-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="caf13-163">378675</span><span class="sxs-lookup"><span data-stu-id="caf13-163">378675</span></span> |
| <span data-ttu-id="caf13-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="caf13-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="caf13-165">379893</span><span class="sxs-lookup"><span data-stu-id="caf13-165">379893</span></span> |
| <span data-ttu-id="caf13-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="caf13-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="caf13-167">393295</span><span class="sxs-lookup"><span data-stu-id="caf13-167">393295</span></span> |
| <span data-ttu-id="caf13-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="caf13-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="caf13-169">394254</span><span class="sxs-lookup"><span data-stu-id="caf13-169">394254</span></span> |
| <span data-ttu-id="caf13-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="caf13-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="caf13-171">394802</span><span class="sxs-lookup"><span data-stu-id="caf13-171">394802</span></span> |
| <span data-ttu-id="caf13-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="caf13-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="caf13-173">460798</span><span class="sxs-lookup"><span data-stu-id="caf13-173">460798</span></span> |
| <span data-ttu-id="caf13-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="caf13-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="caf13-175">461308</span><span class="sxs-lookup"><span data-stu-id="caf13-175">461308</span></span> |
| <span data-ttu-id="caf13-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="caf13-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="caf13-177">461808</span><span class="sxs-lookup"><span data-stu-id="caf13-177">461808</span></span> |
| <span data-ttu-id="caf13-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="caf13-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="caf13-179">528040</span><span class="sxs-lookup"><span data-stu-id="caf13-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="caf13-180">Usar o editor do registro</span><span class="sxs-lookup"><span data-stu-id="caf13-180">Use Registry Editor</span></span>

01. <span data-ttu-id="caf13-181">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="caf13-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="caf13-182">(Você deve ter credenciais administrativas para executar o regedit.)</span><span class="sxs-lookup"><span data-stu-id="caf13-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="caf13-183">No editor do registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="caf13-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="caf13-184">Se a subchave **completa** não estiver presente, você não terá .NET Framework 4,5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="caf13-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="caf13-185">Verifique se há uma entrada de REG_DWORD chamada **versão**.</span><span class="sxs-lookup"><span data-stu-id="caf13-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="caf13-186">Se ele existir, você terá .NET Framework 4,5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="caf13-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="caf13-187">Seu valor corresponde a uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="caf13-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="caf13-188">Na figura a seguir, por exemplo, o valor da entrada de **versão** é 528040, que é a chave de versão para .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="caf13-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![Entrada de registro para .NET Framework 4,5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="caf13-190">Usar o PowerShell para verificar se há uma versão mínima</span><span class="sxs-lookup"><span data-stu-id="caf13-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="caf13-191">Use os comandos do PowerShell para verificar o valor da entrada de **versão** do **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ completa** subkey.</span><span class="sxs-lookup"><span data-stu-id="caf13-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="caf13-192">Os exemplos a seguir verificam o valor da entrada de **versão** para determinar se .NET Framework 4.6.2 ou posterior está instalado.</span><span class="sxs-lookup"><span data-stu-id="caf13-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="caf13-193">Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.</span><span class="sxs-lookup"><span data-stu-id="caf13-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="caf13-194">Consultar o registro usando código</span><span class="sxs-lookup"><span data-stu-id="caf13-194">Query the registry using code</span></span>

01. <span data-ttu-id="caf13-195">Use os <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> métodos e para acessar o **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework instalação \\ NDP \\ v4 \\ completa** subkey no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="caf13-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="caf13-196">Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos do registro serão diferentes dos listados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="caf13-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="caf13-197">O registro de 64 bits está disponível na subchave **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="caf13-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="caf13-198">Por exemplo, a subchave do registro para .NET Framework 4,5 é **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="caf13-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="caf13-199">Verifique o valor da **versão** REG_DWORD para determinar a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="caf13-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="caf13-200">Para compatibilidade com a versão atual, verifique se há um valor superior ou igual ao valor listado na [tabela de versões do .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="caf13-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="caf13-201">O exemplo a seguir verifica o valor da entrada de **versão** no registro para localizar as versões do .NET Framework 4.5-4.8 instaladas:</span><span class="sxs-lookup"><span data-stu-id="caf13-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="caf13-202">O exemplo exibe uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="caf13-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="caf13-203">Este exemplo segue a prática recomendada para a verificação de versão:</span><span class="sxs-lookup"><span data-stu-id="caf13-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="caf13-204">Ele verifica se o valor da entrada **Release** é *superior ou igual* ao valor das chaves de versão conhecidas.</span><span class="sxs-lookup"><span data-stu-id="caf13-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="caf13-205">Ele verifica na ordem da versão mais recente para a versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="caf13-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="caf13-206">Detectar .NET Framework 1,0 a 4,0</span><span class="sxs-lookup"><span data-stu-id="caf13-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="caf13-207">Cada versão do .NET Framework de 1,1 a 4,0 é listada como uma subchave em **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework Setup \\ NDP**.</span><span class="sxs-lookup"><span data-stu-id="caf13-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="caf13-208">A tabela a seguir lista o caminho para cada versão de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="caf13-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="caf13-209">Para a maioria das versões, há um valor de REG_DWORD de **instalação** de `1` para indicar que esta versão está instalada.</span><span class="sxs-lookup"><span data-stu-id="caf13-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="caf13-210">Nessas subchaves, há também uma **versão** REG_SZ valor que contém uma cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="caf13-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="caf13-211">A subchave de **instalação do NET Framework** no caminho do registro *não começa com* um ponto.</span><span class="sxs-lookup"><span data-stu-id="caf13-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="caf13-212">Versão do Framework</span><span class="sxs-lookup"><span data-stu-id="caf13-212">Framework Version</span></span>  | <span data-ttu-id="caf13-213">Subchave do registro</span><span class="sxs-lookup"><span data-stu-id="caf13-213">Registry Subkey</span></span> | <span data-ttu-id="caf13-214">Valor</span><span class="sxs-lookup"><span data-stu-id="caf13-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="caf13-215">1.0</span><span class="sxs-lookup"><span data-stu-id="caf13-215">1.0</span></span>                | <span data-ttu-id="caf13-216">**HKLM \\ software \\ Microsoft \\ . Política de NETFramework \\ \\ v 1.0 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="caf13-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="caf13-217">**Instalar** o REG_SZ igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="caf13-218">1,1</span><span class="sxs-lookup"><span data-stu-id="caf13-218">1.1</span></span>                | <span data-ttu-id="caf13-219">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="caf13-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="caf13-220">**Instalar** o REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="caf13-221">2,0</span><span class="sxs-lookup"><span data-stu-id="caf13-221">2.0</span></span>                | <span data-ttu-id="caf13-222">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="caf13-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="caf13-223">**Instalar** o REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="caf13-224">3.0</span><span class="sxs-lookup"><span data-stu-id="caf13-224">3.0</span></span>                | <span data-ttu-id="caf13-225">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.0 \\ instalação**</span><span class="sxs-lookup"><span data-stu-id="caf13-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="caf13-226">**InstallSuccess** REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="caf13-227">3,5</span><span class="sxs-lookup"><span data-stu-id="caf13-227">3.5</span></span>                | <span data-ttu-id="caf13-228">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**</span><span class="sxs-lookup"><span data-stu-id="caf13-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="caf13-229">**Instalar** o REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="caf13-230">4,0 perfil do cliente</span><span class="sxs-lookup"><span data-stu-id="caf13-230">4.0 Client Profile</span></span> | <span data-ttu-id="caf13-231">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Client**</span><span class="sxs-lookup"><span data-stu-id="caf13-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="caf13-232">**Instalar** o REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="caf13-233">4,0 perfil completo</span><span class="sxs-lookup"><span data-stu-id="caf13-233">4.0 Full Profile</span></span>   | <span data-ttu-id="caf13-234">**HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ completo**</span><span class="sxs-lookup"><span data-stu-id="caf13-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="caf13-235">**Instalar** o REG_DWORD igual a `1`</span><span class="sxs-lookup"><span data-stu-id="caf13-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="caf13-236">Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos do registro serão diferentes dos listados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="caf13-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="caf13-237">O registro de 64 bits está disponível na subchave **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="caf13-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="caf13-238">Por exemplo, a subchave do registro para .NET Framework 3,5 é **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="caf13-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="caf13-239">Observe que o caminho do registro para a subchave .NET Framework 1,0 é diferente dos outros.</span><span class="sxs-lookup"><span data-stu-id="caf13-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="caf13-240">Usar o editor do registro (versões mais antigas do Framework)</span><span class="sxs-lookup"><span data-stu-id="caf13-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="caf13-241">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="caf13-241">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="caf13-242">Você precisará ter credenciais administrativas para executar o REGEDIT.</span><span class="sxs-lookup"><span data-stu-id="caf13-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="caf13-243">Abra a subchave que corresponde à versão que você deseja verificar.</span><span class="sxs-lookup"><span data-stu-id="caf13-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="caf13-244">Use a tabela na seção [detectar .NET Framework 1,0 a 4,0](#detect-net-framework-10-through-40) .</span><span class="sxs-lookup"><span data-stu-id="caf13-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="caf13-245">A figura a seguir mostra a subchave e seu valor de **versão** para .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="caf13-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="caf13-246">![A entrada do registro para .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 e versões anteriores")</span><span class="sxs-lookup"><span data-stu-id="caf13-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="caf13-247">Consultar o registro usando código (versões mais antigas do Framework)</span><span class="sxs-lookup"><span data-stu-id="caf13-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="caf13-248">Use a <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> classe para acessar a subchave de **instalação HKEY_LOCAL_MACHINE do \\ \\ NDP software Microsoft \\ NET Framework Setup \\** no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="caf13-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caf13-249">Se o aplicativo que você está executando for de 32 bits e estiver em execução no Windows de 64 bits, os caminhos do registro serão diferentes dos listados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="caf13-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="caf13-250">O registro de 64 bits está disponível na subchave **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="caf13-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="caf13-251">Por exemplo, a subchave do registro para .NET Framework 3,5 é **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="caf13-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="caf13-252">O exemplo a seguir localiza as versões do .NET Framework 1-4 que estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="caf13-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="caf13-253">O exemplo exibe uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="caf13-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="caf13-254">Encontrar versões do CLR</span><span class="sxs-lookup"><span data-stu-id="caf13-254">Find CLR versions</span></span>

<span data-ttu-id="caf13-255">O .NET Framework CLR instalado com .NET Framework tem controle de versão separadamente.</span><span class="sxs-lookup"><span data-stu-id="caf13-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="caf13-256">Há duas maneiras de detectar a versão do .NET Framework CLR:</span><span class="sxs-lookup"><span data-stu-id="caf13-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="caf13-257">**A ferramenta de Clrver.exe**</span><span class="sxs-lookup"><span data-stu-id="caf13-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="caf13-258">Use a [ferramenta de versão do CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="caf13-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="caf13-259">Abra o [prompt de comando do desenvolvedor para o Visual Studio](../tools/developer-command-prompt-for-vs.md) e digite `clrver` .</span><span class="sxs-lookup"><span data-stu-id="caf13-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="caf13-260">Saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="caf13-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="caf13-261">**A `Environment` classe**</span><span class="sxs-lookup"><span data-stu-id="caf13-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="caf13-262">Para .NET Framework 4,5 e versões posteriores, não use a <xref:System.Environment.Version%2A?displayProperty=nameWithType> propriedade para detectar a versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="caf13-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="caf13-263">Em vez disso, consulte o registro conforme descrito em [detectar .NET Framework 4,5 e versões posteriores](#detect-net-framework-45-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="caf13-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="caf13-264">Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="caf13-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="caf13-265">O objeto `System.Version` retornado identifica a versão do runtime que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="caf13-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="caf13-266">Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="caf13-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="caf13-267">Para .NET Framework versões 4, 4,5, 4.5.1 e 4.5.2, a representação de cadeia de caracteres do <xref:System.Version> objeto retornado tem o formato 4.0.30319.*xxxxx*, em que *xxxxx* é menor que 42000.</span><span class="sxs-lookup"><span data-stu-id="caf13-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="caf13-268">Para .NET Framework 4,6 e versões posteriores, ele tem o formato 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="caf13-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="caf13-269">Depois de ter o objeto **version** , consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="caf13-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="caf13-270">Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="caf13-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="caf13-271">Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="caf13-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="caf13-272">Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="caf13-272">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="caf13-273">Esse método retorna um único valor que reflete a versão do runtime que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="caf13-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="caf13-274">Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="caf13-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="caf13-275">O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:</span><span class="sxs-lookup"><span data-stu-id="caf13-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="caf13-276">O exemplo exibe uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="caf13-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="caf13-277">Confira também</span><span class="sxs-lookup"><span data-stu-id="caf13-277">See also</span></span>

- [<span data-ttu-id="caf13-278">Como determinar quais .NET Framework atualizações estão instaladas</span><span class="sxs-lookup"><span data-stu-id="caf13-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="caf13-279">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="caf13-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="caf13-280">Versões e dependências do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caf13-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
