---
title: 'Como: Criar wrappers manualmente'
description: Crie wrappers de tipos COM manualmente. Use um arquivo IDL existente ou biblioteca de tipos, ou crie declarações gerenciadas e exporte o assembly para uma biblioteca de tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: 0321e98e6237e54397db7e583546fd69803ab7e1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275951"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="fb673-104">Como: Criar wrappers manualmente</span><span class="sxs-lookup"><span data-stu-id="fb673-104">How to: Create Wrappers Manually</span></span>

<span data-ttu-id="fb673-105">Se você decidir declarar tipos COM manualmente no código-fonte gerenciado, o melhor lugar para começar é com um arquivo de linguagem IDL ou uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="fb673-105">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="fb673-106">Quando você não tem o arquivo IDL ou não pode gerar um arquivo de biblioteca de tipos, pode simular os tipos COM criando declarações gerenciadas e exportando o assembly resultante para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="fb673-106">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="fb673-107">Para simular tipos COM de uma fonte gerenciada</span><span class="sxs-lookup"><span data-stu-id="fb673-107">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="fb673-108">Declare os tipos em uma linguagem que está em conformidade com o CLS (Common Language Specification) e compile o arquivo.</span><span class="sxs-lookup"><span data-stu-id="fb673-108">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="fb673-109">Exporte o assembly que contém os tipos com o [Exportador de Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="fb673-109">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="fb673-110">Use a biblioteca de tipos COM exportada como base para declarar tipos gerenciados orientados ao COM.</span><span class="sxs-lookup"><span data-stu-id="fb673-110">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="fb673-111">Para criar um RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="fb673-111">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="fb673-112">Supondo que você tenha um arquivo IDL ou um arquivo de biblioteca de tipos, decida quais classes e interfaces você deseja incluir no RCW personalizado.</span><span class="sxs-lookup"><span data-stu-id="fb673-112">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="fb673-113">Exclua todos os tipos que você não pretende usar direta ou indiretamente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb673-113">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="fb673-114">Crie um arquivo de origem em uma linguagem em conformidade com CLS e declare os tipos.</span><span class="sxs-lookup"><span data-stu-id="fb673-114">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="fb673-115">Consulte [Resumo da conversão de bibliotecas de tipos em assemblies](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) para obter uma descrição completa do processo de conversão de importação.</span><span class="sxs-lookup"><span data-stu-id="fb673-115">See [Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="fb673-116">Efetivamente, quando você cria um RCW (Runtime Callable Wrapper) personalizado, você está executando manualmente a atividade de conversão de tipo fornecida pelo [Importador da Biblioteca de Tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="fb673-116">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="fb673-117">O exemplo na próxima seção mostra os tipos em um arquivo IDL ou de biblioteca de tipos e seus tipos correspondentes no código C#.</span><span class="sxs-lookup"><span data-stu-id="fb673-117">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="fb673-118">Quando as declarações forem concluídas, compile o arquivo como compilaria qualquer código-fonte gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fb673-118">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="fb673-119">Assim como ocorre com os tipos importados com Tlbimp.exe, alguns exigem informações adicionais, que podem ser adicionadas diretamente ao código.</span><span class="sxs-lookup"><span data-stu-id="fb673-119">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="fb673-120">Para obter detalhes, consulte [Como editar assemblies de interoperabilidade](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fb673-120">For details, see [How to: Edit Interop Assemblies](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb673-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb673-121">Example</span></span>  

 <span data-ttu-id="fb673-122">O código a seguir mostra um exemplo da interface `ISATest` e da classe `SATest` na IDL e os tipos correspondentes no código-fonte C#.</span><span class="sxs-lookup"><span data-stu-id="fb673-122">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="fb673-123">**Arquivo IDL ou de biblioteca de tipos**</span><span class="sxs-lookup"><span data-stu-id="fb673-123">**IDL or type library file**</span></span>  
  
```cpp
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="fb673-124">**Wrapper no código-fonte gerenciado**</span><span class="sxs-lookup"><span data-stu-id="fb673-124">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb673-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="fb673-125">See also</span></span>

- <span data-ttu-id="fb673-126">[Personalizando RCWs (Runtime Callable Wrappers)](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb673-126">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="fb673-127">[Tipos de dados COM](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb673-127">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="fb673-128">[Como editar assemblies de interoperabilidade](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb673-128">[How to: Edit Interop Assemblies](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="fb673-129">[Resumo da conversão de bibliotecas de tipos em assemblies](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fb673-129">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="fb673-130">Tlbimp.exe (Importador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="fb673-130">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="fb673-131">Tlbexp.exe (Exportador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="fb673-131">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
