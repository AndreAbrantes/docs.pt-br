---
title: "Funções espaciais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: acc09f9ea83e42377d0ba633927ecef13d5f46a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="spatial-functions"></a><span data-ttu-id="169f2-102">Funções espaciais</span><span class="sxs-lookup"><span data-stu-id="169f2-102">Spatial Functions</span></span>
<span data-ttu-id="169f2-103">Não há nenhum formato literal para tipos espaciais.</span><span class="sxs-lookup"><span data-stu-id="169f2-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="169f2-104">Entretanto, você pode usar funções canônicas do Entity Framework que você chama usando cadeias de caracteres no formato de texto bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="169f2-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="169f2-105">Por exemplo, a chamada de função a seguir cria um ponto geométrico:</span><span class="sxs-lookup"><span data-stu-id="169f2-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="169f2-106">O [SpatialEdmFunctions métodos](http://msdn.microsoft.com/library/hh749531.aspx) página lista todos os métodos Entity Framework canônicos espaciais.</span><span class="sxs-lookup"><span data-stu-id="169f2-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="169f2-107">Clique em um método de interesse ver quais parâmetros devem ser passados para uma função.</span><span class="sxs-lookup"><span data-stu-id="169f2-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
