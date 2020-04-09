---
title: Validação do lado do cliente (validação nas camadas de apresentação)
description: Arquitetura de Microsserviços .NET para aplicativos .NET em contêineres | Explore os principais conceitos da validação do lado do cliente.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988695"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="ab94e-103">Validação do lado do cliente (validação nas camadas de apresentação)</span><span class="sxs-lookup"><span data-stu-id="ab94e-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="ab94e-104">Mesmo quando a fonte de verdade for o modelo de domínio e, em último caso, você precisar ter validação no nível de modelo de domínio, a validação ainda poderá ser manipulada tanto no nível de modelo de domínio (lado do servidor) quanto da interface do usuário (lado do cliente).</span><span class="sxs-lookup"><span data-stu-id="ab94e-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="ab94e-105">A validação do lado do cliente é uma ótima conveniência para usuários.</span><span class="sxs-lookup"><span data-stu-id="ab94e-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="ab94e-106">Ela economiza tempo que de outra forma seria gasto aguardando uma viagem de ida e volta que talvez retorne erros de validação.</span><span class="sxs-lookup"><span data-stu-id="ab94e-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="ab94e-107">Em termos de negócios, até mesmo algumas frações de segundos multiplicadas por centenas de vezes por dia chega a ser muito tempo, despesa e frustração.</span><span class="sxs-lookup"><span data-stu-id="ab94e-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="ab94e-108">A validação imediata e simples permite que os usuários trabalhem com mais eficiência e façam contribuições e produzam entradas e saídas de melhor qualidade.</span><span class="sxs-lookup"><span data-stu-id="ab94e-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="ab94e-109">Como o modelo de exibição e o modelo de domínio são diferentes, a validação do modelo de exibição e do modelo de domínio podem ser semelhantes, mas têm um propósito diferente.</span><span class="sxs-lookup"><span data-stu-id="ab94e-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="ab94e-110">Se você está preocupado com DRY (o princípio Não Repita a si mesmo), considere que neste caso a reutilização do código também pode significar acoplamento, e em aplicativos corporativos é mais importante não acoplar o lado do servidor ao lado do cliente do que seguir o princípio DRY.</span><span class="sxs-lookup"><span data-stu-id="ab94e-110">If you are concerned about DRY (the Don't Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="ab94e-111">Mesmo ao usar a validação do lado do cliente, você sempre deve validar seus comandos ou DTOs de entrada no código do servidor, porque as APIs do servidor são um possível vetor de ataque.</span><span class="sxs-lookup"><span data-stu-id="ab94e-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="ab94e-112">Geralmente, fazer as duas é a melhor opção, porque se você tiver um aplicativo cliente, de uma perspectiva do UX, será melhor ser proativo e não permitir que o usuário insira informações inválidas.</span><span class="sxs-lookup"><span data-stu-id="ab94e-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="ab94e-113">Portanto, no código do lado do cliente você normalmente valida os ViewModels.</span><span class="sxs-lookup"><span data-stu-id="ab94e-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="ab94e-114">Você também pode validar os DTOs ou comandos de saída do cliente antes de enviá-los aos serviços.</span><span class="sxs-lookup"><span data-stu-id="ab94e-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="ab94e-115">A implementação de validação do lado do cliente depende de qual tipo de aplicativo cliente você está criando.</span><span class="sxs-lookup"><span data-stu-id="ab94e-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="ab94e-116">Será diferente se você estiver validando dados em um aplicativo Web MVC da Web com a maior parte do código em .NET, um aplicativo Web SPA com a validação sendo codificada em JavaScript ou TypeScript ou um aplicativo móvel codificado com Xamarin e C#.</span><span class="sxs-lookup"><span data-stu-id="ab94e-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ab94e-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ab94e-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="ab94e-118">Validação de aplicativos móveis Xamarin</span><span class="sxs-lookup"><span data-stu-id="ab94e-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="ab94e-119">**Validar a entrada de texto e mostrar erros** </span><span class="sxs-lookup"><span data-stu-id="ab94e-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="ab94e-120">**Chamada de validação** </span><span class="sxs-lookup"><span data-stu-id="ab94e-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="ab94e-121">Validação em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab94e-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="ab94e-122">**Rick Anderson. Adicionando validação** </span><span class="sxs-lookup"><span data-stu-id="ab94e-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="ab94e-123">Validação em aplicativos Web SPA (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="ab94e-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="ab94e-124">**Ado Kukic. Validação de formulário angular 2** </span><span class="sxs-lookup"><span data-stu-id="ab94e-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="ab94e-125">**Validação de formulários** </span><span class="sxs-lookup"><span data-stu-id="ab94e-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="ab94e-126">**Validação.**</span><span class="sxs-lookup"><span data-stu-id="ab94e-126">**Validation.**</span></span> <span data-ttu-id="ab94e-127">Documentação da Breeze.</span><span class="sxs-lookup"><span data-stu-id="ab94e-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="ab94e-128">Em resumo, estes são os conceitos mais importantes no que diz respeito à validação:</span><span class="sxs-lookup"><span data-stu-id="ab94e-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="ab94e-129">Entidades e agregados devem impor sua própria consistência e ser "sempre válidos".</span><span class="sxs-lookup"><span data-stu-id="ab94e-129">Entities and aggregates should enforce their own consistency and be "always valid".</span></span> <span data-ttu-id="ab94e-130">Raízes agregadas são responsáveis pela consistência de várias entidades dentro da mesma agregação.</span><span class="sxs-lookup"><span data-stu-id="ab94e-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="ab94e-131">Se você acha que uma entidade precisa entrar em um estado inválido, considere usar um modelo de objeto diferente – por exemplo, usar um DTO temporário até criar a entidade de domínio definitiva.</span><span class="sxs-lookup"><span data-stu-id="ab94e-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="ab94e-132">Se precisar criar vários objetos relacionados, como uma agregação, e eles apenas forem válidos depois que todos tiverem sido criados, considere usar o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="ab94e-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="ab94e-133">Na maioria dos casos, ter validação redundante no lado do cliente é bom, porque o aplicativo pode ser proativo.</span><span class="sxs-lookup"><span data-stu-id="ab94e-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ab94e-134">[Próximo](domain-model-layer-validations.md)
>[anterior](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="ab94e-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
