---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5035466de4aa17c374824e1b0f02ed594731a9d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716806"
---
# <a name="-define-visual-basic"></a>-definir (Visual Basic)
Define as constantes de compilador condicional.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

ou

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`symbol`|Necessária. O símbolo a ser definido.|  
|`value`|Opcional. O valor para atribuir `symbol`. Se `value` for uma cadeia de caracteres, ela deverá ser cercada por sequências de barra invertida/aspas (\\") em vez de aspas. Se nenhum valor for especificado, será considerado como True.|  
  
## <a name="remarks"></a>Comentários  
 A opção `-define` tem um efeito semelhante a usar uma diretiva de pré-processador de `#Const` em seu arquivo de origem, exceto que as constantes definidas com `-define` são públicas e se aplicam a todos os arquivos no projeto.  
  
 Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.  
  
 `-d` é a forma abreviada de `-define`.  
  
 Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.  
  
|Para definir-definir no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1. ter um projeto selecionado em **Gerenciador de soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2. Clique na guia **Compilar** .<br />3. clique em **avançado**.<br />4. modifique o valor na caixa **constantes personalizadas** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir define e usa duas constantes de compilador condicional.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Veja também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
