---
title: 'Como: permitir que os usuários resolvam horários ambíguos'
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: d543db20161057764749210533f35f7c2a1ec81d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817790"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="5cec0-102">Como: permitir que os usuários resolvam horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="5cec0-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="5cec0-103">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="5cec0-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="5cec0-104">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="5cec0-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="5cec0-105">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="5cec0-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="5cec0-106">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="5cec0-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="5cec0-107">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="5cec0-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="5cec0-108">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="5cec0-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="5cec0-109">Este tópico mostra como permitir que um usuário resolva um horário ambíguo.</span><span class="sxs-lookup"><span data-stu-id="5cec0-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="5cec0-110">Permitir que o usuário resolva um horário ambíguo</span><span class="sxs-lookup"><span data-stu-id="5cec0-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="5cec0-111">Obtenha a entrada de data e hora do usuário.</span><span class="sxs-lookup"><span data-stu-id="5cec0-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="5cec0-112">Chame o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o tempo é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="5cec0-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="5cec0-113">Se o tempo for ambíguo, chame o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> objetos.</span><span class="sxs-lookup"><span data-stu-id="5cec0-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="5cec0-114">Cada elemento na matriz contém um deslocamento UTC para o qual a hora ambígua pode ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="5cec0-115">Permita que o usuário selecione o deslocamento desejado.</span><span class="sxs-lookup"><span data-stu-id="5cec0-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="5cec0-116">Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.</span><span class="sxs-lookup"><span data-stu-id="5cec0-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="5cec0-117">Chame o `static` `Shared` método (no Visual Basic .net) <xref:System.DateTime.SpecifyKind%2A> para definir a propriedade de valor de data e hora UTC <xref:System.DateTime.Kind%2A> como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5cec0-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="5cec0-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cec0-118">Example</span></span>

<span data-ttu-id="5cec0-119">O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta.</span><span class="sxs-lookup"><span data-stu-id="5cec0-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="5cec0-120">O núcleo do código de exemplo usa uma matriz de <xref:System.TimeSpan> objetos para indicar possíveis deslocamentos do tempo ambíguo do UTC.</span><span class="sxs-lookup"><span data-stu-id="5cec0-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="5cec0-121">No entanto, esses deslocamentos provavelmente não serão significativos para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5cec0-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="5cec0-122">Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão.</span><span class="sxs-lookup"><span data-stu-id="5cec0-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="5cec0-123">O código determina qual é a hora padrão e em qual horário é o horário de verão comparando o deslocamento com o valor da <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5cec0-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="5cec0-124">Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="5cec0-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="5cec0-125">Neste exemplo, todas as referências ao fuso horário local são feitas por meio da <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Propriedade; o fuso horário local nunca é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="5cec0-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="5cec0-126">Essa é uma prática recomendada porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos aos quais o fuso horário local está atribuído.</span><span class="sxs-lookup"><span data-stu-id="5cec0-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="5cec0-127">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5cec0-127">Compiling the code</span></span>

<span data-ttu-id="5cec0-128">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5cec0-128">This example requires:</span></span>

- <span data-ttu-id="5cec0-129">Que o <xref:System> namespace seja importado com a `using` instrução (necessária no código C#).</span><span class="sxs-lookup"><span data-stu-id="5cec0-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cec0-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="5cec0-130">See also</span></span>

- [<span data-ttu-id="5cec0-131">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="5cec0-131">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="5cec0-132">Como: resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="5cec0-132">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)
