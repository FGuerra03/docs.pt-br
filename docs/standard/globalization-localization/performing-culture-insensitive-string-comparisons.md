---
title: "Executando comparações de cadeias de caracteres que não levam em conta a cultura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa689a685a58868ccd34b8bcbc4a779b9f826473
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Executando comparações de cadeias de caracteres que não levam em conta a cultura
Por padrão, o método <xref:System.String.Compare%2A?displayProperty=nameWithType> executa comparações sensíveis à cultura e com diferenciação de maiúsculas e minúsculas. Esse método também inclui várias sobrecargas que fornecem um parâmetro `culture` que permite especificar a cultura a ser usada e um parâmetro `comparisonType` que permite especificar as regras de comparação que serão usadas. Chamar esses métodos em vez da sobrecarga padrão remove qualquer ambiguidade sobre as regras usadas em uma chamada de método específico e a torna claro se uma comparação é sensível à cultura ou não.  
  
> [!NOTE]
>  Ambas as sobrecargas do método <xref:System.String.CompareTo%2A?displayProperty=nameWithType> executam comparações sensíveis à cultura e comparações com diferenciação de maiúsculas e minúsculas. você não pode usar esse método para executar comparações insensíveis à cultura. Para fins de clareza de código, recomenda-se usar o método <xref:System.String.Compare%2A?displayProperty=nameWithType> em vez disso.  
  
 Para operações sensíveis à cultura, especifique o valor da enumeração <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> ou <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> como o parâmetro de `comparisonType`. Se você desejar executar uma comparação sensível à cultura usando uma cultura específica diferente da cultura atual, especifique o objeto <xref:System.Globalization.CultureInfo> que representa a cultura como o parâmetro `culture`.  
  
 As comparações de cadeias de caracteres insensíveis à cultura suportadas pelo método <xref:System.String.Compare%2A?displayProperty=nameWithType> são linguísticas (com base nas convenções de classificação de cultura invariável) ou não linguísticas (com base no valor ordinal dos caracteres na cadeia de caracteres). A maioria das comparações de cadeias de caracteres insensíveis cultura são não linguísticas. Para essas comparações, especifique o valor da enumeração <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> como o parâmetro de `comparisonType`. Por exemplo, se uma decisão de segurança (como uma comparação de nome de usuário ou senha) baseia-se no resultado de uma comparação de cadeia de caracteres, a operação deve ser insensível à cultura e não linguística para garantir que o resultado não seja afetado pelas convenções de uma cultura ou de um idioma específico.  
  
 Use a comparação de cadeia de caracteres linguística insensível à cultura se não desejar tratar cadeias de caracteres linguisticamente relevantes de várias culturas de uma maneira consistente. Por exemplo, se o seu aplicativo exibe palavras que usam vários conjuntos de caracteres em uma caixa de listagem, talvez você queira exibir as palavras na mesma ordem, independentemente da cultura atual. Para comparações linguísticas insensíveis à cultura, o .NET Framework define uma cultura invariável baseada nas convenções linguísticas do inglês. Para executar uma comparação linguística insensível à cultura, especifique <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ou <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> como o parâmetro de `comparisonType`.  
  
 O exemplo a seguir executa duas comparações de cadeias de caracteres não linguísticas insensíveis à cultura. A primeira diferencia maiúsculas de minúsculas, mas a segunda não.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.Compare%2A?displayProperty=nameWithType>  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 [Melhores práticas para o uso de cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md)
