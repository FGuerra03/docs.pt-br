---
title: "Como pintar uma área com uma cor sólida"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a5fe948c3cc6088f238f1f8f53c26c5f1fa5b2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Como pintar uma área com uma cor sólida
Para pintar uma área com uma cor sólida, você pode usar um pincel predefinido do sistema, como <xref:System.Windows.Media.Brushes.Red%2A> ou <xref:System.Windows.Media.Brushes.Blue%2A>, ou você pode criar um novo <xref:System.Windows.Media.SolidColorBrush> e descrever seu <xref:System.Windows.Media.SolidColorBrush.Color%2A> usando valores alfa, vermelhos, verdes e azuis. Em XAML, você também pode pintar uma área com uma cor sólida usando notação hexadecimal.  
  
 Os exemplos a seguir usam cada uma dessas técnicas para pintar uma <xref:System.Windows.Shapes.Rectangle> azul.  
  
## <a name="example"></a>Exemplo  
 **Usando um pincel predefinido**  
  
 No exemplo a seguir usa o pincel predefinido <xref:System.Windows.Media.Brushes.Blue%2A> para desenhar um retângulo azul.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Usando notação Hexadecimal**  
  
 O exemplo a seguir, usa a notação hexadecimal de 8 dígitos para pintar um retângulo de azul.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Usando valores ARGB**  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.SolidColorBrush> e descreve seu <xref:System.Windows.Media.SolidColorBrush.Color%2A> usando os valores ARGB para a cor azul.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Para outras maneiras de descrever cor, consulte o <xref:System.Windows.Media.Color> estrutura.  
  
 **Tópicos relacionados**  
  
 Para obter mais informações sobre <xref:System.Windows.Media.SolidColorBrush> e exemplos adicionais, consulte o [pintura com cores sólidas e visão geral de gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) visão geral.  
  
 Este exemplo de código é parte de um exemplo maior fornecido para a <xref:System.Windows.Media.SolidColorBrush> classe. Para obter o exemplo completo, consulte [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973) (Exemplo de pincéis).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Brushes>
