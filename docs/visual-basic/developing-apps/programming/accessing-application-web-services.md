---
title: Como acessar serviços Web de aplicativo
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: cf9a0c9840b9228b59af9959cf3a4efb9a1d1ea0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410186"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="1a527-102">Acessando serviços Web do aplicativo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a527-102">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="1a527-103">O objeto `My.WebServices` fornece uma instância de cada serviço Web referenciado pelo projeto atual.</span><span class="sxs-lookup"><span data-stu-id="1a527-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="1a527-104">Cada instância é instanciada sob demanda.</span><span class="sxs-lookup"><span data-stu-id="1a527-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="1a527-105">É possível acessar esses serviços Web por meio das propriedades do objeto `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="1a527-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="1a527-106">O nome da propriedade é igual ao nome do serviço Web acessado pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="1a527-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="1a527-107">Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="1a527-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="1a527-108">Tarefas</span><span class="sxs-lookup"><span data-stu-id="1a527-108">Tasks</span></span>

<span data-ttu-id="1a527-109">A tabela a seguir lista as possíveis maneiras de acessar serviços Web referenciados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a527-109">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="1a527-110">Para</span><span class="sxs-lookup"><span data-stu-id="1a527-110">To</span></span>|<span data-ttu-id="1a527-111">Consulte</span><span class="sxs-lookup"><span data-stu-id="1a527-111">See</span></span>|
|---|---|
|<span data-ttu-id="1a527-112">Chamar um serviço Web</span><span class="sxs-lookup"><span data-stu-id="1a527-112">Call a Web service</span></span>|[<span data-ttu-id="1a527-113">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="1a527-113">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="1a527-114">Chamar um serviço Web de forma assíncrona e manipular um evento quando ele for concluído</span><span class="sxs-lookup"><span data-stu-id="1a527-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="1a527-115">Como: Chamar um serviço Web de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="1a527-115">How to: Call a Web Service Asynchronously</span></span>](how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="1a527-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a527-116">See also</span></span>

- [<span data-ttu-id="1a527-117">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="1a527-117">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
