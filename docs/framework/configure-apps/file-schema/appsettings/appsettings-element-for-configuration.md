---
title: Elemento <appSettings> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: e1f285aae10a89fa49846534d5b47e15920294ea
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452273"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="8b1e4-102">\<appSettings > elemento para \<configuração ></span><span class="sxs-lookup"><span data-stu-id="8b1e4-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="8b1e4-103">Contém configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-103">Contains custom application settings.</span></span> <span data-ttu-id="8b1e4-104">Esta é uma seção de configuração predefinida fornecida pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="8b1e4-105">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8b1e4-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="8b1e4-106">&nbsp;&nbsp; **\<appsettings >**</span><span class="sxs-lookup"><span data-stu-id="8b1e4-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8b1e4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b1e4-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="8b1e4-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b1e4-108">Attribute</span></span>

|           | <span data-ttu-id="8b1e4-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8b1e4-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8b1e4-110">**file**</span><span class="sxs-lookup"><span data-stu-id="8b1e4-110">**file**</span></span>  | <span data-ttu-id="8b1e4-111">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-111">Optional attribute.</span></span><br><br><span data-ttu-id="8b1e4-112">Especifica um caminho relativo para um arquivo externo que contém definições de configuração de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="8b1e4-113">O arquivo especificado contém o mesmo tipo de configurações especificadas no **\<adicionar >** , **\<remover >** e\<elementos de **> Clear** e usa o mesmo formato de par de chave/valor que esses elementos.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="8b1e4-114">O caminho especificado é relativo ao arquivo de configuração principal.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="8b1e4-115">Para um aplicativo Windows Forms, essa é a pasta binária (como */bin/Debug*), não o local do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="8b1e4-116">Para aplicativos Web Forms, o caminho é relativo à raiz do aplicativo, em que o arquivo *Web. config* está localizado.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="8b1e4-117">O tempo de execução ignora o atributo se o arquivo especificado não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-117">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8b1e4-118">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="8b1e4-118">Parent element</span></span>

|     | <span data-ttu-id="8b1e4-119">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8b1e4-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8b1e4-120"> **> de configuração de\<** Elementos</span><span class="sxs-lookup"><span data-stu-id="8b1e4-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="8b1e4-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8b1e4-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b1e4-122">Child elements</span></span>

|     | <span data-ttu-id="8b1e4-123">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8b1e4-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8b1e4-124"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="8b1e4-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="8b1e4-125">Adiciona uma configuração de aplicativo personalizada.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="8b1e4-126"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="8b1e4-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="8b1e4-127">Limpa todas as configurações de aplicativo definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="8b1e4-128"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="8b1e4-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="8b1e4-129">Remove uma configuração de aplicativo definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8b1e4-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b1e4-130">Remarks</span></span>

<span data-ttu-id="8b1e4-131">O elemento **\<appsettings >** armazena informações de configuração de aplicativo personalizadas, como cadeias de conexão de banco de dados, caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="8b1e4-132">Os pares de chave/valor especificados no elemento **\<appsettings >** são acessados no código usando a classe <xref:System.Configuration.ConfigurationSettings>.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="8b1e4-133">Você pode usar o atributo **File** no elemento **\<appSettings >** dos arquivos de configuração *Web. config* e de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="8b1e4-134">Esse atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no elemento **\<appsettings >** .</span><span class="sxs-lookup"><span data-stu-id="8b1e4-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="8b1e4-135">O atributo de **arquivo** pode ser usado em cenários de desenvolvimento de equipe de controle do código-fonte, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="8b1e4-136">Os arquivos de configuração especificados pelo atributo de **arquivo** devem ter um nó raiz de **\<appSettings >** em vez de **\<> de configuração**.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="8b1e4-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b1e4-137">Example</span></span>

<span data-ttu-id="8b1e4-138">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="8b1e4-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="8b1e4-139">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="8b1e4-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="8b1e4-140">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="8b1e4-140">Configuration file</span></span>

<span data-ttu-id="8b1e4-141">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b1e4-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b1e4-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b1e4-142">See also</span></span>

- [<span data-ttu-id="8b1e4-143">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b1e4-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
