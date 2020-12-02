---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478530"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="486eb-101">Contract.Invariant ou Contract.Requires\<TException> não consideram String.IsNullOrEmpty puro</span><span class="sxs-lookup"><span data-stu-id="486eb-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="486eb-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="486eb-102">Details</span></span>

<span data-ttu-id="486eb-103">Para aplicativos direcionados para o .NET Framework 4.6.1, se o contrato invariável para o <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> ou o contrato de pré-condição para <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> chamar o <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> método, o regravador emitirá o aviso do compilador CC1036: &quot; chamada para o método ' System. String. IsNullOrWhiteSpace (System. String) ' sem [Pure] no método. &quot; Esse é um aviso do compilador em vez de um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="486eb-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="486eb-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="486eb-104">Suggestion</span></span>

<span data-ttu-id="486eb-105">Esse comportamento foi abordado em [Problema nº 339 no GitHub](https://github.com/Microsoft/CodeContracts/issues/339).</span><span class="sxs-lookup"><span data-stu-id="486eb-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="486eb-106">Para eliminar esse aviso, você pode baixar e compilar uma versão atualizada do código-fonte para a ferramenta de Contratos de Código no [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="486eb-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="486eb-107">As informações para download são encontradas no fim da página.</span><span class="sxs-lookup"><span data-stu-id="486eb-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="486eb-108">Nome</span><span class="sxs-lookup"><span data-stu-id="486eb-108">Name</span></span>    | <span data-ttu-id="486eb-109">Valor</span><span class="sxs-lookup"><span data-stu-id="486eb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="486eb-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="486eb-110">Scope</span></span>   |<span data-ttu-id="486eb-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="486eb-111">Minor</span></span>|
|<span data-ttu-id="486eb-112">Versão</span><span class="sxs-lookup"><span data-stu-id="486eb-112">Version</span></span>|<span data-ttu-id="486eb-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="486eb-113">4.6.1</span></span>|
|<span data-ttu-id="486eb-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="486eb-114">Type</span></span>|<span data-ttu-id="486eb-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="486eb-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="486eb-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="486eb-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
