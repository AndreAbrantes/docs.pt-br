---
title: Script de folha de estilos XSLT usando <msxsl:script>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 206a659656f1019af1540b9b2476ae7fe9ba93eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685104"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="4079d-102">Script de folha de estilos XSLT usando \<msxsl:script></span><span class="sxs-lookup"><span data-stu-id="4079d-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>

<span data-ttu-id="4079d-103">A classe <xref:System.Xml.Xsl.XslTransform> dá suporte a scripts inserido usando o elemento `script`.</span><span class="sxs-lookup"><span data-stu-id="4079d-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4079d-104">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="4079d-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="4079d-105">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4079d-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4079d-106">Confira [Usar a classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4079d-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="4079d-107">A classe <xref:System.Xml.Xsl.XslTransform> dá suporte a scripts inserido usando o elemento `script`.</span><span class="sxs-lookup"><span data-stu-id="4079d-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="4079d-108">Quando a folha de estilos é carregada, todas as funções definidas são compiladas no Microsoft Intermediate Language (MSIL) sendo empacotadas em uma definição de classe e sem perda de desempenho como resultado.</span><span class="sxs-lookup"><span data-stu-id="4079d-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="4079d-109">O elemento `<msxsl:script>` é definido abaixo:</span><span class="sxs-lookup"><span data-stu-id="4079d-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="4079d-110">onde `msxsl` é um prefixo associado ao namespace `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="4079d-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="4079d-111">O `language` atributo não é obrigatório, mas, se especificado, seu valor deve ser um dos seguintes: `C#` , `VB` , `JScript` , `JavaScript` , `VisualBasic` ou `CSharp` .</span><span class="sxs-lookup"><span data-stu-id="4079d-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="4079d-112">Se não for especificado, a linguagem padrão é JScript.</span><span class="sxs-lookup"><span data-stu-id="4079d-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="4079d-113">O `language-name` não diferencia maiúsculas de minúsculas, portanto “JavaScript” e “Javascript” são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="4079d-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="4079d-114">O atributo `implements-prefix` é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4079d-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="4079d-115">Esse atributo é usado para declarar um namespace e associá-lo ao bloco de script.</span><span class="sxs-lookup"><span data-stu-id="4079d-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="4079d-116">O valor desse atributo é o prefixo que representa o namespace.</span><span class="sxs-lookup"><span data-stu-id="4079d-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="4079d-117">Este namespace pode ser definido em qualquer lugar em uma folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="4079d-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="4079d-118">Como o elemento `msxsl:script` pertence ao namespace `urn:schemas-microsoft-com:xslt`, a folha de estilos deverá incluir a declaração de namespace `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="4079d-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="4079d-119">Se o chamador do script não tem permissão de acesso <xref:System.Security.Permissions.SecurityPermissionFlag>, o script em uma folha de estilos nunca compilará e a chamada a <xref:System.Xml.Xsl.XslTransform.Load%2A> falhará.</span><span class="sxs-lookup"><span data-stu-id="4079d-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="4079d-120">Se o chamador tiver a permissão de `UnmanagedCode`, o script será compilado, mas as operações que são permitidas são dependentes da evidência que é fornecida em tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="4079d-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="4079d-121">Se você estiver usando um dos métodos <xref:System.Xml.Xsl.XslTransform.Load%2A> que recebem <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> para carregar a folha de estilos, você precisará usar a sobrecarga <xref:System.Xml.Xsl.XslTransform.Load%2A> que utiliza um parâmetro <xref:System.Security.Policy.Evidence> como um dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="4079d-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="4079d-122">Para fornecer a evidência, o chamador deverá ter a permissão <xref:System.Security.Permissions.SecurityPermissionFlag> para fornecer `Evidence` ao assembly de script.</span><span class="sxs-lookup"><span data-stu-id="4079d-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="4079d-123">Se o chamador não tiver essa permissão, eles poderão definir o parâmetro `Evidence` como `null`.</span><span class="sxs-lookup"><span data-stu-id="4079d-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="4079d-124">Isso faz a função <xref:System.Xml.Xsl.XslTransform.Load%2A> falhar se encontrar o script.</span><span class="sxs-lookup"><span data-stu-id="4079d-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="4079d-125">A permissão `ControlEvidence` é considerada uma permissão muito eficiente que deve ser concedida apenas a código altamente confiável.</span><span class="sxs-lookup"><span data-stu-id="4079d-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="4079d-126">Para obter a evidência do assembly, use `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="4079d-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="4079d-127">Para obter a evidência de um Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="4079d-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="4079d-128">Se você usar os métodos <xref:System.Xml.Xsl.XslTransform.Load%2A> que utilizam um <xref:System.Xml.XmlResolver> mas nenhum `Evidence`, a zona de segurança para o assembly usará como padrão a confiança total.</span><span class="sxs-lookup"><span data-stu-id="4079d-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="4079d-129">Para saber mais, veja <xref:System.Security.SecurityZone> e [Conjuntos de permissões nomeadas](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4079d-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4079d-130">As funções podem ser declaradas no elemento `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="4079d-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="4079d-131">A tabela a seguir mostra os namespaces que têm suporte por padrão.</span><span class="sxs-lookup"><span data-stu-id="4079d-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="4079d-132">Você pode usar as classes fora dos namespaces listados.</span><span class="sxs-lookup"><span data-stu-id="4079d-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="4079d-133">No entanto, essas classes devem ser totalmente qualificadas.</span><span class="sxs-lookup"><span data-stu-id="4079d-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="4079d-134">Namespaces padrão</span><span class="sxs-lookup"><span data-stu-id="4079d-134">Default Namespaces</span></span>|<span data-ttu-id="4079d-135">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="4079d-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="4079d-136">Sistema</span><span class="sxs-lookup"><span data-stu-id="4079d-136">System</span></span>|<span data-ttu-id="4079d-137">Classe do sistema.</span><span class="sxs-lookup"><span data-stu-id="4079d-137">System class.</span></span>|  
|<span data-ttu-id="4079d-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="4079d-138">System.Collection</span></span>|<span data-ttu-id="4079d-139">Classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="4079d-139">Collection classes.</span></span>|  
|<span data-ttu-id="4079d-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="4079d-140">System.Text</span></span>|<span data-ttu-id="4079d-141">Classes de texto.</span><span class="sxs-lookup"><span data-stu-id="4079d-141">Text classes.</span></span>|  
|<span data-ttu-id="4079d-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="4079d-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="4079d-143">Classes de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="4079d-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="4079d-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="4079d-144">System.Xml</span></span>|<span data-ttu-id="4079d-145">Classes XML principais.</span><span class="sxs-lookup"><span data-stu-id="4079d-145">Core XML classes.</span></span>|  
|<span data-ttu-id="4079d-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="4079d-146">System.Xml.Xsl</span></span>|<span data-ttu-id="4079d-147">Classes XSLT.</span><span class="sxs-lookup"><span data-stu-id="4079d-147">XSLT classes.</span></span>|  
|<span data-ttu-id="4079d-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="4079d-148">System.Xml.XPath</span></span>|<span data-ttu-id="4079d-149">Classes da linguagem XPath.</span><span class="sxs-lookup"><span data-stu-id="4079d-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="4079d-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="4079d-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="4079d-151">Classes para scripts do Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4079d-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="4079d-152">Quando uma função é declarada, ela está contida em um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="4079d-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="4079d-153">As folhas de estilos podem conter vários blocos de script, cada uma funcionando de maneira independente da outra.</span><span class="sxs-lookup"><span data-stu-id="4079d-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="4079d-154">Isso significa que, se você estiver realizando a execução em um bloco de script, não poderá chamar uma função definida em outro bloco de script, a menos que tenha sido declarado que ela tem o mesmo namespace e a mesma linguagem de script.</span><span class="sxs-lookup"><span data-stu-id="4079d-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="4079d-155">Como cada bloco de script pode estar em sua própria linguagem, e o bloco é analisado de acordo com as regras de gramática do analisador de linguagem, você deverá usar a sintaxe correta para a linguagem em uso.</span><span class="sxs-lookup"><span data-stu-id="4079d-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="4079d-156">Por exemplo, se você estiver em um bloco de script C#, é um erro usar um nó de comentário XML `<!-- an XML comment -->` no bloco.</span><span class="sxs-lookup"><span data-stu-id="4079d-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="4079d-157">Os argumentos fornecidos e os valores de retorno definidos pelas funções de script devem ser do tipo XPath do W3C (World Wide Web Consortium) ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="4079d-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="4079d-158">A tabela a seguir mostra os tipos correspondentes de W3C, as classes equivalentes do .NET Framework (tipo) e se o tipo do W3C é XPath ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="4079d-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="4079d-159">Type</span><span class="sxs-lookup"><span data-stu-id="4079d-159">Type</span></span>|<span data-ttu-id="4079d-160">Classe equivalente do .NET Framework (tipo)</span><span class="sxs-lookup"><span data-stu-id="4079d-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="4079d-161">Tipo XPath ou XSLT</span><span class="sxs-lookup"><span data-stu-id="4079d-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="4079d-162">String</span><span class="sxs-lookup"><span data-stu-id="4079d-162">String</span></span>|<span data-ttu-id="4079d-163">System.String</span><span class="sxs-lookup"><span data-stu-id="4079d-163">System.String</span></span>|<span data-ttu-id="4079d-164">XPath</span><span class="sxs-lookup"><span data-stu-id="4079d-164">XPath</span></span>|  
|<span data-ttu-id="4079d-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="4079d-165">Boolean</span></span>|<span data-ttu-id="4079d-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="4079d-166">System.Boolean</span></span>|<span data-ttu-id="4079d-167">XPath</span><span class="sxs-lookup"><span data-stu-id="4079d-167">XPath</span></span>|  
|<span data-ttu-id="4079d-168">Número</span><span class="sxs-lookup"><span data-stu-id="4079d-168">Number</span></span>|<span data-ttu-id="4079d-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="4079d-169">System.Double</span></span>|<span data-ttu-id="4079d-170">XPath</span><span class="sxs-lookup"><span data-stu-id="4079d-170">XPath</span></span>|  
|<span data-ttu-id="4079d-171">Fragmento da árvore de resultado</span><span class="sxs-lookup"><span data-stu-id="4079d-171">Result Tree Fragment</span></span>|<span data-ttu-id="4079d-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4079d-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="4079d-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="4079d-173">XSLT</span></span>|  
|<span data-ttu-id="4079d-174">Node Set</span><span class="sxs-lookup"><span data-stu-id="4079d-174">Node Set</span></span>|<span data-ttu-id="4079d-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="4079d-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="4079d-176">XPath</span><span class="sxs-lookup"><span data-stu-id="4079d-176">XPath</span></span>|  
  
 <span data-ttu-id="4079d-177">Se a função de script utilizar um dos seguintes tipos numéricos: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single ou Decimal, eles serão forçados para Double, que mapeia para o número do tipo XPath do W3C.</span><span class="sxs-lookup"><span data-stu-id="4079d-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="4079d-178">Todos os outros tipos são forçados para uma cadeia de caracteres chamando o método `ToString`.</span><span class="sxs-lookup"><span data-stu-id="4079d-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="4079d-179">Se a função de script utilizar um tipo diferente dos mencionados acima, ou se a função não compilar quando a folha de estilos for carregada no objeto <xref:System.Xml.Xsl.XslTransform>, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="4079d-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="4079d-180">Ao usar o elemento`msxsl:script`, é altamente recomendável que o script, independentemente da linguagem, seja colocado em uma seção CDATA.</span><span class="sxs-lookup"><span data-stu-id="4079d-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="4079d-181">Por exemplo, o XML a seguir mostra o modelo de seção CDATA onde o código é colocado.</span><span class="sxs-lookup"><span data-stu-id="4079d-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="4079d-182">É altamente recomendável que todo o conteúdo de script seja colocado em uma seção CDATA, porque os operadores, os identificadores ou os delimitadores para uma determinada linguagem têm o potencial de serem mal interpretados como XML.</span><span class="sxs-lookup"><span data-stu-id="4079d-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="4079d-183">O exemplo a seguir mostra o uso do operador lógico AND no script.</span><span class="sxs-lookup"><span data-stu-id="4079d-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="4079d-184">Isso gera uma exceção porque o E comercial não escapa.</span><span class="sxs-lookup"><span data-stu-id="4079d-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="4079d-185">O documento é carregado como XML e nenhum tratamento especial é aplicado ao texto entre as marcas de elemento de `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="4079d-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4079d-186">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4079d-186">Example</span></span>  

 <span data-ttu-id="4079d-187">O exemplo a seguir usa um script inserido para calcular a circunferência de um círculo considerando o seu raio.</span><span class="sxs-lookup"><span data-stu-id="4079d-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="4079d-188">Entrada</span><span class="sxs-lookup"><span data-stu-id="4079d-188">Input</span></span>  

 <span data-ttu-id="4079d-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="4079d-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="4079d-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="4079d-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="4079d-191">Saída</span><span class="sxs-lookup"><span data-stu-id="4079d-191">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="4079d-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="4079d-192">See also</span></span>

- [<span data-ttu-id="4079d-193">A classe XslTransform implementa do processador XSLT</span><span class="sxs-lookup"><span data-stu-id="4079d-193">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
