---
title: Manipulando exceções de interoperabilidade COM
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 42efd1a5622bae7c476c92fb0864a6214c9bac9b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726178"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="ec5ee-102">Manipulando exceções de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="ec5ee-102">Handling COM Interop Exceptions</span></span>

<span data-ttu-id="ec5ee-103">Os códigos gerenciado e não gerenciado podem trabalhar juntos para tratar de exceções.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="ec5ee-104">Se um método lança uma exceção no código gerenciado, o common language runtime pode passar um HRESULT para um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="ec5ee-105">Se um método falhar no código não gerenciado, retornando um HRESULT de falha, o runtime lançará uma exceção que pode ser detectada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="ec5ee-106">O runtime mapeia automaticamente o HRESULT da interoperabilidade COM para exceções mais específicas.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="ec5ee-107">Por exemplo, E_ACCESSDENIED se torna <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se torna <xref:System.OutOfMemoryException> e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="ec5ee-108">Se o HRESULT for um resultado personalizado, ou se for desconhecido para o runtime, o runtime passará um <xref:System.Runtime.InteropServices.COMException> genérico ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="ec5ee-109">A propriedade **ErrorCode** do **COMException** contém o valor de HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="ec5ee-110">Trabalhar com IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="ec5ee-110">Working with IErrorInfo</span></span>  

 <span data-ttu-id="ec5ee-111">Quando um erro é passado do COM para o código gerenciado, o runtime preenche o objeto de exceção com informações do erro.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="ec5ee-112">Objetos COM que dão suporte a IErrorInfo e retornam HRESULTS fornecem essas informações para exceções de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="ec5ee-113">Por exemplo, o runtime mapeia a Descrição do erro COM para a propriedade <xref:System.Exception.Message%2A> da exceção.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="ec5ee-114">Se o HRESULT não fornecer mais informações sobre o erro, o runtime preencherá muitas das propriedades da exceção com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="ec5ee-115">Se um método falhar no código não gerenciado, uma exceção poderá ser passada para um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="ec5ee-116">O tópico [HRESULTS e exceções](../../framework/interop/how-to-map-hresults-and-exceptions.md) contém uma tabela que mostra como HRESULTS mapeia para objetos de exceção de runtime.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-116">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ec5ee-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec5ee-117">See also</span></span>

- [<span data-ttu-id="ec5ee-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="ec5ee-118">Exceptions</span></span>](index.md)
