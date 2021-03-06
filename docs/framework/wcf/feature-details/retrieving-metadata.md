---
title: Recuperando metadados
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 212ea49418d5e33d79a1b6cf881e2828388c657e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295503"
---
# <a name="retrieving-metadata"></a>Recuperando metadados

A recuperação de metadados é o processo de solicitar e recuperar metadados de um ponto de extremidade de metadados, como um ponto de extremidade de metadados de WS-MetadataExchange (MEX) ou um ponto de extremidade de metadados HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Recuperando metadados da linha de comando usando Svcutil.exe  

 Você pode recuperar os metadados de serviço usando as solicitações WS-MetadataExchange ou HTTP/GET usando a ferramenta [Svcutil.exe (ferramenta de utilitário de metadados ServiceModel)](../servicemodel-metadata-utility-tool-svcutil-exe.md) e passando o `/target:metadata` comutador e um endereço. Svcutil.exe baixa os metadados no endereço especificado e salva o arquivo em disco. Svcutil.exe usa uma <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância internamente e carrega da configuração a <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade cujo nome corresponde ao esquema do endereço passado para Svcutil.exe como entrada.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Recuperando metadados de forma programática usando o MetadataExchangeClient  

 O Windows Communication Foundation (WCF) pode recuperar metadados de serviço usando protocolos padronizados, como WS-MetadataExchange e solicitações HTTP/GET. Os dois protocolos têm suporte do <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo. Você recupera os metadados de serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo fornecendo um endereço para o ponto de extremidade de metadados e uma associação opcional. A associação usada por uma <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância pode ser uma das associações padrão da <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe estática, uma associação fornecida pelo usuário ou uma associação carregada de uma configuração de ponto de extremidade para o `IMetadataExchange` contrato. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> também pode resolver referências de URL http para metadados usando o <xref:System.Net.HttpWebRequest> tipo.  
  
 Por padrão, uma <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância está vinculada a uma única <xref:System.ServiceModel.ChannelFactory> instância. Você pode alterar ou substituir a <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> método virtual. Da mesma forma, você pode alterar ou substituir a <xref:System.Net.HttpWebRequest> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para fazer solicitações HTTP/Get substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> método virtual.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Como: usar Svcutil.exe para baixar documentos de metadados](how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Demonstra como usar Svcutil.exe para baixar documentos de metadados.  
  
 [Como: usar MetadataResolver para obter metadados de associação dinamicamente](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Demonstra como usar o <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> para obter metadados de associação dinamicamente em tempo de execução.  
  
 [Como: usar MetadataExchangeClient para recuperar metadados](how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Demonstra como usar a <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> classe para baixar arquivos de metadados em um <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objeto que contém <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objetos para gravar em arquivos ou para outros usos.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
