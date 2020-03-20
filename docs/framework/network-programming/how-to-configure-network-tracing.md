---
title: Como configurar o rastreamento de rede
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040649"
---
# <a name="how-to-configure-network-tracing"></a>Como: Configurar rastreamento de rede

O aplicativo ou o arquivo de configuração do computador mantém as configurações que determinam o formato e o conteúdo dos rastreamentos de rede. Antes de executar este procedimento, certifique-se de que o rastreamento está habilitado. Para obter mais informações, consulte [Ativar rastreamento de rede](enabling-network-tracing.md).

O arquivo de configuração do computador, *machine.config,* é armazenado na pasta *%windir%\Microsoft.NET\Framework.* Há um arquivo de *máquina.config* separado nas pastas em *%windir%\Microsoft.NET\Framework* para cada versão do .NET Framework instalado no computador, por exemplo:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.

## <a name="configure-network-tracing"></a>Configurar rastreamento de rede

Para configurar o rastreamento de rede, adicione as seguintes linhas ao arquivo de configuração apropriado. Os valores e as opções dessas configurações são descritos nas tabelas abaixo.

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a>Trace saída de métodos

Quando você adiciona um nome para o bloco `<switches>`, a saída de rastreamento inclui informações de alguns métodos relacionados ao nome. A tabela a seguir descreve a saída:

|Nome|Saída de|
|----------|-----------------|
|`System.Net.Sockets`|Alguns métodos <xref:System.Net.Sockets.Socket>públicos <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.TcpClient>das <xref:System.Net.Dns> classes e classes.|
|`System.Net`|Alguns métodos <xref:System.Net.HttpWebRequest>públicos <xref:System.Net.HttpWebResponse> <xref:System.Net.FtpWebRequest>das, <xref:System.Net.FtpWebResponse> e classes e informações de depuração SSL (certificados inválidos, lista de emissores ausentes e erros de certificado do cliente).|
|`System.Net.HttpListener`|Alguns métodos públicos das classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> e <xref:System.Net.HttpListenerResponse>.|
|`System.Net.Cache`|Alguns métodos particulares e internos em `System.Net.Cache`.|
|`System.Net.Http`|Alguns métodos públicos das classes <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> e <xref:System.Net.Http.WebRequestHandler>.|
|`System.Net.WebSockets.WebSocket`|Alguns métodos públicos das classes <xref:System.Net.WebSockets.ClientWebSocket> e <xref:System.Net.WebSockets.WebSocket>.|

### <a name="trace-output-attributes"></a>Atributos de saída de rastreamento

Os atributos listados na tabela a seguir configuram saída de rastreamento:

|Nome do atributo|Valor do atributo|
|--------------------|---------------------|
|`value`|Atributo <xref:System.String> obrigatório. Define o detalhamento da saída. Valores legítimos são `Critical`, `Error`, `Verbose`, `Warning` e `Information`.<br /><br />Este atributo deve ser definido no elemento **de adição** do elemento **switches.** Uma exceção é lançada se esse atributo for definido no elemento **de origem.**<br/><br/>Exemplo: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Atributo <xref:System.Int32> opcional. Define o número máximo de bytes de dados de rede inclusos em cada linha de rastreamento. O valor padrão é 1.024.<br /><br />Este atributo deve ser definido no elemento **de origem.** Uma exceção é lançada se esse atributo for definido em um elemento o elemento **switches.**<br/><br/>Exemplo: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Atributo <xref:System.String> opcional. Definido como `includehex` para exibir rastreamentos de protocolo em formato hexadecimal e textual. Definido como `protocolonly` para exibir somente o texto. O valor padrão é `includehex`.<br /><br />Este atributo deve ser definido no elemento **de origem.** Uma exceção é lançada se esse atributo for definido em um elemento o elemento **switches.**<br/><br/>Exemplo: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Confira também

- [Interpretando o rastreamento de rede](interpreting-network-tracing.md)
- [Rastreamento de rede no .NET Framework](network-tracing.md)
- [Habilitando o rastreamento de rede](enabling-network-tracing.md)
- [Rastreamento e instrumentação de aplicativos](../debug-trace-profile/tracing-and-instrumenting-applications.md)
