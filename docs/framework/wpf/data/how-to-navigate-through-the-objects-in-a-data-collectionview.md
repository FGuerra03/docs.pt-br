---
title: Como navegar pelos objetos em um CollectionView de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 215e3583d50567a2bfec8226e006bc7398628299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Como navegar pelos objetos em um CollectionView de dados
As exibições permitem que a mesma coleção de dados seja visualizada de diferentes maneiras, dependendo da classificação, filtragem ou agrupamento. Os modos de exibição também fornecem um conceito de ponteiro de registro atual e permitem a movimentação do ponteiro. Este exemplo mostra como obter o objeto atual, bem como navegar através de objetos em uma coleção de dados usando a funcionalidade fornecida no <xref:System.Windows.Data.CollectionView> classe.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `myCollectionView` é um <xref:System.Windows.Data.CollectionView> objeto que é um modo de exibição em uma coleção associada.  
  
 No exemplo a seguir, o `OnButton` é um manipulador de eventos para os botões `Previous` e `Next` em um aplicativo, que são botões que permitem que o usuário navegue pela coleção de dados. Observe que o <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> e <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> propriedades de relatório se o ponteiro de registro atual se o início e fim da lista respectivamente assim que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> e <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> pode ser chamado como adequadamente.  
  
 O <xref:System.Windows.Data.CollectionView.CurrentItem%2A> propriedade do modo de exibição será convertida como um `Order` para retornar o item do pedido atual na coleção.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Classificar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Filtrar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Classificar e agrupar dados usando uma exibição em XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
