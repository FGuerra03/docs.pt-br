---
title: Subprocedimentos (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7258d57d2677042a2020097893a4f7a0adb35508
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sub-procedures-visual-basic"></a>Subprocedimentos (Visual Basic)
Um `Sub` procedimento é uma série de instruções do Visual Basic entre o `Sub` e `End Sub` instruções. O `Sub` procedimento executa uma tarefa e, em seguida, retorna o controle para o código de chamada, mas não retorna um valor para o código de chamada.  
  
 Cada vez que é chamada de procedimento, suas declarações são executadas, começando com a primeira instrução executável após o `Sub` instrução e terminando com o primeiro `End Sub`, `Exit Sub`, ou `Return` instrução encontrado.  
  
 Você pode definir um `Sub` procedimento em módulos, classes e estruturas. Por padrão, ele é `Public`, que significa que você pode chamá-lo de qualquer lugar no seu aplicativo que tem acesso para o módulo, classe ou estrutura na qual você a definiu. O termo *método*, descreve um `Sub` ou `Function` procedimento que é acessado de fora de sua definição de módulo, classe ou estrutura. Para obter mais informações, consulte [Procedimentos](./index.md).  
  
 Um `Sub` procedimento pode receber argumentos, como constantes, variáveis ou expressões que são passadas para ele pelo código de chamada.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar um `Sub` procedimento é o seguinte:  
  
 `[` *modificadores de* `] Sub` *subname* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 O `modifiers` pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento. Para obter mais informações, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Declaração de parâmetro  
 Você declara cada parâmetro de procedimento da mesma forma como você declara uma variável, especificando o tipo de dados e o nome do parâmetro. Você também pode especificar o mecanismo de passagem e se o parâmetro é opcional ou uma matriz de parâmetros.  
  
 A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *nome do parâmetro*`As`*tipo de dados*   
  
 Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração. A sintaxe para especificar um valor padrão é da seguinte maneira:  
  
 `Optional [ByVal | ByRef]`  *nome do parâmetro*`As`*datatype*`=`*defaultvalue*   
  
### <a name="parameters-as-local-variables"></a>Parâmetros como variáveis locais  
 Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local. Isso significa que seu tempo de vida é o mesmo que o procedimento e seu escopo é todo o procedimento.  
  
## <a name="calling-syntax"></a>A sintaxe de chamada  
 Invocar um `Sub` procedimento explicitamente com uma instrução de chamada autônoma. Você não pode chamá-lo usando seu nome em uma expressão. Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, opcionalmente, você pode omitir os parênteses. O uso do `Call` palavra-chave é opcional, mas não é recomendado.  
  
 A sintaxe para chamar um `Sub` procedimento é o seguinte:  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 Você pode chamar um `Sub` método de fora da classe que o define. Primeiro, você deve usar o `New` palavra-chave para criar uma instância da classe, ou chamar um método que retorna uma instância da classe. Para obter mais informações, consulte [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md). Em seguida, você pode usar a seguinte sintaxe para chamar o `Sub` método no objeto de exemplo:  
  
 *Objeto*. *MethodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 O seguinte `Sub` procedimento informa o operador do computador qual tarefa de aplicativo está prestes a executar e também exibe um carimbo de hora. Em vez de duplicar este código no início de cada tarefa, o aplicativo apenas chama `tellOperator` de vários locais. Cada chamada passa uma cadeia de caracteres de `task` argumento que identifica a tarefa que está sendo iniciada.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica para `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Como: chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)
