---
title: Introdução a Delegados
description: Saiba mais sobre delegados neste tópico de visão geral que apresenta os conceitos básicos e discute as metas de design da linguagem para delegados.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146223"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="b6f59-103">Introdução a Delegados</span><span class="sxs-lookup"><span data-stu-id="b6f59-103">Introduction to Delegates</span></span>

<span data-ttu-id="b6f59-104">Os delegados fornecem um mecanismo de *associação tardia* no .NET.</span><span class="sxs-lookup"><span data-stu-id="b6f59-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="b6f59-105">Associação tardia significa que você cria um algoritmo em que o chamador também fornece pelo menos um método que implementa a parte do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="b6f59-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="b6f59-106">Por exemplo, considere classificar uma lista de estrelas em um aplicativo de astronomia.</span><span class="sxs-lookup"><span data-stu-id="b6f59-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="b6f59-107">Você pode optar por classificar as estrelas por sua distância da terra ou a magnitude da estrela ou seu brilho percebido.</span><span class="sxs-lookup"><span data-stu-id="b6f59-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="b6f59-108">Em todos esses casos, o método Sort() faz essencialmente a mesma coisa: organiza os itens na lista com base em alguma comparação.</span><span class="sxs-lookup"><span data-stu-id="b6f59-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="b6f59-109">O código que compara duas estrelas é diferente para cada uma das ordenações de classificação.</span><span class="sxs-lookup"><span data-stu-id="b6f59-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="b6f59-110">Esses tipos de soluções foram usados no software por meio século.</span><span class="sxs-lookup"><span data-stu-id="b6f59-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="b6f59-111">O conceito de delegado de linguagem C# fornece suporte de linguagem de primeira classe e segurança de tipos em torno do conceito.</span><span class="sxs-lookup"><span data-stu-id="b6f59-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="b6f59-112">Como você verá posteriormente nesta série, o código C# que você escreve para algoritmos como esse é seguro quanto ao tipo e aproveita a linguagem e o compilador para garantir que os tipos correspondem aos argumentos e tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="b6f59-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="b6f59-113">Metas de design da linguagem para delegados</span><span class="sxs-lookup"><span data-stu-id="b6f59-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="b6f59-114">Os designers de linguagem enumeraram várias metas para o recurso que eventualmente se tornaram delegados.</span><span class="sxs-lookup"><span data-stu-id="b6f59-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="b6f59-115">A equipe queria um constructo de linguagem comum que pudesse ser usada qualquer algoritmo de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="b6f59-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="b6f59-116">Isso permite aos desenvolvedores aprender um conceito e usar esse conceito entre muitos problemas de software diferentes.</span><span class="sxs-lookup"><span data-stu-id="b6f59-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="b6f59-117">Em segundo lugar, a equipe queria dar suporte a chamadas de método single ou multicast.</span><span class="sxs-lookup"><span data-stu-id="b6f59-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="b6f59-118">(Delegados multicast são delegados que encadeiam várias chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="b6f59-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="b6f59-119">Você verá exemplos [posteriormente nesta série](delegate-class.md).)</span><span class="sxs-lookup"><span data-stu-id="b6f59-119">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="b6f59-120">A equipe queria delegados para dar suporte à mesma segurança de tipos que os desenvolvedores esperam de todos os constructos de C#.</span><span class="sxs-lookup"><span data-stu-id="b6f59-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="b6f59-121">Por fim, a equipe reconheceu que um padrão de eventos é um padrão específico em que delegados ou qualquer algoritmo de associação tardia é muito útil.</span><span class="sxs-lookup"><span data-stu-id="b6f59-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="b6f59-122">A equipe quis garantir que o código para delegados pudesse fornecer a base para o padrão de evento .NET.</span><span class="sxs-lookup"><span data-stu-id="b6f59-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="b6f59-123">O resultado de todo esse trabalho era o suporte do delegado e do evento no C# e .NET.</span><span class="sxs-lookup"><span data-stu-id="b6f59-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="b6f59-124">Os demais artigos nessa seção abordarão os recursos da linguagem, o suporte da biblioteca e as expressões comuns que são usadas ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="b6f59-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="b6f59-125">Você aprenderá sobre a palavra-chave `delegate` e qual código ela gera.</span><span class="sxs-lookup"><span data-stu-id="b6f59-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="b6f59-126">Você aprenderá sobre os recursos na classe `System.Delegate` e como esses recursos são usados.</span><span class="sxs-lookup"><span data-stu-id="b6f59-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="b6f59-127">Você aprenderá como criar delegados de segurança de tipos e como criar métodos que podem ser invocados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="b6f59-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="b6f59-128">Você também aprenderá a trabalhar com eventos e delegados usando expressões Lambda.</span><span class="sxs-lookup"><span data-stu-id="b6f59-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="b6f59-129">Você verá onde delegados se tornam um dos blocos de construção para LINQ.</span><span class="sxs-lookup"><span data-stu-id="b6f59-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="b6f59-130">Você aprenderá como os delegados são a base para o padrão de evento do .NET e como eles são diferentes.</span><span class="sxs-lookup"><span data-stu-id="b6f59-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="b6f59-131">Em geral, você verá como os delegados são parte integrante de programação em .NET e no trabalho com as APIs de estrutura.</span><span class="sxs-lookup"><span data-stu-id="b6f59-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="b6f59-132">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="b6f59-132">Let's get started.</span></span>

[<span data-ttu-id="b6f59-133">Avançar</span><span class="sxs-lookup"><span data-stu-id="b6f59-133">Next</span></span>](delegate-class.md)
