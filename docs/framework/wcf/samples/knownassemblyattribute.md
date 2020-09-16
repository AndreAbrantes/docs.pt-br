---
title: KnownAssemblyAttribute
ms.date: 03/30/2017
ms.assetid: b3bc7f31-95ff-46e1-8308-d206ec426f6e
ms.openlocfilehash: 12f28f44b408dde1ea04d6b84e663206cb4437df
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555400"
---
# <a name="knownassemblyattribute"></a><span data-ttu-id="4870d-102">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="4870d-102">KnownAssemblyAttribute</span></span>
<span data-ttu-id="4870d-103">Este exemplo demonstra como os processos de serialização e desserialização podem ser personalizados usando a <xref:System.Runtime.Serialization.DataContractResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="4870d-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="4870d-104">Este exemplo mostra como adicionar tipos conhecidos dinamicamente durante a serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="4870d-104">This sample shows how to dynamically add known types during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4870d-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="4870d-105">Sample Details</span></span>  
 <span data-ttu-id="4870d-106">Este exemplo é composto de quatro projetos.</span><span class="sxs-lookup"><span data-stu-id="4870d-106">This sample is composed of four projects.</span></span> <span data-ttu-id="4870d-107">Um deles corresponde ao serviço, para ser hospedado pelo IIS, que define o seguinte contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="4870d-107">One of them corresponds to the service, to be hosted by IIS, which defines the following service contract.</span></span>  
  
```csharp
// Definition of a service contract.  
[ServiceContract(Namespace = "http://Microsoft.Samples.KAA")]  
[KnownAssembly("Types")]  
public interface IDataContractCalculator  
 {  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2);  
}  
```  
  
 <span data-ttu-id="4870d-108">O contrato de serviço é implementado conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4870d-108">The service contract is implemented as shown in the following example.</span></span>  
  
```csharp
// Service class that implements the service contract.  
 public class DataContractCalculatorService : IDataContractCalculator  
 {  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real, n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real, n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
  
        return new ComplexNumber(real1 + real2, imaginary1 + imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real, -1 * n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
  
        return new ComplexNumber(numerator.Real / denominator.Real, numerator.Imaginary);  
    }  
  
    public List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2)  
    {  
        List<ComplexNumber> result  = new List<ComplexNumber>();  
        result.AddRange(list1);  
        result.AddRange(list2);  
  
        return result;  
    }  
}  
```  
  
 <span data-ttu-id="4870d-109">Outro projeto corresponde ao cliente, que se comunica com o servidor e invoca os métodos que ele expõe.</span><span class="sxs-lookup"><span data-stu-id="4870d-109">Another project corresponds to the client, which communicates with the server and invokes the methods that it exposes.</span></span> <span data-ttu-id="4870d-110">A definição do cliente é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4870d-110">The definition of the client is shown in the following example.</span></span>  
  
