---
title: MDA moduloObjectHashcode
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216179"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="8cb19-102">MDA moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="8cb19-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="8cb19-103">O MDA (Assistente de Depuração Gerenciado) de `moduloObjectHashcode` altera o comportamento da classe <xref:System.Object> para executar uma operação de módulo no código hash retornado pelo método <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cb19-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="8cb19-104">O módulo padrão para esse MDA é 1, o que faz com que <xref:System.Object.GetHashCode%2A> retorne 0 para todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="8cb19-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8cb19-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="8cb19-105">Symptoms</span></span>  
 <span data-ttu-id="8cb19-106">Depois de migrar para uma nova versão do CLR (Common Language Runtime), um programa não é mais executado corretamente:</span><span class="sxs-lookup"><span data-stu-id="8cb19-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="8cb19-107">O programa está obtendo o objeto errado de um <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="8cb19-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="8cb19-108">A ordem de enumeração de um <xref:System.Collections.Hashtable> tem uma alteração que interrompe o programa.</span><span class="sxs-lookup"><span data-stu-id="8cb19-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="8cb19-109">Dois objetos que costumavam ser iguais não o são mais.</span><span class="sxs-lookup"><span data-stu-id="8cb19-109">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="8cb19-110">Dois objetos que costumavam não ser iguais agora o são.</span><span class="sxs-lookup"><span data-stu-id="8cb19-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8cb19-111">Causa</span><span class="sxs-lookup"><span data-stu-id="8cb19-111">Cause</span></span>  
 <span data-ttu-id="8cb19-112">Seu programa pode estar obtendo o objeto errado de um <xref:System.Collections.Hashtable> porque a implementação do método <xref:System.Object.Equals%2A> na classe para a chave no <xref:System.Collections.Hashtable> testa a igualdade de objetos ao comparar os resultados da chamada para o método <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cb19-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="8cb19-113">Códigos hash não devem ser usados para testar a igualdade de objetos porque os dois objetos podem ter o mesmo código hash, mesmo que seus respectivos campos tenham valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="8cb19-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="8cb19-114">Esses conflitos de código hash, embora raros na prática, ocorrem.</span><span class="sxs-lookup"><span data-stu-id="8cb19-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="8cb19-115">O efeito disso em uma pesquisa <xref:System.Collections.Hashtable> é que duas chaves que não são iguais parecem ser e o objeto errado é retornado do <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="8cb19-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="8cb19-116">Por motivos de desempenho, a implementação de <xref:System.Object.GetHashCode%2A> pode variar entre as versões de runtime, então colisões que podem não ocorrer em uma versão podem ocorrer em versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="8cb19-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="8cb19-117">Quando códigos hash entrarem em conflito, habilite esse MDA para testar se o seu código tem bugs.</span><span class="sxs-lookup"><span data-stu-id="8cb19-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="8cb19-118">Quando habilitado, esse MDA faz com que o método <xref:System.Object.GetHashCode%2A> retorne 0, resultando em uma colisão de todos os códigos hash.</span><span class="sxs-lookup"><span data-stu-id="8cb19-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="8cb19-119">O único efeito que habilitar esse MDA deve ter em seu programa é tornar a execução dele mais lenta.</span><span class="sxs-lookup"><span data-stu-id="8cb19-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="8cb19-120">A ordem de enumeração de um <xref:System.Collections.Hashtable> poderá variar de uma versão de runtime para outra se o algoritmo usado para calcular os códigos hash para a chave for alterado.</span><span class="sxs-lookup"><span data-stu-id="8cb19-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="8cb19-121">Para testar se o seu programa obteve uma dependência na ordem de enumeração de chaves ou valores de uma tabela de hash, você pode habilitar esse MDA.</span><span class="sxs-lookup"><span data-stu-id="8cb19-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8cb19-122">Resolução</span><span class="sxs-lookup"><span data-stu-id="8cb19-122">Resolution</span></span>  
 <span data-ttu-id="8cb19-123">Nunca use códigos hash como um substituto para a identidade do objeto.</span><span class="sxs-lookup"><span data-stu-id="8cb19-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="8cb19-124">Implemente a substituição do método <xref:System.Object.Equals%2A?displayProperty=nameWithType> para não comparar códigos hash.</span><span class="sxs-lookup"><span data-stu-id="8cb19-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="8cb19-125">Não crie dependências na ordem das enumerações de chaves ou valores em tabelas de hash.</span><span class="sxs-lookup"><span data-stu-id="8cb19-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8cb19-126">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="8cb19-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="8cb19-127">Os aplicativos são executados mais lentamente quando esse MDA está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8cb19-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="8cb19-128">Esse MDA simplesmente usa o código hash que teria sido retornado e em vez disso, retorna o resto quando dividido por um módulo.</span><span class="sxs-lookup"><span data-stu-id="8cb19-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8cb19-129">Saída</span><span class="sxs-lookup"><span data-stu-id="8cb19-129">Output</span></span>  
 <span data-ttu-id="8cb19-130">Não há nenhuma saída para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="8cb19-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8cb19-131">Configuração</span><span class="sxs-lookup"><span data-stu-id="8cb19-131">Configuration</span></span>  
 <span data-ttu-id="8cb19-132">O atributo `modulus` especifica o módulo usado no código hash.</span><span class="sxs-lookup"><span data-stu-id="8cb19-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="8cb19-133">O valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="8cb19-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cb19-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="8cb19-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8cb19-135">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="8cb19-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
