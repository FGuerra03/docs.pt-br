---
title: Não é possível referenciar &#39; &lt;nome&gt;&#39; porque ele é um membro do campo de tipo de valor &#39;&lt; nome&gt;&#39; de classe &#39;&lt; nome da classe&gt;&#39; que tem &#39; MarshalByRefObject &#39; como uma classe base
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Não é possível referenciar &#39; &lt;nome&gt;&#39; porque ele é um membro do campo de tipo de valor &#39;&lt; nome&gt;&#39; de classe &#39;&lt; nome da classe&gt;&#39; que tem &#39; MarshalByRefObject &#39; como uma classe base
O `System.MarshalByRefObject` classe permite que os aplicativos que oferecem suporte a acesso remoto a objetos nos limites do domínio de aplicativo. Tipos devem herdar do `MarshalByRejectObject` classe quando o tipo é usado além dos limites do domínio de aplicativo. O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.  
  
 **ID do erro:** BC30310  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se a referência para certificar-se de que o membro que está sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com o `Me` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.MarshalByRefObject>  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
