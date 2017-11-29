---
title: Como codificar e decodificar uma imagem TIFF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c839f449a0b19f2aa3bbe26a393bdfd2226fa9f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="e1ba0-102">Como codificar e decodificar uma imagem TIFF</span><span class="sxs-lookup"><span data-stu-id="e1ba0-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="e1ba0-103">Os exemplos a seguir mostram como decodificar e codificar um [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] imagem usando específico <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> e <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objetos.</span><span class="sxs-lookup"><span data-stu-id="e1ba0-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1ba0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ba0-104">Example</span></span>  
 <span data-ttu-id="e1ba0-105">Este exemplo demonstra como decodificar uma [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] imagem usando uma <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> de um <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="e1ba0-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e1ba0-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ba0-106">Example</span></span>  
 <span data-ttu-id="e1ba0-107">Este exemplo demonstra como codificar um <xref:System.Windows.Media.Imaging.BitmapSource> em uma [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] imagem usando um <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="e1ba0-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e1ba0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1ba0-108">See Also</span></span>  
 [<span data-ttu-id="e1ba0-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="e1ba0-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
