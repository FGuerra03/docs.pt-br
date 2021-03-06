---
title: "Visão geral do controle TrackBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>Visão geral do controle TrackBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> controle (também chamado de controle "deslizante") é usado para navegar por uma grande quantidade de informações ou para ajustar visualmente uma configuração numérica. O <xref:System.Windows.Forms.TrackBar> controle tem duas partes: o thumb, também conhecido como um controle deslizante e as marcas de escala. O elevador é parte que pode ser ajustada. Sua posição corresponde do <xref:System.Windows.Forms.TrackBar.Value%2A> propriedade. As marcas de escala são indicadores visuais espaçados em intervalos regulares. A trackbar se move em incrementos especificados e pode ser alinhada horizontalmente ou verticalmente. Por exemplo, é possível usar a trackbar para controlar a taxa de intermitência do cursor ou a velocidade do mouse em um sistema.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Propriedades de chave do <xref:System.Windows.Forms.TrackBar> controle são <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, e <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>é o espaçamento de tiques. <xref:System.Windows.Forms.TrackBar.Minimum%2A>e <xref:System.Windows.Forms.TrackBar.Maximum%2A> são os valores menores e maiores que podem ser representados na barra de controle.  
  
 Duas outras propriedades importantes forem <xref:System.Windows.Forms.TrackBar.SmallChange%2A> e <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. O valor de <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propriedade é o número de posições de controle deslizante se move em resposta a ter a chave esquerda ou para a direita pressionada. O valor de <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propriedade é o número de posições que o controle deslizante se move em resposta a ter a tecla PAGE UP ou PAGE DOWN pressionada ou em resposta a mouse clica na barra de controle em ambos os lados do controle deslizante.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TrackBar>  
 [Controle TrackBar](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