```csharp  
 // Client implementation code.  
 class Client  
 {  
    static void Main()  
    {  
        // Create a channel.  
         EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc/IDataContractCalculator");  
        BasicHttpBinding binding = new BasicHttpBinding();  
        ChannelFactory<IDataContractCalculator> factory = new ChannelFactory<IDataContractCalculator>(binding, address);  
        IDataContractCalculator channel = factory.CreateChannel();  
  
        // Call the Add service operation.  
         ComplexNumber value1 = new ComplexNumber(1, 2);  
        ComplexNumber value2 = new ComplexNumberWithMagnitude(3, 4);  
        ComplexNumber result = channel.Add(value1, value2);  
        Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Subtract service operation.  
         value1 = new ComplexNumber(1, 2);  
        value2 = new ComplexNumber(3, 4);  
        result = channel.Subtract(value1, value2);  
        Console.WriteLine("Subtract({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Multiply service operation.  
         value1 = new ComplexNumber(2, 3);  
        value2 = new ComplexNumber(4, 7);  
        result = channel.Multiply(value1, value2);  
        Console.WriteLine("Multiply({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Divide service operation.  
         value1 = new ComplexNumber(3, 7);  
        value2 = new ComplexNumber(5, -2);  
        result = channel.Divide(value1, value2);  
        Console.WriteLine("Divide({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the CombineLists service operation.  
         List<ComplexNumber> list1 = new List<ComplexNumber>();  
        List<ComplexNumber> list2 = new List<ComplexNumber>();  
        list1.Add(new ComplexNumber(1, 1));  
        list1.Add(new ComplexNumber(2, 2));  
        list1.Add(new ComplexNumberWithMagnitude(3, 3));  
        list1.Add(new ComplexNumberWithMagnitude(4, 4));  
        List<ComplexNumber> listResult = channel.CombineLists(list1, list2);  
        Console.WriteLine("Lists combined:");  
        foreach (ComplexNumber n in listResult)  
        {  
            Console.WriteLine("{0} + {1}i", n.Real, n.Imaginary);  
        }  
        Console.WriteLine();  
  
        // Close the channel  
         ((IChannel)channel).Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="4870d-111">A definição do contrato de serviço é marcada com o `KnownAssembly` atributo.</span><span class="sxs-lookup"><span data-stu-id="4870d-111">The definition of the service contract is marked with the `KnownAssembly` attribute.</span></span> <span data-ttu-id="4870d-112">Esse atributo contém o nome de uma biblioteca de tipos, que todos se tornam conhecidos em tempo de execução tanto pelo serviço quanto pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="4870d-112">This attribute contains the name of a library of types, which all become known at runtime by both the service and the client.</span></span>  
  
 <span data-ttu-id="4870d-113">O `KnownAssembly` atributo implementa para `IContractBehavior` definir um `DataContractSerializer` com um `DataContractResolver` definido para cada um dos comportamentos de operação.</span><span class="sxs-lookup"><span data-stu-id="4870d-113">The `KnownAssembly` attribute implements `IContractBehavior` in order to define a `DataContractSerializer` with a `DataContractResolver` defined for each of the operation behaviors.</span></span> <span data-ttu-id="4870d-114">O `DataContractResolver` reflete sobre o assembly quando ele é criado e cria o dicionário com o mapeamento entre os tipos e nomes a serem usados ao serializar e desserializar os diferentes tipos.</span><span class="sxs-lookup"><span data-stu-id="4870d-114">The `DataContractResolver` reflects over the assembly when it is created, and creates the dictionary with the mapping between types and names to be used when serializing and deserializing the different types.</span></span> <span data-ttu-id="4870d-115">Dessa forma, os `ResolveType` tipos e `ResolveName` devem Pesquisar os dados necessários no dicionário.</span><span class="sxs-lookup"><span data-stu-id="4870d-115">In that way, the `ResolveType` and `ResolveName` types must look up the data required in the dictionary.</span></span>  
  
 <span data-ttu-id="4870d-116">O `DataContractResolver` definido para este exemplo é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4870d-116">The `DataContractResolver` defined for this sample is shown in the following example.</span></span>  
  
```csharp
public class MyDataContractResolver : DataContractResolver  
    {  
       Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();  
       Assembly assembly;  
  
       public MyDataContractResolver(string assemblyName)  
       {  
           this.KnownTypes = new List<Type>();  
  
           assembly = Assembly.Load(new AssemblyName(assemblyName));  
           foreach (Type type in assembly.GetTypes())  
           {  
               bool knownTypeFound = false;  
               System.Attribute[] attrs = System.Attribute.GetCustomAttributes(type);  
               if (attrs.Length != 0)  
               {  
                   foreach (System.Attribute attr in attrs)  
                   {  
                       if (attr is KnownTypeAttribute)  
                       {  
                           Type t = ((KnownTypeAttribute)attr).Type;  
                           if (this.KnownTypes.IndexOf(t) < 0)  
                           {  
                               this.KnownTypes.Add(t);  
                           }  
                           knownTypeFound = true;  
                       }  
                   }  
               }  
               if (!knownTypeFound)  
               {  
                   string name = type.Name;  
                   string namesp = type.Namespace;  
                   if (!dictionary.ContainsKey(name))  
                   {  
                       dictionary.Add(name, new XmlDictionaryString(XmlDictionary.Empty, name, 0));  
                   }  
                   if (!dictionary.ContainsKey(namesp))  
                   {  
                       dictionary.Add(namesp, new XmlDictionaryString(XmlDictionary.Empty, namesp, 0));  
                   }  
               }  
           }  
       }  
  
       public IList<Type> KnownTypes  
       {  
           get; set;  
       }  
  
       // Used at deserialization  
        // Allows users to map xsi:type name to any Type
        public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
       {  
           XmlDictionaryString tName;  
           XmlDictionaryString tNamespace;  
  
           if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))  
           {  
               return this.assembly.GetType(tNamespace.Value + "." + tName.Value);  
           }  
           else  
            {  
               return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
           }  
       }  
  
       // Used at serialization  
        // Maps any Type to a new xsi:type representation  
        public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
       {  
           knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
           if (typeName == null || typeNamespace == null)  
           {  
               typeName = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Name, 0);  
               typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Namespace, 0);  
           }  
       }  
   }  
