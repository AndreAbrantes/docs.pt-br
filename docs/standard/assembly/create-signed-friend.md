---
title: Como criar assemblies Friend assinados
description: Este artigo mostra como usar os assemblies Friend com assemblies que têm nomes fortes. Ele inclui informações sobre a segurança do .NET.
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: b6176afed44e32911a37a0d753cea2bae7d8554e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378537"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="2078c-104">Como criar assemblies Friend assinados</span><span class="sxs-lookup"><span data-stu-id="2078c-104">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="2078c-105">Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="2078c-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="2078c-106">Os dois assemblies devem ter nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="2078c-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="2078c-107">Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="2078c-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="2078c-108">Criar um assembly assinado e um assembly Friend</span><span class="sxs-lookup"><span data-stu-id="2078c-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="2078c-109">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2078c-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="2078c-110">Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="2078c-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="2078c-111">Para obter mais informações, consulte [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="2078c-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="2078c-112">Gere uma chave de nome forte para este exemplo e armazene-a no arquivo *FriendAssemblies. SNK*:</span><span class="sxs-lookup"><span data-stu-id="2078c-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="2078c-113">Extraia a chave pública de *FriendAssemblies. SNK* e coloque-a em *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="2078c-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="2078c-114">Exiba a chave pública armazenada no arquivo *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="2078c-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="2078c-115">Crie um arquivo em C# ou Visual Basic chamado *friend_signed_A* que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2078c-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="2078c-116">O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo para declarar *friend_signed_B* como um assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="2078c-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="2078c-117">A ferramenta Nome Forte gera uma nova chave pública sempre que for executada.</span><span class="sxs-lookup"><span data-stu-id="2078c-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="2078c-118">Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2078c-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="2078c-119">Compile e assine *friend_signed_A* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2078c-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="2078c-120">Crie um arquivo em C# ou Visual Basic chamado *friend_signed_B* que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2078c-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="2078c-121">Como *friend_signed_A* especifica *friend_signed_B* como um assembly Friend, o código em *friend_signed_B* pode acessar `internal` `Friend` os tipos e os membros do (C#) ou (Visual Basic) de *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="2078c-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="2078c-122">O arquivo contém o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="2078c-122">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="2078c-123">Compile e assine *friend_signed_B* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2078c-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="2078c-124">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2078c-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2078c-125">Você deve especificar explicitamente o nome do assembly de saída (*. exe* ou *. dll*) usando a `-out` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="2078c-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="2078c-126">Para obter mais informações, consulte [-out (opções do compilador C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="2078c-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="2078c-127">Execute o arquivo *friend_signed_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="2078c-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="2078c-128">O programa gera a cadeia de caracteres **Class1. Test**.</span><span class="sxs-lookup"><span data-stu-id="2078c-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="2078c-129">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="2078c-129">.NET security</span></span>  
 <span data-ttu-id="2078c-130">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="2078c-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2078c-131">A principal diferença é que o <xref:System.Security.Permissions.StrongNameIdentityPermission> pode exigir que as permissões de segurança executem uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade de `internal` tipos e Membros (C#) ou `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2078c-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2078c-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="2078c-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="2078c-133">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="2078c-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="2078c-134">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="2078c-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="2078c-135">Como: criar assemblies Friend não assinados</span><span class="sxs-lookup"><span data-stu-id="2078c-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="2078c-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="2078c-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="2078c-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2078c-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="2078c-138">Sn. exe (ferramenta Strong Name)</span><span class="sxs-lookup"><span data-stu-id="2078c-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="2078c-139">Criar e usar assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="2078c-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="2078c-140">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="2078c-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2078c-141">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2078c-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
