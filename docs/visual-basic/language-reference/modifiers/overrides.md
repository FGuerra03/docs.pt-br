---
title: "Substituições (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="overrides-visual-basic"></a>Substituições (Visual Basic)
Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Overrides` somente na declaração de uma propriedade ou procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `Overrides` junto com `Shadows` ou `Shared` na mesma declaração. Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides`.  
  
-   **Correspondência de assinaturas.** A assinatura dessa declaração deve corresponder exatamente a *assinatura* da propriedade ou procedimento que ela substitui. Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.  
  
     Além da assinatura, a declaração de substituição deve corresponder exatamente também o seguinte:  
  
    -   O nível de acesso  
  
    -   O tipo de retorno, se houver  
  
-   **Assinaturas genéricas.** Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo. Portanto, a declaração de substituição deve corresponder à versão de classe base em também.  
  
-   **Correspondência adicionais.** Além de correspondência a assinatura da versão da classe base, essa declaração deve também coincidir nos seguintes aspectos:  
  
    -   Modificador de nível de acesso (como [pública](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Mecanismo de passagem de cada parâmetro ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Listas de restrições em cada parâmetro de tipo de um procedimento genérico  
  
-   **Sombreamento e sobreposição.** Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Se você usar `Overrides`, o compilador adiciona implicitamente `Overloads` para que sua biblioteca de APIs trabalhar mais facilmente com c#.  
  
 O `Overrides` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