```  
  
 <span data-ttu-id="4870d-117">A biblioteca de tipos usados neste exemplo é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4870d-117">The library of types used in this sample is shown in the following example.</span></span>  
  
```csharp
 [DataContract]  
 public class ComplexNumber  
 {  
    [DataMember]  
    private double real;  
  
    [DataMember]  
    private double imaginary;  
  
    public ComplexNumber(double r1, double i1)  
    {  
        this.Real = r1;  
        this.Imaginary = i1;  
    }  
  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
}  
  
[DataContract]  
public class ComplexNumberWithMagnitude : ComplexNumber  
 {  
    public ComplexNumberWithMagnitude(double real, double imaginary) : base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary * Imaginary + Real * Real); }  
        set { }  
    }  
}  
```  
  
 <span data-ttu-id="4870d-118">Observe que `ComplexNumber` o não precisa saber estaticamente o `ComplexNumberWithMagnitude` tipo, pois ele se torna conhecido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4870d-118">Note that `ComplexNumber` does not need to statically know the `ComplexNumberWithMagnitude` type, because it becomes known at runtime.</span></span>  
  
 <span data-ttu-id="4870d-119">Quando o exemplo é compilado e executado, essa é a saída esperada obtida no cliente:</span><span class="sxs-lookup"><span data-stu-id="4870d-119">When the sample is built and executed, this is the expected output obtained in the client:</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
Lists combined:  
1 + 1i  
2 + 2i  
3 + 3i  
4 + 4i  
```  
  
#### <a name="to-set-up-run-and-build-the-sample"></a><span data-ttu-id="4870d-120">Para configurar, executar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4870d-120">To set up, run, and build the sample</span></span>  
  
1. <span data-ttu-id="4870d-121">Clique com o botão direito do mouse na solução **KnownAssemblyAttribute** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4870d-121">Right-click the solution **KnownAssemblyAttribute** and select **Properties**.</span></span>  
  
2. <span data-ttu-id="4870d-122">Em **Propriedades comuns**, selecione **projeto de inicialização**e clique em **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="4870d-122">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
3. <span data-ttu-id="4870d-123">Adicione a ação **Iniciar** aos projetos **serviço** e **cliente** .</span><span class="sxs-lookup"><span data-stu-id="4870d-123">Add the **Start** action to the **Service** and **Client** projects.</span></span>  
  
4. <span data-ttu-id="4870d-124">Clique em **OK**e pressione **F5** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="4870d-124">Click **OK**, and press **F5** to run the sample.</span></span>  
  
5. <span data-ttu-id="4870d-125">Se o aplicativo não for executado corretamente, siga estas etapas para verificar se o seu ambiente foi configurado corretamente:</span><span class="sxs-lookup"><span data-stu-id="4870d-125">If the application does not run properly, follow these steps to make sure your environment has been properly set up:</span></span>  
  
6. <span data-ttu-id="4870d-126">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](./one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4870d-126">Ensure that you have performed the [One-Time Set Up Procedure for the Windows Communication Foundation Samples](./one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
7. <span data-ttu-id="4870d-127">Para criar a solução, siga as instruções em [criando o Windows Communication Foundation exemplo](./building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4870d-127">To build the solution, follow the instructions in [Building the Windows Communication Foundation Sample](./building-the-samples.md).</span></span>  
  
8. <span data-ttu-id="4870d-128">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](./running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4870d-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](./running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4870d-129">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4870d-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4870d-130">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4870d-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4870d-131">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4870d-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4870d-132">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4870d-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownAssemblyAttribute`
