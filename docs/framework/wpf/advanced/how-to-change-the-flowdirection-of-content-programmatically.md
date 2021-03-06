---
title: Como alterar o FlowDirection de conteúdo de forma programática
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88beba371a9dd8ea54dabe8f541b4a01773982cb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Como alterar o FlowDirection de conteúdo de forma programática
Este exemplo mostra como alterar programaticamente o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade de um <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Exemplo  
 Dois <xref:System.Windows.Controls.Button> elementos são criados, cada um representando um dos possíveis valores de <xref:System.Windows.FlowDirection>. Quando um botão é clicado, o valor da propriedade associada é aplicado ao conteúdo de um <xref:System.Windows.Controls.FlowDocumentReader> chamado `tf1`.  O valor da propriedade também é gravado em um <xref:System.Windows.Controls.TextBlock> chamado `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Exemplo  
 Os eventos associados com os cliques de botão definidos acima são tratados em um arquivo de code-behind c#.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
