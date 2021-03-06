---
title: -optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ad78c82303d3655d5dda9e2286df0a55b8bf3e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-optionexplicit"></a>-optionexplicit
Faz com que o compilador para relatar erros se variáveis não são declaradas antes de serem usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especifique `-optionexplicit+` para requer declaração explícita de variáveis. O `-optionexplicit+` opção é o padrão e é o mesmo que `-optionexplicit`. O `-optionexplicit-` opção permite que a declaração implícita de variáveis.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código fonte contém um [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substitui a `-optionexplicit` configuração do compilador de linha de comando.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Para definir /optionexplicit - no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2.  Clique na guia **Compilar**.  
  
3.  Modificar o valor de **Option Explicit** caixa.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila quando `-optionexplicit-` é usado.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
