---
title: Assinar um assembly com atraso
description: Este artigo descreve a assinatura atrasada ou parcial, que reserva espaço no arquivo PE para a assinatura de nome forte, mas adia a assinatura real.
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 7b5c8c8463fdc573782fa457bf5671c72a7e25f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378499"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="e01bd-103">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="e01bd-103">Delay-sign an assembly</span></span>

<span data-ttu-id="e01bd-104">Uma organização pode ter um par de chaves bem protegido que os desenvolvedores não podem acessar diariamente.</span><span class="sxs-lookup"><span data-stu-id="e01bd-104">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="e01bd-105">A chave pública normalmente está disponível, mas o acesso à chave privada é restrito a apenas algumas pessoas.</span><span class="sxs-lookup"><span data-stu-id="e01bd-105">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="e01bd-106">Ao desenvolver assemblies com nomes fortes, cada assembly que referencia o assembly de destino com nome forte contém o token da chave pública usada para fornecer ao assembly de destino um nome forte.</span><span class="sxs-lookup"><span data-stu-id="e01bd-106">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="e01bd-107">Isso requer que a chave pública esteja disponível durante o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e01bd-107">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="e01bd-108">Você pode usar a assinatura atrasada ou parcial no momento da compilação para reservar espaço no arquivo executável portátil (PE) para a assinatura de nome forte, mas adiar a assinatura real até algum estágio posterior, geralmente antes de enviar o assembly.</span><span class="sxs-lookup"><span data-stu-id="e01bd-108">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="e01bd-109">Para assinar um assembly com atraso:</span><span class="sxs-lookup"><span data-stu-id="e01bd-109">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="e01bd-110">Obtenha a parte da chave pública do par de chaves da organização que fará a assinatura eventual.</span><span class="sxs-lookup"><span data-stu-id="e01bd-110">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="e01bd-111">Normalmente, essa chave está na forma de um arquivo *. SNK* , que pode ser criado usando a [ferramenta de nome forte (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) fornecida pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="e01bd-111">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="e01bd-112">Anote o código-fonte para o assembly com dois atributos personalizados de <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="e01bd-112">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="e01bd-113"><xref:System.Reflection.AssemblyKeyFileAttribute>, que passa o nome do arquivo que contém a chave pública como um parâmetro para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="e01bd-113"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="e01bd-114"><xref:System.Reflection.AssemblyDelaySignAttribute>, que indica que o atraso da assinatura está sendo usado passando **true** como um parâmetro para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="e01bd-114"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="e01bd-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e01bd-115">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="e01bd-116">O compilador insere a chave pública no manifesto do assembly e reserva espaço no arquivo PE para a assinatura de nome forte completo.</span><span class="sxs-lookup"><span data-stu-id="e01bd-116">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="e01bd-117">A chave pública real deve ser armazenada enquanto o assembly é compilado para que outros assemblies que referenciam esse assembly possam obter a chave para armazenar em sua própria referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="e01bd-117">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="e01bd-118">Como o assembly não tem uma assinatura de nome forte válida, a verificação dessa assinatura deve ser desativada.</span><span class="sxs-lookup"><span data-stu-id="e01bd-118">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="e01bd-119">Você pode fazer isso usando a opção **– Vr** com a ferramenta Nome Forte.</span><span class="sxs-lookup"><span data-stu-id="e01bd-119">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="e01bd-120">O exemplo a seguir desativa a verificação para um assembly chamado *myAssembly. dll*.</span><span class="sxs-lookup"><span data-stu-id="e01bd-120">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="e01bd-121">Para desligar a verificação em plataformas em que você não pode executar a ferramenta Nome Forte, como microprocessadores ARM (Advanced RISC Machine), use a opção **–Vk** para criar um arquivo de Registro.</span><span class="sxs-lookup"><span data-stu-id="e01bd-121">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="e01bd-122">Importe o arquivo de Registro para o Registro no computador em que você deseja desligar a verificação.</span><span class="sxs-lookup"><span data-stu-id="e01bd-122">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="e01bd-123">O exemplo a seguir cria um arquivo de Registro para `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e01bd-123">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="e01bd-124">Com a opção **– VR** ou **– VK** , você pode, opcionalmente, incluir um arquivo *. SNK* para assinatura de chave de teste.</span><span class="sxs-lookup"><span data-stu-id="e01bd-124">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="e01bd-125">Por segurança, não confie em nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="e01bd-125">Do not rely on strong names for security.</span></span> <span data-ttu-id="e01bd-126">Eles apenas fornecem uma identidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="e01bd-126">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e01bd-127">Se você usar o atraso de assinatura durante o desenvolvimento com o Visual Studio em um computador de 64 bits e compilar um assembly para **Qualquer CPU**, talvez seja necessário aplicar a opção **-Vr** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="e01bd-127">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="e01bd-128">(No Visual Studio, **qualquer CPU** é um valor da propriedade de compilação de **destino de plataforma** ; quando você compila a partir da linha de comando, é o padrão.) Para executar o aplicativo na linha de comando ou no explorador de arquivos, use a versão de 64 bits do [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md) para aplicar a opção **-VR** ao assembly.</span><span class="sxs-lookup"><span data-stu-id="e01bd-128">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="e01bd-129">Para carregar o assembly no Visual Studio no tempo de design (por exemplo, se o assembly contiver componentes que são usados por outros assemblies em seu aplicativo), use a versão de 32 bits da ferramenta de nome forte.</span><span class="sxs-lookup"><span data-stu-id="e01bd-129">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="e01bd-130">Isso ocorre porque o compilador JIT (Just-in-time) compila o assembly para código nativo de 64 bits quando o assembly é executado da linha de comando e para código nativo de 32 bits quando o assembly é carregado no ambiente de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e01bd-130">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="e01bd-131">Posteriormente, normalmente imediatamente antes do envio, você envia o assembly para a autoridade de assinatura da sua organização para a assinatura de nome forte real usando a opção **–R** com a ferramenta Nome Forte.</span><span class="sxs-lookup"><span data-stu-id="e01bd-131">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="e01bd-132">O exemplo a seguir assina um assembly chamado *myAssembly. dll* com um nome forte usando o par de chaves *sgKey. SNK* .</span><span class="sxs-lookup"><span data-stu-id="e01bd-132">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="e01bd-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="e01bd-133">See also</span></span>

- [<span data-ttu-id="e01bd-134">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="e01bd-134">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="e01bd-135">Como criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="e01bd-135">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="e01bd-136">Sn. exe (ferramenta Strong Name)</span><span class="sxs-lookup"><span data-stu-id="e01bd-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
