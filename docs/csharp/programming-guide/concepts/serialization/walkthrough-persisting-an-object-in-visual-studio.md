---
title: 'Passo a passo: Persistindo um objeto usando o C#'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167564"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="08879-102">Passo a passo: persistir um objeto usando o C\#</span><span class="sxs-lookup"><span data-stu-id="08879-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="08879-103">Você pode usar a serialização para manter os dados de um objeto entre instâncias, o que permite armazenar valores e recuperá-los na próxima vez que o objeto for instanciado.</span><span class="sxs-lookup"><span data-stu-id="08879-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="08879-104">Neste passo a passo, você criará um objeto `Loan` básico e persistirá seus dados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="08879-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="08879-105">Em seguida, você recuperará os dados do arquivo quando recriar o objeto.</span><span class="sxs-lookup"><span data-stu-id="08879-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08879-106">Este exemplo criará um novo arquivo se o arquivo ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="08879-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="08879-107">Se um aplicativo precisar criar um arquivo, esse aplicativo precisará ter a permissão `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="08879-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="08879-108">Permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="08879-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="08879-109">Se o arquivo já existir, o aplicativo precisará somente da permissão `Write`, que é uma permissão menor.</span><span class="sxs-lookup"><span data-stu-id="08879-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="08879-110">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder permissões `Read` a um único arquivo (em vez das permissões Create para uma pasta).</span><span class="sxs-lookup"><span data-stu-id="08879-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="08879-111">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.</span><span class="sxs-lookup"><span data-stu-id="08879-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08879-112">Este exemplo armazena dados em um arquivo de formato binário.</span><span class="sxs-lookup"><span data-stu-id="08879-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="08879-113">Esses formatos não devem ser usados para dados confidenciais, como senhas ou informações de cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="08879-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08879-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="08879-114">Prerequisites</span></span>

