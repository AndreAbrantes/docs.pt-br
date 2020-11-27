---
title: Usando a Biblioteca de Classes Portátil com Modelo MVVM
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: e8bce469fd09de02ef6ab30e21ae20a9b9f71325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259265"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="5debe-102">Usando a Biblioteca de Classes Portátil com Modelo MVVM</span><span class="sxs-lookup"><span data-stu-id="5debe-102">Using Portable Class Library with Model-View-View Model</span></span>

<span data-ttu-id="5debe-103">Você pode usar a .NET Framework [biblioteca de classes portátil](portable-class-library.md) para implementar o padrão MVVM (Model-View-View Model) e compartilhar assemblies em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="5debe-103">You can use the .NET Framework [Portable Class Library](portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="5debe-104">MVVM é um padrão de aplicativo que isola a interface do usuário da lógica de negócios subjacente.</span><span class="sxs-lookup"><span data-stu-id="5debe-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="5debe-105">Você pode implementar as classes modelo e exibir modelo em um projeto de biblioteca de classes portátil no Visual Studio 2012 e, em seguida, criar exibições que são personalizadas para diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="5debe-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="5debe-106">Essa abordagem permite que você grave o modelo de dados e a lógica de negócios somente uma vez e use esse código em aplicativos de .NET Framework, Silverlight, Windows Phone e Windows 8. x da loja, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="5debe-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Mostra a biblioteca de classes portátil com o MVVM Sharing assemblies entre plataformas.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="5debe-108">Este tópico não fornece informações gerais sobre o padrão MVVM.</span><span class="sxs-lookup"><span data-stu-id="5debe-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="5debe-109">Ele fornece apenas informações sobre como usar a biblioteca de classes portátil para implementar o MVVM.</span><span class="sxs-lookup"><span data-stu-id="5debe-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="5debe-110">Para obter mais informações sobre o MVVM, consulte o [MVVM QuickStart usando a biblioteca Prism 5,0 para WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="5debe-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="5debe-111">Classes que dão suporte a MVVM</span><span class="sxs-lookup"><span data-stu-id="5debe-111">Classes That Support MVVM</span></span>

 <span data-ttu-id="5debe-112">Quando você direciona o .NET Framework 4,5, .NET para aplicativos da loja do Windows 8. x, Silverlight ou Windows Phone 7,5 para seu projeto de biblioteca de classes portátil, as seguintes classes estão disponíveis para implementar o padrão MVVM:</span><span class="sxs-lookup"><span data-stu-id="5debe-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="5debe-113">Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-114">Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-115">Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-116">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-117">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-118">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-119">Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-120">Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-121">Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-122">Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5debe-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="5debe-123">Todas as classes no <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span><span class="sxs-lookup"><span data-stu-id="5debe-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="5debe-124">Implementando o MVVM</span><span class="sxs-lookup"><span data-stu-id="5debe-124">Implementing MVVM</span></span>

 <span data-ttu-id="5debe-125">Para implementar o MVVM, você normalmente cria o modelo e o modelo de exibição em um projeto de biblioteca de classes portátil, pois um projeto de biblioteca de classes portátil não pode fazer referência a um projeto não portátil.</span><span class="sxs-lookup"><span data-stu-id="5debe-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="5debe-126">O modelo e o modelo de exibição podem estar no mesmo projeto ou em projetos separados.</span><span class="sxs-lookup"><span data-stu-id="5debe-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="5debe-127">Se você usar projetos separados, adicione uma referência do projeto de modelo de exibição ao projeto de modelo.</span><span class="sxs-lookup"><span data-stu-id="5debe-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="5debe-128">Depois de compilar o modelo e exibir projetos de modelo, você faz referência a esses assemblies no aplicativo que contém a exibição.</span><span class="sxs-lookup"><span data-stu-id="5debe-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="5debe-129">Se a exibição interage apenas com o modelo de exibição, você só precisa referenciar o assembly que contém o modelo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5debe-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="5debe-130">Modelar</span><span class="sxs-lookup"><span data-stu-id="5debe-130">Model</span></span>

 <span data-ttu-id="5debe-131">O exemplo a seguir mostra uma classe de modelo simplificada que pode residir em um projeto de biblioteca de classes portátil.</span><span class="sxs-lookup"><span data-stu-id="5debe-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="5debe-132">O exemplo a seguir mostra uma maneira simples de popular, recuperar e atualizar os dados em um projeto de biblioteca de classes portátil.</span><span class="sxs-lookup"><span data-stu-id="5debe-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="5debe-133">Em um aplicativo real, você recuperaria os dados de uma fonte, como um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5debe-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="5debe-134">Exibir modelo</span><span class="sxs-lookup"><span data-stu-id="5debe-134">View Model</span></span>

 <span data-ttu-id="5debe-135">Uma classe base para modelos de exibição é frequentemente adicionada ao implementar o padrão MVVM.</span><span class="sxs-lookup"><span data-stu-id="5debe-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="5debe-136">O exemplo a seguir mostra uma classe base.</span><span class="sxs-lookup"><span data-stu-id="5debe-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="5debe-137">Uma implementação da <xref:System.Windows.Input.ICommand> interface é frequentemente usada com o padrão MVVM.</span><span class="sxs-lookup"><span data-stu-id="5debe-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="5debe-138">O exemplo a seguir mostra uma implementação da interface <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="5debe-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="5debe-139">O exemplo a seguir mostra um modelo de exibição simplificado.</span><span class="sxs-lookup"><span data-stu-id="5debe-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="5debe-140">Visualizar</span><span class="sxs-lookup"><span data-stu-id="5debe-140">View</span></span>  

 <span data-ttu-id="5debe-141">De um aplicativo .NET Framework 4,5, aplicativo da loja do Windows 8. x, aplicativo baseado no Silverlight ou Windows Phone aplicativo 7,5, você pode fazer referência ao assembly que contém os projetos modelo e exibir modelo.</span><span class="sxs-lookup"><span data-stu-id="5debe-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="5debe-142">Em seguida, você cria um modo de exibição que interage com o modelo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5debe-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="5debe-143">O exemplo a seguir mostra um aplicativo de Windows Presentation Foundation simplificado (WPF) que recupera e atualiza dados do modelo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5debe-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="5debe-144">Você pode criar exibições semelhantes nos aplicativos do Silverlight, Windows Phone ou Windows 8. x da loja.</span><span class="sxs-lookup"><span data-stu-id="5debe-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5debe-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="5debe-145">See also</span></span>

- [<span data-ttu-id="5debe-146">Biblioteca de Classes Portátil</span><span class="sxs-lookup"><span data-stu-id="5debe-146">Portable Class Library</span></span>](portable-class-library.md)
