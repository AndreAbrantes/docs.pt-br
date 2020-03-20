---
title: Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144976"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="04c2c-102">Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="04c2c-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="04c2c-103">Esta amostra demonstra como <xref:System.Runtime.Serialization.DataContractSerializer> o <xref:System.Runtime.Serialization.DataContractResolver> uso de um <xref:System.Runtime.Serialization.NetDataContractSerializer>apropriado fornece a mesma funcionalidade que .</span><span class="sxs-lookup"><span data-stu-id="04c2c-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="04c2c-104">Esta amostra mostra como <xref:System.Runtime.Serialization.DataContractResolver> criar o apropriado e <xref:System.Runtime.Serialization.DataContractSerializer>como adicioná-lo ao .</span><span class="sxs-lookup"><span data-stu-id="04c2c-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="04c2c-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="04c2c-105">Sample details</span></span>
 <span data-ttu-id="04c2c-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>difere de <xref:System.Runtime.Serialization.DataContractSerializer> uma forma <xref:System.Runtime.Serialization.NetDataContractSerializer> importante: inclui informações do tipo CLR no <xref:System.Runtime.Serialization.DataContractSerializer> XML serializado, enquanto não.</span><span class="sxs-lookup"><span data-stu-id="04c2c-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="04c2c-107">Portanto, <xref:System.Runtime.Serialization.NetDataContractSerializer> só pode ser usado se as extremidades serializadora e desserializadora compartilharem os mesmos tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="04c2c-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="04c2c-108">No entanto, recomenda-se usar <xref:System.Runtime.Serialization.DataContractSerializer> porque <xref:System.Runtime.Serialization.NetDataContractSerializer>seu desempenho é melhor do que .</span><span class="sxs-lookup"><span data-stu-id="04c2c-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="04c2c-109">Você pode alterar as informações <xref:System.Runtime.Serialization.DataContractSerializer> que são <xref:System.Runtime.Serialization.DataContractResolver> serializadas adicionando a ela.</span><span class="sxs-lookup"><span data-stu-id="04c2c-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="04c2c-110">Esta amostra consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="04c2c-110">This sample consists of two projects.</span></span> <span data-ttu-id="04c2c-111">O primeiro <xref:System.Runtime.Serialization.NetDataContractSerializer> projeto usa para serializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="04c2c-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="04c2c-112">O segundo <xref:System.Runtime.Serialization.DataContractSerializer> projeto <xref:System.Runtime.Serialization.DataContractResolver> usa com a para fornecer a mesma funcionalidade do primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="04c2c-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="04c2c-113">O exemplo de código a <xref:System.Runtime.Serialization.DataContractResolver> seguir `MyDataContractResolver` mostra a <xref:System.Runtime.Serialization.DataContractSerializer> implementação de um personalizado nomeado que é adicionado ao projeto DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="04c2c-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        type ??= Type.GetType(typeName + ", " + typeNamespace);
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="04c2c-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="04c2c-114">To use this sample</span></span>

1. <span data-ttu-id="04c2c-115">Usando o Visual Studio 2012, abra o arquivo de solução DCRSample.sLn.</span><span class="sxs-lookup"><span data-stu-id="04c2c-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="04c2c-116">Clique com o botão direito do mouse no arquivo da solução e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="04c2c-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="04c2c-117">Na caixa de diálogo Páginas de propriedade de **solução,** em **Propriedades Comuns,** **Projeto de Inicialização,** selecione **Vários projetos de inicialização:**.</span><span class="sxs-lookup"><span data-stu-id="04c2c-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="04c2c-118">Ao lado do projeto **DCSwithDCR,** **selecione Iniciar** a partir da parada **Ação.**</span><span class="sxs-lookup"><span data-stu-id="04c2c-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="04c2c-119">Ao lado do projeto **NetDCS,** **selecione Iniciar** a partir da parada **Ação.**</span><span class="sxs-lookup"><span data-stu-id="04c2c-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="04c2c-120">Clique em **OK** para fechar o diálogo.</span><span class="sxs-lookup"><span data-stu-id="04c2c-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="04c2c-121">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="04c2c-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="04c2c-122">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="04c2c-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04c2c-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="04c2c-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04c2c-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="04c2c-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="04c2c-125">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="04c2c-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04c2c-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="04c2c-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
