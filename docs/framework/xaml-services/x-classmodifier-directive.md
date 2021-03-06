---
title: Diretiva x:ClassModifier
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab6036ecb37bb80588a59b581af0b88fc83230a4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="xclassmodifier-directive"></a>Diretiva x:ClassModifier
Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido. Especificamente, em vez de criar um parcial `class` que tem um `Public` (o padrão), do nível de acesso fornecido `x:Class` é criada com um `NotPublic` nível de acesso. Esse comportamento afeta o nível de acesso para a classe no assembly gerado.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*NotPublic*|A cadeia de caracteres exata para passar para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação por trás do código que você usa. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 [X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página. Para obter mais informações, consulte [ \[XAML MS\] seção 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Comentários  
 O valor de `x:ClassModifier` em serviços XAML do .NET Framework uso varia de acordo com a linguagem de programação. A cadeia de caracteres a ser usado depende de como cada linguagem implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e conversores de tipo que ele retorna para definir os significados de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se o idioma diferencia maiusculas de minúsculas.  
  
-   Para c#, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal`.  
  
-   Para o Microsoft Visual Basic .NET, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend`.  
  
-   Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nenhum destino existe que dão suporte a compilação XAML; portanto, o valor passado for especificado.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` em c#, `Public` no Visual Basic); no entanto, especificando <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> raramente é feito porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.  
  
 Outros valores com o código de usuário equivalente nível de acesso restrições, como `private` em c#, não são relevantes para `x:ClassModifier` porque não há suporte para referências de classe aninhada em XAML e, portanto, o <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tem o mesmo efeito.  
  
## <a name="security-notes"></a>Observações de segurança  
 O nível de acesso conforme declarado em `x:ClassModifier` ainda está sujeito a interpretação de determinadas estruturas e seus recursos. WPF inclui recursos para carregar e instanciar tipos onde `x:ClassModifier` é `internal`, se essa classe é referenciada em um recurso do WPF por meio de um referência URI de pacote. Como consequência neste caso e possivelmente outros como ele é implementado por outras estruturas, não confie exclusivamente em `x:ClassModifier` para bloquear todas as possíveis instanciação tentativas.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Class](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Code-behind e XAML no WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Diretiva x:FieldModifier](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [Segurança (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [Tipos migrados do WPF para System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
