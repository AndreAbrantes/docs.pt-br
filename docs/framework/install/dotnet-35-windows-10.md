---
title: Instalar o .NET Framework 3,5 no Windows 10, 8,1, 8
description: Saiba como instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: cfe21c0821b8f3223301dcc802533e1aaf024a79
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965939"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8

Talvez você precise do .NET Framework 3.5 para executar um aplicativo no Windows 10, no Windows 8.1 e no Windows 8. Você também pode usar essas instruções para versões anteriores do Windows.

## <a name="download-the-offline-installer"></a>Baixar o instalador offline

O instalador offline do .NET Framework 3,5 SP1 está disponível na [página de download do .NET Framework 3,5 SP1](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) e está disponível para versões do Windows anteriores ao Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Instalação do .NET Framework 3.5 sob demanda

Se você tentar executar um aplicativo que exige o .NET Framework 3.5, você verá a seguinte caixa de diálogo de configuração. Escolha **Instalar este recurso** para habilitar o .NET Framework 3.5. Essa opção exige uma conexão com a Internet.

![Captura de tela da caixa de diálogo de instalação do .NET Framework.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Por que estou recebendo este pop-up?

O .NET Framework é criado pela Microsoft e fornece um ambiente para a execução de aplicativos. Há versões diferentes disponíveis. Muitas empresas desenvolvem seus aplicativos para serem executados usando o .NET Framework, e esses aplicativos têm como destino uma versão específica. Quando vê esse pop-up, você está tentando executar um aplicativo que requer o .NET Framework versão 3.5, mas essa versão não está instalada em seu sistema.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Habilitar o .NET Framework 3.5 no Painel de Controle

Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle do Windows. Essa opção exige uma conexão com a Internet.

1. Pressione a tecla Windows ![captura de tela do logotipo da tecla Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) no teclado, digite "recursos do Windows" e pressione Enter. A caixa de diálogo **Ativar ou desativar recursos do Windows** é exibida.

2. Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)** , selecione **OK** e reinicialize o computador, se isso for solicitado.

   ![Captura de tela mostrando a instalação do .NET com o painel de controle.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Não é necessário selecionar os itens filho para a **Ativação HTTP do WCF (Windows Communication Foundation)** e para a **Ativação Não HTTP do WCF (Windows Communication Foundation)** , a menos que você seja um desenvolvedor ou administrador de servidor que exija essa funcionalidade.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Solucionar problemas de instalação do .NET Framework 3.5

Durante a instalação, você poderá se deparar com o erro 0x800f0906, 0x800f0907, 0x800f081f ou 0x800F0922. Nesse caso, consulte [Erro de instalação do .NET Framework 3.5: 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) para descobrir como resolver esses problemas.

Se ainda não conseguir resolver o problema de instalação ou se não tiver uma conexão com a Internet, você poderá tentar instalá-lo usando a mídia de instalação do Windows. Para obter mais informações, consulte [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism) (Implantar o .NET Framework 3.5 usando o DISM (Gerenciamento e Manutenção de Imagens de Implantação)). Se você não tiver a mídia de instalação, confira [Criar mídia de instalação para Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Se você não conta com o Windows Update como a origem de instalação do .NET Framework 3.5, use obrigatoriamente origens que sejam da mesma versão do sistema operacional Windows correspondente. O uso de um caminho de origem que não corresponde à mesma versão do Windows não impede a instalação de uma versão incompatível do .NET Framework 3.5. No entanto, isso fará com que o sistema fique em um estado sem suporte e sem manutenção.
