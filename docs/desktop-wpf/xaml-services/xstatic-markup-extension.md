---
title: Extensão de marcação x:Static
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551605"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="96478-102">Extensão de marcação x:Static</span><span class="sxs-lookup"><span data-stu-id="96478-102">x:Static Markup Extension</span></span>

<span data-ttu-id="96478-103">Faz referência a qualquer entidade de código de valor estático definida em uma maneira compatível com Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="96478-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="96478-104">A propriedade estática que é referenciada pode ser usada para fornecer o valor de uma propriedade em XAML.</span><span class="sxs-lookup"><span data-stu-id="96478-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="96478-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="96478-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="96478-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="96478-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="96478-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="96478-107">Optional.</span></span> <span data-ttu-id="96478-108">Um prefixo que se refere a um namespace XAML mapeado e não padrão.</span><span class="sxs-lookup"><span data-stu-id="96478-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="96478-109">`prefix` é mostrado explicitamente no uso porque você raramente referencia propriedades estáticas que vêm de um namespace XAML padrão.</span><span class="sxs-lookup"><span data-stu-id="96478-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="96478-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="96478-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="96478-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="96478-111">Required.</span></span> <span data-ttu-id="96478-112">O nome do tipo que define o membro estático desejado.</span><span class="sxs-lookup"><span data-stu-id="96478-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="96478-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="96478-113">Required.</span></span> <span data-ttu-id="96478-114">O nome do membro de valor estático desejado (uma constante, uma propriedade estática, um campo ou um valor de enumeração).</span><span class="sxs-lookup"><span data-stu-id="96478-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="96478-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="96478-115">Remarks</span></span>

<span data-ttu-id="96478-116">A entidade de código que é referenciada deve ser uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="96478-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="96478-117">Uma constante</span><span class="sxs-lookup"><span data-stu-id="96478-117">A constant</span></span>
- <span data-ttu-id="96478-118">Uma propriedade estática</span><span class="sxs-lookup"><span data-stu-id="96478-118">A static property</span></span>
- <span data-ttu-id="96478-119">Um campo</span><span class="sxs-lookup"><span data-stu-id="96478-119">A field</span></span>
- <span data-ttu-id="96478-120">Um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="96478-120">An enumeration value</span></span>

