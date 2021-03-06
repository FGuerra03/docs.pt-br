---
title: Tipos de dados de resultados do operador (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508329894758436158970760ba0d13a7780f83db
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="data-types-of-operator-results-visual-basic"></a>Tipos de dados de resultados do operador (Visual Basic)
Visual Basic determina o tipo de dados de resultado de uma operação com base nos tipos de dados dos operandos. Em alguns casos, isso pode ser um tipo de dados com um intervalo maior do que o operando.  
  
## <a name="data-type-ranges"></a>Intervalos de tipos de dados  
 Os intervalos de tipos de dados relevantes, na ordem do menor ao maior, são da seguinte maneira:  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dois valores possíveis  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 possíveis valores integrais  
  
-   [Curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65,536 (6.5... E + 4) valores integrais possíveis  
  
-   [Inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4.294.967.296 (4.2... E + 9) valores integrais possíveis  
  
-   [Longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18.446.744.073.709.551.615 (1.8... E + 19) valores integrais possíveis  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1.5... E + 29 valores integrais possíveis, máximo intervalo 7.9... E + 28 (valor absoluto)  
  
-   [Único](../../../visual-basic/language-reference/data-types/single-data-type.md) — máximo intervalo 3.4... E + 38 (valor absoluto)  
  
-   [Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) — máximo intervalo 1.7... E + 308 (valor absoluto)  
  
 Para obter mais informações sobre tipos de dados do Visual Basic, consulte [tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Se um operando é avaliado como [nada](../../../visual-basic/language-reference/nothing.md), os operadores aritméticos do Visual Basic tratá-lo como zero.  
  
## <a name="decimal-arithmetic"></a>Aritmética decimal  
 Observe que o [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) é do tipo de dados nem ponto flutuante nem inteiro.  
  
 Se o operando de um `+`, `–`, `*`, `/`, ou `Mod` operação `Decimal` e o outro não `Single` ou `Double`, Visual Basic amplia o outro operando para `Decimal`. Ele realiza a operação em `Decimal`, e o tipo de dados do resultado é `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmética de ponto flutuante  
 Visual Basic executa a maioria das aritmética de ponto flutuante em [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md), que é o mais eficiente de dados de tipo para essas operações. No entanto, se um operando for [único](../../../visual-basic/language-reference/data-types/single-data-type.md) e o outro não `Double`, Visual Basic realiza a operação em `Single`. Ele amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
### <a name="-and--operators"></a>/ e ^ operadores  
 O `/` operador é definido somente para o [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [único](../../../visual-basic/language-reference/data-types/single-data-type.md), e [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) tipos de dados. Visual Basic amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
 A tabela a seguir mostra o resultado de tipos de dados para o `/` operador. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados do operando, o tipo de dados do resultado é o mesmo, independentemente da ordem dos operandos.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Qualquer tipo de inteiro|  
|`Decimal`|Decimal|Simples|Duplo|Decimal|  
|`Single`|Simples|Simples|Duplo|Simples|  
|`Double`|Duplo|Duplo|Duplo|Duplo|  
|Qualquer tipo de inteiro|Decimal|Simples|Duplo|Duplo|  
  
 O `^` operador é definido somente para o `Double` tipo de dados. Visual Basic amplia cada operando conforme necessário para `Double` antes da operação e o resultado de tipo de dados é sempre `Double`.  
  
## <a name="integer-arithmetic"></a>Aritmética de inteiros  
 O tipo de dados de resultado de uma operação de inteiro depende dos tipos de dados dos operandos. Em geral, o Visual Basic usa as políticas a seguir para determinar o tipo de dados de resultado:  
  
-   Se ambos os operandos de um operador binário têm o mesmo tipo de dados, o resultado tem esse tipo de dados. Uma exceção é `Boolean`, que é forçado a `Short`.  
  
-   Se um operador sem sinal participar com um operando assinado, o resultado tem um tipo assinado pelo menos tão grande um intervalo de cada um dos operandos.  
  
-   Caso contrário, o resultado geralmente tem o maior dos dois tipos de dados do operando.  
  
 Observe que o tipo de dados de resultado não pode ser o mesmo que o tipo de dados do operando.  
  
> [!NOTE]
>  O tipo de dados de resultado não é sempre grande o suficiente para conter todos os possíveis valores resultantes da operação. Um <xref:System.OverflowException> exceção poderá ocorrer se o valor for muito grande para o tipo de dados de resultado.  
  
### <a name="unary--and--operators"></a>Unários + e – operadores  
 A tabela a seguir mostra o resultado de tipos de dados para os dois operadores unários, `+` e `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unário `+`|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|Unário `–`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\< e >> operadores  
 A tabela a seguir mostra o resultado de tipos de dados para os dois operadores bit shift, `<<` e `>>`. Visual Basic trata cada operador bit shift como um operador unário em seu operando da esquerda (o bit padrão a ser deslocado).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando esquerdo é `Decimal`, `Single`, `Double`, ou `String`, Visual Basic tenta convertê-lo para `Long` antes da operação e o resultado é do tipo de dados `Long`. O operando direito (o número de posições de bit para deslocar) deve ser `Integer` ou um tipo que amplia a `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binary +, -, * e Mod operadores  
 A tabela a seguir mostra o resultado de tipos de dados para o binário `+` e `–` operadores e o `*` e `Mod` operadores. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados do operando, o tipo de dados do resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>Operador \  
 A tabela a seguir mostra o resultado de tipos de dados para o `\` operador. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados do operando, o tipo de dados do resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se ambos os operandos do `\` operador é [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [único](../../../visual-basic/language-reference/data-types/single-data-type.md), ou [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic tenta convertê-lo para [longa](../../../visual-basic/language-reference/data-types/long-data-type.md)antes da operação e o resultado é do tipo de dados `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparações relacionais e bit a bit  
 O tipo de dados de resultado de uma operação relacional (`=`, `<>`, `<`, `>`, `<=`, `>=`) é sempre `Boolean` [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). O mesmo é válido para operações lógicas (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) em `Boolean` operandos.  
  
 O tipo de dados de resultado de uma operação lógica bit a bit depende dos tipos de dados dos operandos. Observe que `AndAlso` e `OrElse` são definidos somente para `Boolean`, e o Visual Basic converte cada operando conforme necessário para `Boolean` antes de executar a operação.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<= e > = operadores  
 Se ambos os operandos forem `Boolean`, Visual Basic considera `True` para ser menor que `False`. Se um tipo numérico é comparado com um `String`, Visual Basic tenta converter o `String` para `Double` antes da operação. Um `Char` ou `Date` operando pode ser comparado somente com outro operando do mesmo tipo de dados. O tipo de dados do resultado é sempre `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bit a bit operador Not  
 A tabela a seguir mostra o resultado de tipos de dados para o bit a bit `Not` operador.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando for `Decimal`, `Single`, `Double`, ou `String`, Visual Basic tenta convertê-lo para `Long` antes da operação e o resultado é do tipo de dados `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bit a bit e, ou e operadores Xor  
 A tabela a seguir mostra o resultado de tipos de dados para o bit a bit `And`, `Or`, e `Xor` operadores. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados do operando, o tipo de dados do resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se for um operando `Decimal`, `Single`, `Double`, ou `String`, Visual Basic tenta convertê-lo para `Long` antes da operação e os dados de resultado a tipo é o mesmo que o operando já fosse `Long`.  
  
## <a name="miscellaneous-operators"></a>Operadores diversos  
 O `&` operador é definido somente para concatenação de `String` operandos. Visual Basic converte cada operando conforme necessário para `String` antes da operação e o resultado de tipo de dados é sempre `String`. Para fins do `&` operador, todas as conversões para `String` são considerados ser widening, mesmo se `Option Strict` é `On`.  
  
 O `Is` e `IsNot` operadores exigem ambos os operandos de um tipo de referência. O `TypeOf`... `Is` expressão requer que o primeiro operando de um tipo de referência e o segundo operando para o nome de um tipo de dados. Em todos esses casos os dados de resultado é tipo `Boolean`.  
  
 O `Like` operador é definido somente para correspondência de padrões de `String` operandos. Visual Basic tenta converter cada operando conforme necessário para `String` antes da operação. O tipo de dados do resultado é sempre `Boolean`.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operadores](../../../visual-basic/language-reference/operators/index.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
