---
title: "Três categorias de serviços gráficos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 305ffae04b6f1ddb94081f8a6ee334f8195caba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="three-categories-of-graphics-services"></a>Três categorias de serviços gráficos
As ofertas de elementos gráficos no Windows Forms se enquadram nas três categorias amplas a seguir:  
  
-   Gráficos vetoriais bidimensionais (2D)  
  
-   Imagens  
  
-   Tipografia  
  
## <a name="2-d-vector-graphics"></a>Gráficos vetoriais 2D  
 Gráficos vetoriais bidimensionais são primitivos, como linhas, curvas e figuras. que são especificadas por conjuntos de pontos em um sistema de coordenadas. Por exemplo, uma linha reta é especificada por seus dois pontos de extremidade e um retângulo é especificado por um ponto que indica o local de seu canto superior esquerdo e um par de números fornecendo sua largura e altura. Um demarcador simples é especificado por uma matriz de pontos conectados por linhas retas. Uma spline de Bézier é uma curva sofisticada especificada por quatro pontos de controle.  
  
 O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece classes e estruturas que armazenam informações sobre os próprios primitivos, classes que armazenam informações sobre como os primitivos serão desenhados e classes que efetivamente executam o desenho. Por exemplo, o <xref:System.Drawing.Rectangle> estrutura armazena o local e o tamanho de um retângulo; o <xref:System.Drawing.Pen> classe armazena informações sobre a cor da linha, a largura da linha e estilo de linha; e o <xref:System.Drawing.Graphics> classe tem métodos para desenhar linhas, retângulos, caminhos, e outros valores. Há também várias <xref:System.Drawing.Brush> classes que armazenam informações sobre como fechado figuras e caminhos serão preenchidos com cores ou padrões.  
  
 Você pode gravar uma imagem de vetor, que é uma sequência de comandos gráficos, em um metarquivo. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fornece o <xref:System.Drawing.Imaging.Metafile> classe para registrar, exibir e salvar metarquivos. Com o <xref:System.Drawing.Imaging.MetafileHeader> e <xref:System.Drawing.Imaging.MetaHeader> classes, você pode inspecionar os dados armazenados em um cabeçalho de metarquivo.  
  
## <a name="imaging"></a>Imagens  
 Determinados tipos de imagens são difíceis ou impossíveis de exibir com as técnicas de gráficos vetoriais. Por exemplo, as imagens nos botões da barra de ferramentas e as imagens que aparecem como ícones são difíceis de especificar como conjuntos de linhas e curvas. Uma fotografia digital de alta resolução de um estádio lotado é ainda mais difícil criar com técnicas de vetor. Imagens desse tipo são armazenadas como bitmaps, que são matrizes de números que representam as cores de pontos individuais na tela. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fornece o <xref:System.Drawing.Bitmap> classe para exibir, manipular e salvando bitmaps.  
  
## <a name="typography"></a>Tipografia  
 Tipografia é a exibição do texto em uma variedade de fontes, tamanhos e estilos. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dá um extenso suporte para essa tarefa complexa. Um dos novos recursos do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é a suavização de subpixel, que proporciona ao texto renderizado em uma tela LCD uma aparência mais suave.  
  
 Além disso, o Windows Forms oferece a opção para desenhar texto com [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] recursos no seu <xref:System.Windows.Forms.TextRenderer> classe.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de elementos gráficos](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Sobre o Código Gerenciado no GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Usando Classes de Elementos Gráficos Gerenciadas](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
