---
title: Como criar wrappers manualmente
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: a7818a1c08d8538acfacb22dc270d7ef23a7a582
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181423"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="f8f58-102">Como criar wrappers manualmente</span><span class="sxs-lookup"><span data-stu-id="f8f58-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="f8f58-103">Se você decidir declarar tipos COM manualmente no código-fonte gerenciado, o melhor lugar para começar é com um arquivo de linguagem IDL ou uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="f8f58-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="f8f58-104">Quando você não tem o arquivo IDL ou não pode gerar um arquivo de biblioteca de tipos, pode simular os tipos COM criando declarações gerenciadas e exportando o assembly resultante para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f8f58-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="f8f58-105">Para simular tipos COM de uma fonte gerenciada</span><span class="sxs-lookup"><span data-stu-id="f8f58-105">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="f8f58-106">Declare os tipos em uma linguagem que está em conformidade com o CLS (Common Language Specification) e compile o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f8f58-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="f8f58-107">Exporte o assembly que contém os tipos com o [Exportador de Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="f8f58-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="f8f58-108">Use a biblioteca de tipos COM exportada como base para declarar tipos gerenciados orientados ao COM.</span><span class="sxs-lookup"><span data-stu-id="f8f58-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="f8f58-109">Para criar um RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="f8f58-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="f8f58-110">Supondo que você tenha um arquivo IDL ou um arquivo de biblioteca de tipos, decida quais classes e interfaces você deseja incluir no RCW personalizado.</span><span class="sxs-lookup"><span data-stu-id="f8f58-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="f8f58-111">Exclua todos os tipos que você não pretende usar direta ou indiretamente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f8f58-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="f8f58-112">Crie um arquivo de origem em uma linguagem em conformidade com CLS e declare os tipos.</span><span class="sxs-lookup"><span data-stu-id="f8f58-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="f8f58-113">Consulte [Resumo da conversão de bibliotecas de tipos em assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) para obter uma descrição completa do processo de conversão de importação.</span><span class="sxs-lookup"><span data-stu-id="f8f58-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="f8f58-114">Efetivamente, quando você cria um RCW (Runtime Callable Wrapper) personalizado, você está executando manualmente a atividade de conversão de tipo fornecida pelo [Importador da Biblioteca de Tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="f8f58-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f8f58-115">O exemplo na próxima seção mostra os tipos em um arquivo IDL ou de biblioteca de tipos e seus tipos correspondentes no código C#.</span><span class="sxs-lookup"><span data-stu-id="f8f58-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="f8f58-116">Quando as declarações forem concluídas, compile o arquivo como compilaria qualquer código-fonte gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8f58-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="f8f58-117">Assim como ocorre com os tipos importados com Tlbimp.exe, alguns exigem informações adicionais, que podem ser adicionadas diretamente ao código.</span><span class="sxs-lookup"><span data-stu-id="f8f58-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="f8f58-118">Para obter detalhes, consulte [Como editar assemblies de interoperabilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f8f58-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8f58-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8f58-119">Example</span></span>  
 <span data-ttu-id="f8f58-120">O código a seguir mostra um exemplo da interface `ISATest` e da classe `SATest` na IDL e os tipos correspondentes no código-fonte C#.</span><span class="sxs-lookup"><span data-stu-id="f8f58-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="f8f58-121">**Arquivo IDL ou de biblioteca de tipos**</span><span class="sxs-lookup"><span data-stu-id="f8f58-121">**IDL or type library file**</span></span>  
  
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
  
 <span data-ttu-id="f8f58-122">**Wrapper no código-fonte gerenciado**</span><span class="sxs-lookup"><span data-stu-id="f8f58-122">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8f58-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="f8f58-123">See also</span></span>

- <span data-ttu-id="f8f58-124">[Personalizando RCWs (Runtime Callable Wrappers)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8f58-124">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="f8f58-125">[Tipos de dados COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8f58-125">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="f8f58-126">[Como editar assemblies de interoperabilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8f58-126">[How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="f8f58-127">[Resumo da conversão de bibliotecas de tipos em assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8f58-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="f8f58-128">Tlbimp.exe (Importador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="f8f58-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="f8f58-129">Tlbexp.exe (Exportador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="f8f58-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
