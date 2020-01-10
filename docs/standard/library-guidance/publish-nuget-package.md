---
title: Publicar um pacote NuGet
description: Práticas recomendadas para a publicação de bibliotecas .NET para NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706459"
---
# <a name="publishing-a-nuget-package"></a>Publicar um pacote NuGet

Os pacotes NuGet são publicados e consumidos dos repositórios de pacote. Embora o NuGet.org seja o repositório mais amplamente conhecido e usado, há muitos locais para publicar pacotes NuGet:

* **[NuGet.org](https://www.nuget.org/)** é o principal repositório online para pacotes NuGet. Todos os pacotes no NuGet.org estão disponíveis publicamente para todos. Por padrão, o Visual Studio tem o NuGet.org como fonte de pacotes, e para muitos desenvolvedores o NuGet.org é o único repositório de pacotes com o qual eles vão interagir. O NuGet.org é o melhor lugar para publicar pacotes estáveis e pacotes de pré-lançamento para os quais você deseja comentários da comunidade.

* **[MyGet](https://myget.org/)** é um serviço de repositório que oferece suporte aos feeds de pacotes personalizados para projetos de software livre. Um feed personalizado público do MyGet é um local ideal para publicar pacotes de pré-lançamento criados pelo seu serviço de CI. O MyGet também fornece comercialmente feeds privados.

* Um **[feed local](/nuget/hosting-packages/local-feeds)** permite que você trate uma pasta como um repositório de pacotes e torna os arquivos `*.nupkg` na pasta acessível pelo NuGet. Um feed local é útil para testar um pacote do NuGet antes de publicá-lo no NuGet.org.

> [!NOTE]
> O NuGet.org [não permite que um pacote seja excluído](/nuget/policies/deleting-packages) depois que ele foi carregado. Um pacote pode ser não listado para que não seja visível publicamente na interface do usuário, mas o `*.nupkg` ainda pode ser baixado na restauração. Além disso, o nuget.org não permite versões duplicadas do pacote. Para corrigir um pacote NuGet com um erro, você precisa remover o pacote incorreto, aumentar o número de versão e publicar uma nova versão do pacote.

**✔️** [publicar pacotes estáveis e pacotes de pré-lançamento](/nuget/create-packages/publish-a-package) nos quais você deseja que os comentários da Comunidade NuGet.org.

**✔️ CONSIDERE:** publique pacotes de pré-lançamento no feed MyGet de uma compilação de integração contínua.

**✔️ CONSIDERE:** teste os pacotes no ambiente de desenvolvimento usando um feed local ou MyGet. Verifique se o pacote funciona e publique-o no NuGet.org.

## <a name="nugetorg-security"></a>Segurança no NuGet.org

É importante que os invasores não possam acessar sua conta do NuGet e carregar uma versão mal-intencionado da sua biblioteca. O NuGet.org oferece autenticação de dois fatores e notificações por email quando um pacote é publicado. Habilite esses recursos após fazer logon no NuGet.org, na página **Configurações de conta**.

![alt text](./media/publish-nuget-package/nuget-2fa.png "Segurança da conta do NuGet")

**✔️ SIM:** use uma conta da Microsoft para entrar no NuGet.

**✔️ SIM:** habilite a autenticação de dois fatores para acessar o NuGet.

**✔️ SIM:** habilite a notificação por email quando um pacote é publicado.

>[!div class="step-by-step"]
>[Anterior](sourcelink.md)
>[Próximo](versioning.md)
