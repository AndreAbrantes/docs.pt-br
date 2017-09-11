---
title: "Arquivo XML de exemplo: Teste de configuração (LINQ to XML) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2e0e19f2-83e4-42ad-958a-6b3e34c9bf17
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 192f6ca5796bb21c96b0d2f968793706749c7236
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sample-xml-file-test-configuration-linq-to-xml"></a><span data-ttu-id="f38a5-102">Arquivo XML de Exemplo: Configuração de teste (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f38a5-102">Sample XML File: Test Configuration (LINQ to XML)</span></span>
<span data-ttu-id="f38a5-103">O arquivo XML a seguir é usado em vários exemplos na documentação do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="f38a5-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] documentation.</span></span> <span data-ttu-id="f38a5-104">Este é um arquivo de configuração de teste.</span><span class="sxs-lookup"><span data-stu-id="f38a5-104">This is a test configuration file.</span></span>  
  
## <a name="testconfigxml"></a><span data-ttu-id="f38a5-105">TestConfig.xml</span><span class="sxs-lookup"><span data-stu-id="f38a5-105">TestConfig.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests>  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f38a5-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f38a5-106">See Also</span></span>  
 [<span data-ttu-id="f38a5-107">Documentos XML de exemplo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f38a5-107">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
