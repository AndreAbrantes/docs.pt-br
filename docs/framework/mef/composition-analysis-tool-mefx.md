---
title: Ferramenta de Análise de Composição (Mefx)
description: Leia sobre a ferramenta de análise de composição (Mefx), que analisa os arquivos DLL e EXE que contêm partes Managed Extensibility Frameworks (MEF) no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: abb1459afc5aeb2d39ee553c62fe382bb7af58d5
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281271"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="f1f38-103">Ferramenta de Análise de Composição (Mefx)</span><span class="sxs-lookup"><span data-stu-id="f1f38-103">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="f1f38-104">A Ferramenta de Análise de Composição (Mefx) é um aplicativo de linha de comando que analisa arquivos de biblioteca (.dll) e de aplicativo (.exe) que contêm partes do MEF (Managed Extensibility Framework).</span><span class="sxs-lookup"><span data-stu-id="f1f38-104">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="f1f38-105">A principal finalidade da Mefx é fornecer aos desenvolvedores uma maneira de diagnosticar falhas de composição em seus aplicativos MEF sem a necessidade de adicionar um código de rastreamento inconveniente ao próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1f38-105">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="f1f38-106">Ele também pode ser útil para ajudar a entender as partes de uma biblioteca fornecida por terceiros.</span><span class="sxs-lookup"><span data-stu-id="f1f38-106">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="f1f38-107">Este tópico descreve como usar a Mefx e fornece uma referência para sua sintaxe.</span><span class="sxs-lookup"><span data-stu-id="f1f38-107">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="f1f38-108">Obtendo a Mefx</span><span class="sxs-lookup"><span data-stu-id="f1f38-108">Getting Mefx</span></span>  
 <span data-ttu-id="f1f38-109">A Mefx está disponível no GitHub em [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="f1f38-109">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="f1f38-110">Basta baixar e descompactar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f1f38-110">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="f1f38-111">Sintaxe básica</span><span class="sxs-lookup"><span data-stu-id="f1f38-111">Basic Syntax</span></span>  
 <span data-ttu-id="f1f38-112">A Mefx é invocada na linha de comando no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="f1f38-112">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="f1f38-113">O primeiro conjunto de argumentos especifica os arquivos e os diretórios dos quais as partes devem ser carregadas para análise.</span><span class="sxs-lookup"><span data-stu-id="f1f38-113">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="f1f38-114">Especifique um arquivo com a opção `/file:` e um diretório com a opção `/directory:`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-114">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="f1f38-115">Você pode especificar vários arquivos ou diretórios, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f1f38-115">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="f1f38-116">Cada arquivo .dll ou .exe deve ser carregado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="f1f38-116">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="f1f38-117">Se algum arquivo for carregado várias vezes, a ferramenta poderá retornar informações incorretas.</span><span class="sxs-lookup"><span data-stu-id="f1f38-117">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="f1f38-118">Depois da lista de arquivos e diretórios, você deverá especificar um comando e as opções para esse comando.</span><span class="sxs-lookup"><span data-stu-id="f1f38-118">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="f1f38-119">Listando as partes disponíveis</span><span class="sxs-lookup"><span data-stu-id="f1f38-119">Listing Available Parts</span></span>  
 <span data-ttu-id="f1f38-120">Use a ação `/parts` para listar todas as partes declaradas nos arquivos carregados.</span><span class="sxs-lookup"><span data-stu-id="f1f38-120">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="f1f38-121">O resultado é uma lista simple de nomes de parte.</span><span class="sxs-lookup"><span data-stu-id="f1f38-121">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="f1f38-122">Para obter mais informações sobre as partes, use a opção `/verbose`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-122">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="f1f38-123">Isso produzirá mais informações para todas as partes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f1f38-123">This will output more information for all available parts.</span></span> <span data-ttu-id="f1f38-124">Para obter mais informações sobre uma única parte, use a ação `/type` em vez de `/parts`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-124">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="f1f38-125">Listando as importações e exportações</span><span class="sxs-lookup"><span data-stu-id="f1f38-125">Listing Imports and Exports</span></span>  
 <span data-ttu-id="f1f38-126">As ações `/imports` e `/exports` listarão todas as partes importadas e todas as partes exportadas, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f1f38-126">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="f1f38-127">Você também pode listar as partes que importam ou exportam um tipo específico usando as ações `/importers` ou `/exporters`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-127">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="f1f38-128">Você também pode aplicar a opção `/verbose` a essas ações.</span><span class="sxs-lookup"><span data-stu-id="f1f38-128">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="f1f38-129">Localizando as partes rejeitadas</span><span class="sxs-lookup"><span data-stu-id="f1f38-129">Finding Rejected Parts</span></span>  
 <span data-ttu-id="f1f38-130">Depois de carregar as partes disponíveis, a Mefx usa o mecanismo de composição do MEF para compô-las.</span><span class="sxs-lookup"><span data-stu-id="f1f38-130">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="f1f38-131">As partes que não podem ser compostas com êxito são chamadas de *rejeitadas*.</span><span class="sxs-lookup"><span data-stu-id="f1f38-131">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="f1f38-132">Para listar todas as partes rejeitadas, use a ação `/rejected`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-132">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="f1f38-133">Você pode usar a opção `/verbose` com a ação `/rejected` para imprimir informações detalhadas sobre as partes rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="f1f38-133">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="f1f38-134">No exemplo a seguir, a DLL `ClassLibrary1` contém a parte `AddIn`, que importa as partes `MemberPart` e `ChainOne`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-134">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="f1f38-135">A `ChainOne` importa a `ChainTwo`, mas a `ChainTwo` não existe.</span><span class="sxs-lookup"><span data-stu-id="f1f38-135">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="f1f38-136">Isso significa que a `ChainOne` foi rejeitada, o que faz com que a `AddIn` seja rejeitada.</span><span class="sxs-lookup"><span data-stu-id="f1f38-136">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="f1f38-137">O exemplo a seguir mostra a saída completa do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="f1f38-137">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="f1f38-138">As informações interessantes estão contidas nos resultados de `[Exception]` e `[Unsuitable]`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-138">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="f1f38-139">O resultado de `[Exception]` fornece informações sobre por que uma parte foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="f1f38-139">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="f1f38-140">O resultado `[Unsuitable]` indica por que uma parte com outro tipo de correspondência não pôde ser usada para preencher uma importação. Nesse caso, porque essa parte foi rejeitada devido à ausência de importações.</span><span class="sxs-lookup"><span data-stu-id="f1f38-140">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="f1f38-141">Analisando a causa principal</span><span class="sxs-lookup"><span data-stu-id="f1f38-141">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="f1f38-142">Se várias partes estiverem vinculadas em uma cadeia longa de dependência, um problema envolvendo uma parte próxima à parte inferior poderá fazer com que a cadeia inteira seja rejeitada.</span><span class="sxs-lookup"><span data-stu-id="f1f38-142">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="f1f38-143">O diagnóstico desses problemas pode ser difícil, pois a causa raiz da falha nem sempre é óbvia.</span><span class="sxs-lookup"><span data-stu-id="f1f38-143">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="f1f38-144">Para ajudar a resolver o problema, você pode usar a ação `/causes`, que tenta localizar a causa raiz de qualquer rejeição em cascata.</span><span class="sxs-lookup"><span data-stu-id="f1f38-144">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="f1f38-145">O uso da ação `/causes` no exemplo anterior listaria apenas as informações para `ChainOne`, cuja importação não preenchida é a causa raiz da rejeição de `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-145">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="f1f38-146">A ação `/causes` pode ser usada nas opções normal e `/verbose`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-146">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1f38-147">Na maioria dos casos, a Mefx poderá diagnosticar a causa raiz de uma falha em cascata.</span><span class="sxs-lookup"><span data-stu-id="f1f38-147">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="f1f38-148">No entanto, nos casos em que as partes são adicionadas de forma programática a um contêiner, nos que envolvem contêineres hierárquicos ou nos que envolvem implementações de `ExportProvider` personalizadas, a Mefx não pode diagnosticar a causa.</span><span class="sxs-lookup"><span data-stu-id="f1f38-148">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="f1f38-149">Em geral, esses casos descritos devem ser evitados sempre que possível, pois as falhas geralmente são difíceis de diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="f1f38-149">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="f1f38-150">Listas de permissões</span><span class="sxs-lookup"><span data-stu-id="f1f38-150">White Lists</span></span>  
 <span data-ttu-id="f1f38-151">A opção `/whitelist` permite que você especifique um arquivo de texto que lista as partes que devem ser rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="f1f38-151">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="f1f38-152">Assim, as rejeições inesperadas serão sinalizadas.</span><span class="sxs-lookup"><span data-stu-id="f1f38-152">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="f1f38-153">Isso pode ser útil ao analisar uma biblioteca incompleta ou uma sub-biblioteca com algumas dependências faltando.</span><span class="sxs-lookup"><span data-stu-id="f1f38-153">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="f1f38-154">A opção `/whitelist` pode ser aplicada às ações `/rejected` ou `/causes`.</span><span class="sxs-lookup"><span data-stu-id="f1f38-154">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="f1f38-155">Considere um arquivo chamado test.txt que contenha o texto "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="f1f38-155">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="f1f38-156">Se você executar a ação `/rejected` com a opção `/whitelist` no exemplo anterior, ela produzirá a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f1f38-156">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
