---
title: Nomes de assembly
description: Saiba mais sobre os nomes de assembly .NET e seu impacto sobre o escopo do assembly e uso por um aplicativo e saiba mais sobre a propriedade FullName.
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 5a499f4f04c84de8d6542d7107d7a707b808e47f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379882"
---
# <a name="assembly-names"></a>Nomes de assembly
Um nome de assembly é armazenado em metadados e tem um impacto significativo no escopo e uso do assembly por um aplicativo. Um assembly de nome forte tem um nome totalmente qualificado que inclui o nome, a cultura, a chave pública e o número de versão do assembly. Isso muitas vezes é chamado de nome de exibição, e para os assemblies carregados pode ser obtido usando a propriedade <xref:System.Reflection.Assembly.FullName%2A>.

 O runtime usa essas informações para localizar o assembly e diferenciá-lo de outros assemblies com o mesmo nome. Por exemplo, um assembly de nome forte chamado `myTypes` poderia ter o seguinte nome totalmente qualificado:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> A arquitetura do processador é adicionada à identidade do assembly na versão 2.0 do .NET Framework, para permitir versões específicas do processador de assemblies. Crie versões de um assembly cuja identidade varie apenas pela arquitetura do processador, por exemplo, versões específicas de processador 32 bits e 64 bits. A arquitetura do processador não é necessária para nomes fortes. Para obter mais informações, consulte <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Neste exemplo, o nome totalmente qualificado indica que o assembly `myTypes` tem um nome forte com um token de chave pública, tem o valor de cultura para inglês (EUA) e tem um número de versão de 1.0.1234.0. A arquitetura de seu processador é "msil", que significa que ele será compilado no modo JIT (just-in-time) para códigos de 32 bits ou 64 bits dependendo do sistema operacional e do processador.

 O código que solicita tipos em um assembly deve usar um nome totalmente qualificado do assembly. Isso é chamado de associação totalmente qualificada. A associação parcial, que especifica um nome de assembly, não tem permissão ao fazer referência a assemblies no .NET Framework.

 Todas as referências de assembly a assemblies que compõem o .NET Framework também devem conter o nome totalmente qualificado do assembly. Por exemplo, uma referência ao assembly System. Data .NET Framework para a versão 1,0 incluiria:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Observe que a versão corresponde ao número de versão de todos os assemblies do .NET Framework que acompanham o .NET Framework versão 1.0. Para assemblies do .NET Framework, o valor da cultura é sempre neutro, e a chave pública é a mesma mostrada no exemplo acima.

 Por exemplo, para adicionar uma referência de assembly em um arquivo de configuração a fim de configurar um ouvinte de rastreamento, você incluiria o nome totalmente qualificado do assembly do .NET Framework do sistema:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> O runtime trata nomes de assembly sem diferenciar maiúsculas de minúsculas ao associar a um assembly, mas preserva qualquer caso usado em um nome de assembly. Várias ferramentas no SDK do Windows lidam com nomes de assembly diferenciando maiúsculas de minúsculas. Para obter melhores resultados, gerencie nomes de assembly como se diferenciassem maiúsculas de minúsculas.

## <a name="name-application-components"></a>Nomear componentes de aplicativos
 O runtime não considera o nome do arquivo ao determinar a identidade de um assembly. A identidade do assembly, composta pelo nome, versão, cultura e nome forte do assembly, deve ficar clara para o runtime.

 Por exemplo, se você tiver um assembly chamado *myAssembly. exe* que faz referência a um assembly chamado *myAssembly. dll*, a vinculação ocorrerá corretamente se você executar *myAssembly. exe*. No entanto, se outro aplicativo executar o *myAssembly. exe* usando o método <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> , o tempo de execução determinará que `myAssembly` já está carregado quando o *myAssembly. exe* solicitará a associação ao `myAssembly` . Nesse caso, *myAssembly. dll* nunca é carregado. Como o *myAssembly. exe* não contém o tipo solicitado, <xref:System.TypeLoadException> ocorre um erro.

 Para evitar esse problema, verifique se os assemblies que compõem seu aplicativo não têm o mesmo nome de assembly ou colocam assemblies com o mesmo nome em diretórios diferentes.

> [!NOTE]
> Na .NET Framework, se você colocar um assembly de nome forte no cache de assembly global, o nome do arquivo do assembly deverá corresponder ao nome do assembly, não incluindo a extensão de nome de arquivo, como *. exe* ou *. dll*. Por exemplo, se o nome de arquivo de um assembly for *myAssembly. dll*, o nome do assembly deverá ser `myAssembly` . Assemblies particulares implantados somente no diretório do aplicativo raiz podem ter um nome de assembly diferente do nome do arquivo.

## <a name="see-also"></a>Confira também

- [Como determinar o nome totalmente qualificado de um assembly](find-fully-qualified-name.md)
- [Criar assemblies](create.md)
- [Assemblies de nome forte](strong-named.md)
- [Cache de assembly global](../../framework/app-domains/gac.md)
- [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