- <span data-ttu-id="08879-115">Para criar e executar, instale o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="08879-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="08879-116">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="08879-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="08879-117">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="08879-117">Need to install a code editor?</span></span> <span data-ttu-id="08879-118">Experimente o [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="08879-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="08879-119">O exemplo exige C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="08879-119">The example requires C# 7.3.</span></span> <span data-ttu-id="08879-120">Confira [Selecionar a versão da linguagem C#](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="08879-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="08879-121">Examine o código de exemplo online [no repositório GitHub de amostras do .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="08879-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="08879-122">Criando o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="08879-122">Creating the loan object</span></span>

<span data-ttu-id="08879-123">A primeira etapa é criar uma classe `Loan` e um aplicativo de console que usa a classe:</span><span class="sxs-lookup"><span data-stu-id="08879-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="08879-124">Crie um aplicativo novo.</span><span class="sxs-lookup"><span data-stu-id="08879-124">Create a new application.</span></span> <span data-ttu-id="08879-125">Digite `dotnet new console -o serialization` para criar um novo aplicativo de console em um subdiretório chamado `serialization`.</span><span class="sxs-lookup"><span data-stu-id="08879-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="08879-126">Abra o aplicativo no editor e adicione uma nova classe chamada `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="08879-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="08879-127">Adicione o seguinte código à classe `Loan`:</span><span class="sxs-lookup"><span data-stu-id="08879-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="08879-128">Você também precisará criar um aplicativo que usa a classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="08879-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="08879-129">Serializar o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="08879-129">Serialize the loan object</span></span>

1. <span data-ttu-id="08879-130">Abra o `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="08879-130">Open `Program.cs`.</span></span> <span data-ttu-id="08879-131">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="08879-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="08879-132">Adicione um manipulador de eventos ao evento `PropertyChanged` e algumas linhas para modificar o objeto `Loan` e exibir as alterações.</span><span class="sxs-lookup"><span data-stu-id="08879-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="08879-133">Veja as adições no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="08879-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="08879-134">Neste ponto, você pode executar o código e ver a saída atual:</span><span class="sxs-lookup"><span data-stu-id="08879-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="08879-135">A execução desse aplicativo repetidamente grava os mesmos valores.</span><span class="sxs-lookup"><span data-stu-id="08879-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="08879-136">Um novo objeto Loan é criado sempre que o programa é executado.</span><span class="sxs-lookup"><span data-stu-id="08879-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="08879-137">No mundo real, as taxas de juros mudam periodicamente, mas não necessariamente toda vez que o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="08879-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="08879-138">Código de serialização significa preservar a taxa de juros mais recente entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08879-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="08879-139">Na próxima etapa, você fará exatamente isso adicionando a serialização à classe Loan.</span><span class="sxs-lookup"><span data-stu-id="08879-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="08879-140">Usando a serialização para manter o objeto</span><span class="sxs-lookup"><span data-stu-id="08879-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="08879-141">Para manter os valores da classe Loan, primeiro você deve marcar a classe com o atributo `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="08879-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="08879-142">Adicione o seguinte código acima da definição da classe Loan:</span><span class="sxs-lookup"><span data-stu-id="08879-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="08879-143">O <xref:System.SerializableAttribute> informa ao compilador que tudo na classe pode ser persistido em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="08879-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="08879-144">Como o evento `PropertyChanged` não representa a parte do grafo do objeto que deve ser armazenada, ele não deve ser serializado.</span><span class="sxs-lookup"><span data-stu-id="08879-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="08879-145">Ao fazer isso, todos os objetos anexados a esse evento serão serializados.</span><span class="sxs-lookup"><span data-stu-id="08879-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="08879-146">Adicione o <xref:System.NonSerializedAttribute> à declaração de campo do manipulador de eventos `PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="08879-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="08879-147">Do C# 7.3 em diante, você pode anexar atributos ao campo de suporte de uma propriedade autoimplementada usando o valor de destino `field`.</span><span class="sxs-lookup"><span data-stu-id="08879-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="08879-148">O seguinte código adiciona uma propriedade `TimeLastLoaded` e a marca como não serializável:</span><span class="sxs-lookup"><span data-stu-id="08879-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="08879-149">A etapa seguinte é adicionar o código de serialização ao aplicativo LoanApp.</span><span class="sxs-lookup"><span data-stu-id="08879-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="08879-150">Para serializar a classe e gravá-la em um arquivo, use os namespaces <xref:System.IO> e <xref:System.Runtime.Serialization.Formatters.Binary>.</span><span class="sxs-lookup"><span data-stu-id="08879-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="08879-151">Para evitar a digitação dos nomes totalmente qualificados, você pode adicionar referências aos namespaces necessários, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="08879-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="08879-152">A próxima etapa é adicionar código para desserializar o objeto do arquivo quando o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="08879-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="08879-153">Adicione uma constante à classe do nome de arquivo dos dados serializados, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="08879-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="08879-154">Em seguida, adicione o seguinte código após a linha que cria o objeto `TestLoan`:</span><span class="sxs-lookup"><span data-stu-id="08879-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="08879-155">Primeiro, é necessário verificar se o arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="08879-155">You first must check that the file exists.</span></span> <span data-ttu-id="08879-156">Se ele existir, crie uma classe <xref:System.IO.Stream> para ler o arquivo binário e uma classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para converter o arquivo.</span><span class="sxs-lookup"><span data-stu-id="08879-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="08879-157">Você também precisa converter do tipo de fluxo para o tipo de objeto Loan.</span><span class="sxs-lookup"><span data-stu-id="08879-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="08879-158">Em seguida, é necessário adicionar um código para serializar a classe em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="08879-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="08879-159">Adicione o seguinte código após o código existente no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="08879-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="08879-160">Neste ponto, você pode compilar e executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="08879-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="08879-161">Na primeira vez em que ele é executado, observe que as taxas de juros começam em 7,5 e, em seguida, são alteradas para 7,1.</span><span class="sxs-lookup"><span data-stu-id="08879-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="08879-162">Feche o aplicativo e execute-o novamente.</span><span class="sxs-lookup"><span data-stu-id="08879-162">Close the application and then run it again.</span></span> <span data-ttu-id="08879-163">Agora, o aplicativo imprime a mensagem indicando que ele leu o arquivo salvo e a taxa de juros é 7,1, mesmo antes do código que a altera.</span><span class="sxs-lookup"><span data-stu-id="08879-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="08879-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="08879-164">See also</span></span>

- [<span data-ttu-id="08879-165">Serialização (C#)</span><span class="sxs-lookup"><span data-stu-id="08879-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="08879-166">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="08879-166">C# Programming Guide</span></span>](../..//index.md)
