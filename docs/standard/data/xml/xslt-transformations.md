---
title: Transformações XSLT
ms.date: 03/30/2017
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: b87768b402f92e0e59279aab0f0062e510fda2e6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818187"
---
# <a name="xslt-transformations"></a><span data-ttu-id="f235a-102">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="f235a-102">XSLT Transformations</span></span>
<span data-ttu-id="f235a-103">A linguagem XSL Transformation (XSLT) permite transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f235a-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="f235a-104">Por exemplo, você pode usar XSLT para transformar XML em HTML para usar em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f235a-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="f235a-105">Esse processo de transformação é especificado pela [Recomendação da linguagem XSL Transformations (XSLT) do W3C Versão 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="f235a-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="f235a-106">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT no .NET.</span><span class="sxs-lookup"><span data-stu-id="f235a-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="f235a-107">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é compatível com a [recomendação XSLT 1.0 do W3C](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="f235a-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f235a-108">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="f235a-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="f235a-109">A classe <xref:System.Xml.Xsl.XslCompiledTransform> é uma nova implementação do mecanismo do XSLT.</span><span class="sxs-lookup"><span data-stu-id="f235a-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="f235a-110">Ela inclui aprimoramentos de desempenho e novos recursos de segurança.</span><span class="sxs-lookup"><span data-stu-id="f235a-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="f235a-111">A prática recomendada é criar aplicativos do XSLT usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f235a-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f235a-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f235a-112">In This Section</span></span>  
 [<span data-ttu-id="f235a-113">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="f235a-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="f235a-114">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f235a-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="f235a-115">Migrar da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="f235a-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="f235a-116">Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="f235a-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="f235a-117">Compilador de XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="f235a-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="f235a-118">Fornece informações sobre como usar o compilador do XSLT.</span><span class="sxs-lookup"><span data-stu-id="f235a-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="f235a-119">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="f235a-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="f235a-120">Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="f235a-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f235a-121">Referência</span><span class="sxs-lookup"><span data-stu-id="f235a-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="f235a-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f235a-122">Related Sections</span></span>  
 [<span data-ttu-id="f235a-123">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="f235a-123">XML Documents and Data</span></span>](index.md)
