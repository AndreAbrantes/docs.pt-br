---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: ce7eb74a3e06df8db2e6d8261faca16650e4e4f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242260"
---
# <a name="transaction-models"></a><span data-ttu-id="20791-102">Modelos de transação</span><span class="sxs-lookup"><span data-stu-id="20791-102">Transaction Models</span></span>

<span data-ttu-id="20791-103">Este tópico descreve a relação entre os modelos de programação de transação e os componentes de infraestrutura fornecidos pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="20791-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="20791-104">Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você não está selecionando entre diferentes modelos transacionais, mas operando em camadas diferentes de um modelo integrado e consistente.</span><span class="sxs-lookup"><span data-stu-id="20791-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="20791-105">As seções a seguir descrevem os três componentes principais de transação.</span><span class="sxs-lookup"><span data-stu-id="20791-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="20791-106">Transações de Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="20791-106">Windows Communication Foundation Transactions</span></span>  

 <span data-ttu-id="20791-107">O suporte a transações no WCF permite que você escreva serviços transacionais.</span><span class="sxs-lookup"><span data-stu-id="20791-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="20791-108">Além disso, com seu suporte para o protocolo WS-AtomicTransaction (WS-AT), os aplicativos podem fluir transações para serviços Web criados usando o WCF ou tecnologia de terceiros.</span><span class="sxs-lookup"><span data-stu-id="20791-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="20791-109">Em um serviço ou aplicativo WCF, os recursos de transação do WCF fornecem atributos e configurações para especificar declarativamente como e quando a infraestrutura deve criar, fluir e sincronizar transações.</span><span class="sxs-lookup"><span data-stu-id="20791-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="20791-110">Transações de System. Transactions</span><span class="sxs-lookup"><span data-stu-id="20791-110">System.Transactions Transactions</span></span>  

 <span data-ttu-id="20791-111">O <xref:System.Transactions> namespace fornece um modelo de programação explícito baseado na <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, na qual a infraestrutura gerencia automaticamente as transações.</span><span class="sxs-lookup"><span data-stu-id="20791-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="20791-112">Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="20791-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="20791-113">Em um serviço ou aplicativo WCF, <xref:System.Transactions> o fornece o modelo de programação para criar transações em um aplicativo cliente e, para interagir explicitamente com uma transação, quando necessário, dentro de um serviço.</span><span class="sxs-lookup"><span data-stu-id="20791-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="20791-114">Transações MSDTC</span><span class="sxs-lookup"><span data-stu-id="20791-114">MSDTC Transactions</span></span>  

 <span data-ttu-id="20791-115">O Microsoft Coordenador de Transações Distribuídas (MSDTC) é um Gerenciador de transações que fornece suporte para transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="20791-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="20791-116">Para obter mais informações, consulte a [referência do programador do DTC](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="20791-116">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="20791-117">Em um serviço ou aplicativo WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="20791-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
