---
title: Configurações do Registro de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186171"
---
# <a name="cleartype-registry-settings"></a>Configurações do Registro de ClearType
Este tópico fornece uma visão geral das configurações de registro do Microsoft ClearType que são usadas por aplicativos WPF.  

<a name="overview"></a>
## <a name="technology-overview"></a>Visão geral da tecnologia  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplicativos que tornam texto para um dispositivo de exibição usam recursos do ClearType para fornecer uma experiência de leitura aprimorada. ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (Liquid Crystal Displays), como telas de laptop, telas de Pocket PC e monitores de tela plana. O ClearType funciona acessando os elementos de listras de cores verticais individuais em cada pixel de uma tela LCD. Para obter mais informações sobre clearType, consulte [ClearType Overview](cleartype-overview.md).  
  
 O texto renderizado com o ClearType pode aparecer significativamente diferente quando visualizado em vários dispositivos de exibição. Por exemplo, um pequeno número de monitores implementam os elementos de listras de cor em azul, verde, vermelho, em vez da ordem mais comum vermelho, verde, azul (RGB).  
  
 O texto renderizado com clearType também pode aparecer significativamente diferente quando visto por indivíduos com diferentes níveis de sensibilidade à cor. Algumas pessoas podem detectar pequenas diferenças nas cores melhor do que outras.  
  
 Em cada um desses casos, os recursos do ClearType precisam ser modificados para proporcionar a melhor experiência de leitura para cada indivíduo.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Configurações do registro  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]especifica quatro configurações de registro para controlar os recursos do ClearType:  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nível ClearType|Descreve o nível de clareza de cor ClearType.|  
|Nível de gama|Descreve o nível do componente de cor do pixel para um dispositivo de vídeo.|  
|Estrutura de Pixel|Descreve a disposição dos pixels para um dispositivo de vídeo.|  
|Nível de contraste do texto|Descreve o nível de contraste para o texto exibido.|  
  
 Essas configurações podem ser acessadas por um utilitário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de configuração externa que sabe como referenciar as configurações de registro ClearType identificadas. Essas configurações também podem ser criadas ou modificadas acessando os valores diretamente usando o Editor de Registro do Windows.  
  
 Se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as configurações do registro ClearType não estiverem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definidas (que é o estado padrão), o aplicativo consulta as informações dos parâmetros do sistema Windows para as configurações de suavização da fonte.  
  
> [!NOTE]
> Para obter informações sobre a enumeração de nomes de dispositivos de exibição, consulte a `SystemParametersInfo`função Win32.  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>Nível de ClearType  
 O nível ClearType permite ajustar a renderização do texto com base na sensibilidade de cor e percepção de um indivíduo. Para alguns indivíduos, a renderização de texto que usa clearType em seu nível mais alto não produz a melhor experiência de leitura.  
  
 O nível ClearType é um valor inteiro que varia de 0 a 100. O nível padrão é 100, o que significa que o ClearType usa a capacidade máxima dos elementos de faixa de cor do dispositivo de exibição. No entanto, um nível ClearType de 0 renderiza o texto como escala cinza. Ao definir o nível ClearType em algum lugar entre 0 e 100, você pode criar um nível intermediário adequado à sensibilidade de cor de um indivíduo.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 O local de configuração do registro para o nível ClearType é uma configuração individual do usuário que corresponde a um nome específico do dispositivo de exibição:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome do dispositivo `ClearTypeLevel` de exibição para um usuário, um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor de registro para o nível ClearType.  
  
 ![Configurações do ClearType no Editor de registro.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplicativos renderizam texto em um dos dois modos, com e sem ClearType. Quando o texto é renderizado sem ClearType, ele é referido como renderização em escala cinza.  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Nível de Gama  
 O nível de fama se refere à relação não linear entre o valor de um pixel e a luminância. A configuração do nível de gama deve corresponder às características físicas do dispositivo de vídeo. Caso contrário, podem ocorrer distorções na saída renderizada. Por exemplo, o texto pode parecer muito largo ou muito estreito, ou franjas de cor podem aparecer nas bordas de hastes verticais de glifos.  
  
 O nível de gama é um valor inteiro que varia de 1000 a 2200. O nível padrão é 1900.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de gama é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome do dispositivo `GammaLevel` de exibição para um usuário, um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de gama.  
  
 ![Configurações de nível gama ClearType no Editor de registro](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>Estrutura de pixel  
 A estrutura de pixel descreve o tipo de pixels que compõem um dispositivo de vídeo. A estrutura de pixel é definida como um de três tipos:  
  
|Type|Valor|Descrição|  
|----------|-----------|-----------------|  
|Plano|0|O dispositivo de vídeo não tem uma estrutura de pixel. Isso significa que as fontes de luz para cada cor são distribuídas igualmente na área de pixel — isso é conhecido como renderização em escala de cinza. É assim que um dispositivo de vídeo padrão funciona. O ClearType nunca é aplicado ao texto renderizado.|  
|RGB|1|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: vermelho, verde e azul. ClearType é aplicado ao texto renderizado.|  
|BGR|2|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: azul, verde e vermelho. ClearType é aplicado ao texto renderizado. Observe como a ordem é invertida com relação ao tipo RGB.|  
  
 A estrutura de pixel corresponde a um valor inteiro que vai de 0 a 2. O nível padrão é 0, que representa uma estrutura de pixel plana.  
  
> [!NOTE]
> Para obter informações sobre a enumeração de nomes de dispositivos de exibição, consulte a `EnumDisplayDevices`função Win32.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para a estrutura de pixel é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome do dispositivo `PixelStructure` de exibição para um usuário, um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para a estrutura de pixel.  
  
 ![Configurações de nível gama ClearType no Editor de registro](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>Nível de Contraste do Texto  
 O nível de contraste do texto permite que você ajuste a renderização do texto com base nas larguras dos troncos dos glifos. O nível de contraste do texto é um valor inteiro que varia de 0 a 6 — quanto maior o valor inteiro, mais largo o tronco. O nível padrão é 1.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de contraste do texto é uma configuração individual do usuário que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome do dispositivo `TextContrastLevel` de exibição para um usuário, um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de contraste do texto.  
  
 ![Configurações do ClearType no Editor de registro.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Confira também

- [Visão geral de ClearType](cleartype-overview.md)
- [Suavização de ClearType](/windows/desktop/gdi/cleartype-antialiasing)
