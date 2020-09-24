---
title: Mapeamento externo
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 79427cde0784746480e851cf1be56c8bce854919
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161380"
---
# <a name="external-mapping"></a><span data-ttu-id="de1a2-102">Mapeamento externo</span><span class="sxs-lookup"><span data-stu-id="de1a2-102">External Mapping</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="de1a2-103">dá suporte ao *mapeamento externo*, um processo pelo qual você usa um arquivo XML separado para especificar o mapeamento entre o modelo de dados do banco de dado e o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="de1a2-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="de1a2-104">As vantagens de usar um arquivo de mapeamento externo incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="de1a2-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="de1a2-105">Você pode manter seu código de mapeamento fora de seu código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de1a2-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="de1a2-106">Essa abordagem reduz a confusão no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de1a2-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="de1a2-107">Você pode manipular um arquivo de mapeamento externo algo como um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="de1a2-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="de1a2-108">Por exemplo, você pode atualizar como o aplicativo se comporta após enviar os binários apenas alternando para fora o arquivo de mapeamento externo.</span><span class="sxs-lookup"><span data-stu-id="de1a2-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de1a2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de1a2-109">Requirements</span></span>  

 <span data-ttu-id="de1a2-110">O arquivo de mapeamento deve ser um arquivo XML e o arquivo deve ser validado em relação a um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivo de definição de esquema (. xsd).</span><span class="sxs-lookup"><span data-stu-id="de1a2-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="de1a2-111">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="de1a2-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="de1a2-112">O arquivo de mapeamento deve ser um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="de1a2-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="de1a2-113">O arquivo de mapeamento de XML deve ser válido no arquivo de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="de1a2-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="de1a2-114">Para obter mais informações, consulte [como: validar o dbml e os arquivos de mapeamento externos](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="de1a2-114">For more information, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="de1a2-115">As substituições externos de mapeamento atributos com o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="de1a2-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="de1a2-116">Ou seja quando você usa uma fonte externa de mapeamento para criar <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignora todos os atributos de mapeamento que você criou em classes.</span><span class="sxs-lookup"><span data-stu-id="de1a2-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="de1a2-117">Esse comportamento é verdadeiro se a classe está incluída no arquivo de mapeamento externo.</span><span class="sxs-lookup"><span data-stu-id="de1a2-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="de1a2-118">não oferece suporte ao uso híbrido das duas abordagens mapeando (com base em atributos e externos).</span><span class="sxs-lookup"><span data-stu-id="de1a2-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="de1a2-119">Arquivo de Definição de Esquema XML</span><span class="sxs-lookup"><span data-stu-id="de1a2-119">XML Schema Definition File</span></span>  

 <span data-ttu-id="de1a2-120">O mapeamento externa em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] deve ser válido com a seguinte definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="de1a2-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="de1a2-121">Distinguir este arquivo de definição do esquema do arquivo de definição do esquema que é usado para validar um arquivo DBML.</span><span class="sxs-lookup"><span data-stu-id="de1a2-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="de1a2-122">Para obter mais informações, consulte [geração de código no LINQ to SQL](code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="de1a2-122">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de1a2-123">Os usuários do Visual Studio também encontrarão esse arquivo XSD na caixa de diálogo esquemas XML como "LinqToSqlMapping. xsd".</span><span class="sxs-lookup"><span data-stu-id="de1a2-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="de1a2-124">Para usar esse arquivo corretamente para validar um arquivo de mapeamento externo, consulte [como validar arquivos dbml e de mapeamento externo](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="de1a2-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de1a2-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="de1a2-125">See also</span></span>

- [<span data-ttu-id="de1a2-126">Geração de código em LINQ para SQL</span><span class="sxs-lookup"><span data-stu-id="de1a2-126">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="de1a2-127">Referência</span><span class="sxs-lookup"><span data-stu-id="de1a2-127">Reference</span></span>](reference.md)
- [<span data-ttu-id="de1a2-128">Como: gerar o modelo de objeto como um arquivo externo</span><span class="sxs-lookup"><span data-stu-id="de1a2-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