<span data-ttu-id="96478-121">Especificar qualquer outra entidade de código, como uma propriedade não estática, causará um erro em tempo de compilação se o XAML for uma marcação compilada ou uma exceção de análise de tempo de carga XAML.</span><span class="sxs-lookup"><span data-stu-id="96478-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="96478-122">Você pode fazer `x:Static` referências a campos estáticos ou propriedades que não estão no namespace XAML padrão para o documento XAML atual; no entanto, isso requer um mapeamento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="96478-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="96478-123">Os namespaces XAML quase sempre são definidos no elemento raiz do documento XAML.</span><span class="sxs-lookup"><span data-stu-id="96478-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="96478-124">As operações de pesquisa para propriedades estáticas podem ser executadas pelos serviços XAML .NET e seus leitores XAML e gravadores XAML, quando estão em execução com o contexto de esquema XAML padrão.</span><span class="sxs-lookup"><span data-stu-id="96478-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="96478-125">Este contexto de esquema XAML pode usar a reflexão do CLR para fornecer os valores estáticos necessários para a construção do grafo de objeto.</span><span class="sxs-lookup"><span data-stu-id="96478-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="96478-126">O `typeName` que você especifica é, na verdade, um nome de tipo XAML, não um nome de tipo CLR, embora eles sejam essencialmente o mesmo nome ao usar o contexto de esquema XAML padrão ou ao usar todas as estruturas de implementação XAML existentes baseadas em CLR.</span><span class="sxs-lookup"><span data-stu-id="96478-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="96478-127">Tenha cuidado ao fazer `x:Static` referências que não são diretamente o tipo de valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="96478-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="96478-128">Na sequência de processamento XAML, os valores fornecidos de uma extensão de marcação não invocam a conversão de valor adicional.</span><span class="sxs-lookup"><span data-stu-id="96478-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="96478-129">Isso é verdadeiro mesmo que a `x:Static` referência crie uma cadeia de texto, e uma conversão de valor para valores de atributo com base na cadeia de texto normalmente ocorra para esse membro específico ou para qualquer valor de membro do tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="96478-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="96478-130">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="96478-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="96478-131">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Static` é atribuído como o valor <xref:System.Windows.Markup.StaticExtension.Member%2A> da classe de extensão subjacente <xref:System.Windows.Markup.StaticExtension>.</span><span class="sxs-lookup"><span data-stu-id="96478-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="96478-132">Há dois outros usos de XAML que são tecnicamente possíveis.</span><span class="sxs-lookup"><span data-stu-id="96478-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="96478-133">No entanto, esses usos são menos comuns porque são desnecessariamente detalhados:</span><span class="sxs-lookup"><span data-stu-id="96478-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="96478-134">Sintaxe do elemento Object.</span><span class="sxs-lookup"><span data-stu-id="96478-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="96478-135">Sintaxe de atributo com propriedade de membro explícita para cadeia de inicialização.</span><span class="sxs-lookup"><span data-stu-id="96478-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="96478-136">Na implementação de serviços XAML .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.StaticExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="96478-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="96478-137">`x:Static` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="96478-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="96478-138">Todas as extensões de marcação em XAML usam os `{` `}` caracteres e em sua sintaxe de atributo, que é a Convenção pela qual um processador XAML reconhece que uma extensão de marcação deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="96478-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="96478-139">Para obter mais informações sobre extensões de marcação, consulte [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96478-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="96478-140">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="96478-140">WPF Usage Notes</span></span>

<span data-ttu-id="96478-141">O namespace XAML padrão que você usa para a programação do WPF não contém muitas propriedades estáticas úteis, e a maioria das propriedades estáticas úteis têm suporte como conversores de tipo que facilitam o uso sem a necessidade de `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="96478-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="96478-142">Para propriedades estáticas, você deve mapear um prefixo para um namespace XAML se uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="96478-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="96478-143">Você está fazendo referência a um tipo que existe no WPF, mas que não faz parte do namespace XAML padrão para WPF ( `http://schemas.microsoft.com/winfx/2006/xaml/presentation` ).</span><span class="sxs-lookup"><span data-stu-id="96478-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="96478-144">Esse é um cenário bastante comum para usar o `x:Static` .</span><span class="sxs-lookup"><span data-stu-id="96478-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="96478-145">Por exemplo, você pode usar uma `x:Static` referência com um mapeamento de namespace XAML para o <xref:System> namespace CLR e o assembly mscorlib a fim de fazer referência às propriedades estáticas da <xref:System.Environment> classe.</span><span class="sxs-lookup"><span data-stu-id="96478-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="96478-146">Você está fazendo referência a um tipo de um assembly personalizado.</span><span class="sxs-lookup"><span data-stu-id="96478-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="96478-147">Você está fazendo referência a um tipo que existe em um assembly do WPF, mas esse tipo está dentro de um namespace CLR que não foi mapeado para fazer parte do namespace XAML padrão do WPF.</span><span class="sxs-lookup"><span data-stu-id="96478-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="96478-148">O mapeamento de namespaces CLR para o namespace XAML padrão do WPF é executado por definições nos vários assemblies do WPF (para obter mais informações sobre esse conceito, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span><span class="sxs-lookup"><span data-stu-id="96478-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span></span> <span data-ttu-id="96478-149">Os namespaces CLR não mapeados podem existir se o namespace CLR é composto principalmente de definições de classe que normalmente não são pretendidas para XAML, como <xref:System.Windows.Threading> .</span><span class="sxs-lookup"><span data-stu-id="96478-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="96478-150">Para obter mais informações sobre como usar prefixos e namespaces XAML para WPF, consulte [namespaces XAML e mapeamento de namespace para WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="96478-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

## <a name="see-also"></a><span data-ttu-id="96478-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="96478-151">See also</span></span>

- [<span data-ttu-id="96478-152">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="96478-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="96478-153">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="96478-153">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
