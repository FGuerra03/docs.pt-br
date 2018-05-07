---
title: Usando expressões regulares com o controle MaskedTextBox no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72542c05123ef62a8f95afbe1bb19cb823d1f21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Usando expressões regulares com o controle MaskedTextBox no Visual Basic
Este exemplo demonstra como converter expressões regulares simples para trabalhar com o <xref:System.Windows.Forms.MaskedTextBox> controle.  
  
## <a name="description-of-the-masking-language"></a>Descrição da linguagem máscara  
 O padrão <xref:System.Windows.Forms.MaskedTextBox> linguagem máscara baseia usada pelo `Masked Edit` controle no Visual Basic 6.0 e deve ser familiar aos usuários migrando desta plataforma.  
  
 O <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade o <xref:System.Windows.Forms.MaskedTextBox> controle especifica qual máscara de entrada usar. A máscara deve ser uma cadeia de caracteres composta de um ou mais elementos de máscara da seguinte tabela.  
  
|Elemento de mascaramento|Descrição|Elemento de expressão regular|  
|---------------------|-----------------|--------------------------------|  
|0|Qualquer dígito único entre 0 e 9. Entrada obrigatória.|\d|  
|9|Dígito ou espaço. Entrada opcional.|\d?|  
|#|Dígito ou espaço. Entrada opcional. Se a posição é deixada em branco na máscara de, ele será renderizado como um espaço. Sinal de adição (+) e menos (-) são permitidos.|\d+-?|  
|L|Letra de ASCII. Entrada obrigatória.|[a-zA-Z]|  
|?|Letra de ASCII. Entrada opcional.|[a-zA-Z]?|  
|&|Caractere. Entrada obrigatória.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo]}|  
|C|Caractere. Entrada opcional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Alfanumérico. Entrada opcional.|\W|  
|.|Apropriado para decimal.|Não disponível.|  
|,|Cultura apropriado para milhares.|Não disponível.|  
|:|Separador de tempo apropriado.|Não disponível.|  
|/|Separador de data apropriado.|Não disponível.|  
|$|Símbolo de moeda apropriado.|Não disponível.|  
|\<|Converte todos os caracteres em minúsculas.|Não disponível.|  
|>|Converte todos os caracteres em maiusculas.|Não disponível.|  
|&#124;|Desfaz um turno anterior para cima ou baixo.|Não disponível.|  
|\|Escape de um caractere de máscara, transformando-a em um literal. "\\\\" é a sequência de escape para uma barra invertida.|\|  
|Todos os outros caracteres.|Literais. Todos os elementos não máscara aparecerão como eles mesmos dentro <xref:System.Windows.Forms.MaskedTextBox>.|Todos os outros caracteres.|  
  
 Decimal (.), milhares (,), tempo (:), data (/) e padrão de símbolos de moeda ($) para exibir os símbolos, conforme definido pela cultura do aplicativo. Você pode forçá-los para exibir os símbolos de outra localização usando a <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> propriedade.  
  
## <a name="regular-expressions-and-masks"></a>Expressões regulares e máscaras  
 Embora você possa usar expressões regulares e máscaras para validar a entrada do usuário, elas não são completamente equivalentes. Expressões regulares podem expressar padrões mais complexos que máscaras, mas máscaras podem expressar as mesmas informações de forma mais sucinta e em um formato localmente relevante.  
  
 A tabela a seguir compara quatro expressões regulares e a máscara equivalente para cada um.  
  
|Expressão regular|Máscara|Observações|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O `/` caractere da máscara é um separador de data lógica, e ela será exibida para o usuário como o separador de data apropriado para a cultura atual do aplicativo.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data (dia, abreviação de mês e ano) no formato de Estados Unidos em que a abreviação de mês de três letras é exibida com uma letra maiuscula inicial seguida de duas letras minúsculas.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Número de telefone dos Estados Unidos, código de área opcional. Se o usuário não deseja inserir os caracteres opcionais, ela pode inserir espaços ou colocar o ponteiro do mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor de moeda no intervalo de 0 a 999999. Caracteres decimais, moeda e milésimos serão substituídos em tempo de execução por seus equivalentes específicos de cultura.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [Controle MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
