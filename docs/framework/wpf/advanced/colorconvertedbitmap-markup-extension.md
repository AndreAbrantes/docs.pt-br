---
title: Extensão de marcação ColorConvertedBitmap
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141223"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="0aac2-102">Extensão de marcação ColorConvertedBitmap</span><span class="sxs-lookup"><span data-stu-id="0aac2-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="0aac2-103">Fornece uma maneira de especificar uma origem de bitmap que não tem um perfil inserido.</span><span class="sxs-lookup"><span data-stu-id="0aac2-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="0aac2-104">Os perfis/contextos de cor são especificados por URI, assim como o URI de origem da imagem.</span><span class="sxs-lookup"><span data-stu-id="0aac2-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0aac2-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="0aac2-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0aac2-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="0aac2-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="0aac2-107">O URI do bitmap não perfilado.</span><span class="sxs-lookup"><span data-stu-id="0aac2-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="0aac2-108">O URI da configuração do perfil de origem.</span><span class="sxs-lookup"><span data-stu-id="0aac2-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="0aac2-109">O URI da configuração do perfil de destino</span><span class="sxs-lookup"><span data-stu-id="0aac2-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aac2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0aac2-110">Remarks</span></span>  
 <span data-ttu-id="0aac2-111">Essa extensão de marcação destina-se a preencher um conjunto relacionado de valores de propriedade de origem <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>de imagem, como.</span><span class="sxs-lookup"><span data-stu-id="0aac2-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="0aac2-112">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="0aac2-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="0aac2-113">`ColorConvertedBitmap`(ou `ColorConvertedBitmapExtension`) não pode ser usado na sintaxe do elemento de propriedade, pois os valores só podem ser definidos como valores no construtor inicial, que é a cadeia de caracteres após o identificador de extensão.</span><span class="sxs-lookup"><span data-stu-id="0aac2-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="0aac2-114">`ColorConvertedBitmap` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="0aac2-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="0aac2-115">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="0aac2-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="0aac2-116">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="0aac2-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="0aac2-117">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="0aac2-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aac2-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="0aac2-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="0aac2-119">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="0aac2-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="0aac2-120">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="0aac2-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
