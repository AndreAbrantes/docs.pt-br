---
title: Emitindo métodos e assemblies dinâmicos
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180535"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="7d664-102">Emitindo métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="7d664-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="7d664-103">Esta seção descreve um conjunto de tipos gerenciados no namespace <xref:System.Reflection.Emit> que permite que um compilador ou ferramenta emita metadados e o MSIL (Microsoft Intermediate Language) no tempo de execução e, opcionalmente, gere um arquivo executável portátil (PE) no disco.</span><span class="sxs-lookup"><span data-stu-id="7d664-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="7d664-104">Mecanismos de script e compiladores são os principais usuários desse namespace.</span><span class="sxs-lookup"><span data-stu-id="7d664-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="7d664-105">Nesta seção, a funcionalidade fornecida pelo namespace <xref:System.Reflection.Emit> é conhecida como emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="7d664-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="7d664-106">A emissão de reflexão fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="7d664-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="7d664-107">Defina métodos globais leves no tempo de execução usando a classe <xref:System.Reflection.Emit.DynamicMethod> e execute-os usando delegados.</span><span class="sxs-lookup"><span data-stu-id="7d664-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="7d664-108">Defina os assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="7d664-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="7d664-109">Defina os assemblies no tempo de execução, execute-os, descarregue-os e permita que a coleta de lixo recupere seus recursos.</span><span class="sxs-lookup"><span data-stu-id="7d664-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="7d664-110">Defina módulos em novos assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="7d664-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="7d664-111">Defina os tipos de módulos no tempo de execução, crie instâncias desses tipos e invoque seus métodos.</span><span class="sxs-lookup"><span data-stu-id="7d664-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="7d664-112">Identifique as informações simbólicas para módulos definidos que podem ser usadas por ferramentas como depuradores e criadores de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="7d664-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="7d664-113">Além dos tipos gerenciados no namespace <xref:System.Reflection.Emit>, há interfaces de metadados não gerenciados que são descritos na documentação de referência de [Interfaces de Metadados](../unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7d664-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="7d664-114">A emissão de reflexão gerenciada fornece verificação de erros semânticos mais potente e um nível mais alto de abstração de metadados que as interfaces de metadados não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="7d664-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="7d664-115">Outro recurso útil para trabalhar com metadados e MSIL é a documentação da CLI (Common Language Infrastructure), especialmente a “Partição II: definição e semântica de metadados” e a “Partição III: conjunto de instruções de CIL”.</span><span class="sxs-lookup"><span data-stu-id="7d664-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="7d664-116">A documentação está disponível online no [site da Ecma.](https://www.ecma-international.org/publications/standards/Ecma-335.htm)</span><span class="sxs-lookup"><span data-stu-id="7d664-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d664-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7d664-117">In This Section</span></span>
  
[<span data-ttu-id="7d664-118">Questões de segurança em reflexão emitidas</span><span class="sxs-lookup"><span data-stu-id="7d664-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="7d664-119">Descreve os problemas de segurança relacionados à criação de assemblies dinâmicos usando emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="7d664-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="7d664-120">[Como: Definir e executar métodos dinâmicos](how-to-define-and-execute-dynamic-methods.md) Mostra como executar um método dinâmico simples e um método dinâmico vinculado a uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="7d664-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="7d664-121">[Como: Definir um tipo genérico com reflexão emitida](how-to-define-a-generic-type-with-reflection-emit.md) Mostra como criar um tipo genérico simples com dois parâmetros de tipo, como aplicar classe, interface e restrições especiais aos parâmetros do tipo e como criar membros que usam os parâmetros de tipo da classe como tipos de parâmetros e tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="7d664-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="7d664-122">[Como: Definir um método genérico com reflexão emitida](how-to-define-a-generic-method-with-reflection-emit.md) Mostra como criar, emitir e invocar um método genérico simples.</span><span class="sxs-lookup"><span data-stu-id="7d664-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="7d664-123">[Montagens colecionáveis para geração de tipo dinâmico](collectible-assemblies.md) Introduz conjuntos colecionáveis, que são conjuntos dinâmicos que podem ser descarregados sem descarregar o domínio do aplicativo no qual foram criados.</span><span class="sxs-lookup"><span data-stu-id="7d664-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="7d664-124">Referência</span><span class="sxs-lookup"><span data-stu-id="7d664-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="7d664-125">Cataloga os códigos de instrução de MSIL, que você pode usar para criar corpos de método.</span><span class="sxs-lookup"><span data-stu-id="7d664-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="7d664-126">Contém classes gerenciadas usadas para emitir métodos, assemblies e tipos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="7d664-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="7d664-127">Descreve a classe <xref:System.Type>, que representa os tipos de reflexão gerenciada e emissão de reflexão, e qual é a chave para o uso dessas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="7d664-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="7d664-128">Contém classes gerenciadas usadas para explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7d664-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d664-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7d664-129">Related Sections</span></span>  

[<span data-ttu-id="7d664-130">Reflexão</span><span class="sxs-lookup"><span data-stu-id="7d664-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="7d664-131">Explica como explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7d664-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="7d664-132">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="7d664-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="7d664-133">Fornece uma visão geral dos assemblies em implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="7d664-133">Provides an overview of assemblies in .NET implementations.</span></span>
