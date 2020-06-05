---
title: Objeto My.Response
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372448"
---
# <a name="myresponse-object"></a><span data-ttu-id="01a65-102">Objeto My.Response</span><span class="sxs-lookup"><span data-stu-id="01a65-102">My.Response Object</span></span>
<span data-ttu-id="01a65-103">Obtém o <xref:System.Web.HttpResponse> objeto associado ao <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="01a65-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="01a65-104">Esse objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.</span><span class="sxs-lookup"><span data-stu-id="01a65-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01a65-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="01a65-105">Remarks</span></span>  
 <span data-ttu-id="01a65-106">O `My.Response` objeto contém o <xref:System.Web.HttpResponse> objeto atual associado à página.</span><span class="sxs-lookup"><span data-stu-id="01a65-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="01a65-107">O `My.Response` objeto só está disponível para aplicativos ASP.net.</span><span class="sxs-lookup"><span data-stu-id="01a65-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01a65-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01a65-108">Example</span></span>  
 <span data-ttu-id="01a65-109">O exemplo a seguir obtém a coleção de cabeçalho do `My.Request` objeto e usa o `My.Response` objeto para escrevê-lo na página ASP.net.</span><span class="sxs-lookup"><span data-stu-id="01a65-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01a65-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="01a65-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="01a65-111">Objeto My.Request</span><span class="sxs-lookup"><span data-stu-id="01a65-111">My.Request Object</span></span>](my-request-object.md)
