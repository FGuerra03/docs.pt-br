---
title: Modo virtual no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06c5bb1d4a36d51bb07d59b48c730f722af23f8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Modo virtual no controle DataGridView dos Windows Forms
Com o modo virtual, você pode gerenciar a interação entre o <xref:System.Windows.Forms.DataGridView> controle e um cache de dados personalizados. Para implementar o modo virtual, defina o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade `true` e lidar com um ou mais dos eventos descritos neste tópico. Você normalmente manipulará pelo menos o evento `CellValueNeeded`, que permite os valores de consulta do controle no cache de dados.  
  
## <a name="bound-mode-and-virtual-mode"></a>Modo associado e modo virtual  
 O modo virtual é necessário somente quando você precisar suplementar ou substituir o modo associado. No modo associado, você deve definir o <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade e o controle automaticamente carrega os dados de origem especificada e envia o usuário altera para ele. Você pode controlar quais colunas associadas são exibidas e a fonte de dados que geralmente lida com operações como classificação.  
  
## <a name="supplementing-bound-mode"></a>Complementando o modo associado  
 Você pode complementar o modo associado exibindo colunas não associadas junto com as colunas associadas. Isso, às vezes, é chamado de "modo misto" e é útil para exibir coisas como controles de interface do usuário ou valores calculados.  
  
 Como as colunas não associadas estão fora da fonte de dados, elas são ignoradas por operações de classificação da fonte de dados. Portanto, quando você ativar a classificação no modo misto, você deve gerenciar os dados não associados em um cache local e implementar o modo virtual para permitir que o <xref:System.Windows.Forms.DataGridView> controle interagir com ele.  
  
 Para obter mais informações sobre como usar o modo virtual para manter os valores em colunas desassociadas, consulte os exemplos de <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> propriedade e <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> tópicos de referência de classe.  
  
## <a name="replacing-bound-mode"></a>Substituindo o modo associado  
 Se o modo associado não atender às suas necessidades de desempenho, você poderá gerenciar todos os seus dados em um cache personalizado por meio de manipuladores de eventos de modo virtual. Por exemplo, você pode usar o modo virtual para implementar um mecanismo de carregamento de dados Just-In-Time que recupera apenas os dados necessários de um banco de dados para desempenho ideal. Esse cenário é particularmente útil ao trabalhar com grandes quantidades de dados em uma conexão de rede lenta ou com computadores cliente que têm uma quantidade limitada de RAM ou espaço de armazenamento.  
  
 Para obter mais informações sobre como usar o modo virtual em um cenário Just-In-Time, consulte [Implementando o modo virtual com o carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Eventos de modo virtual  
 Se seus dados são somente leitura, o evento `CellValueNeeded` pode ser o único com o qual você precisará lidar. Eventos adicionais de modo virtual permitem que você habilite uma funcionalidade específica como edições do usuário, adição de linha e exclusão e transações de nível de linha.  
  
 Alguns padrão <xref:System.Windows.Forms.DataGridView> eventos (como eventos que ocorrem quando os usuários a adicionar ou excluem linhas ou valores de célula quando são editados, analisados, validados ou formatados) são úteis no modo virtual. Você também pode manipular eventos que lhe permitam manter valores que geralmente não são armazenados em uma fonte de dados associada, como o texto de dica de ferramenta da célula, texto de erro de linha e célula, célula e dados de menu de atalho da linha e dados de altura de linha.  
  
 Para mais informações sobre como implementar o modo virtual para gerenciar os dados de leitura/gravação com um escopo de confirmação de nível de linha, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Para obter um exemplo que implementa o modo virtual com um escopo de confirmação de nível de célula, consulte o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> tópico de referência de propriedade.  
  
 Os seguintes eventos ocorrem somente quando o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> está definida como `true`.  
  
|evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Usado pelo controle para recuperar um valor de célula do cache de dados para exibição. Esse evento ocorre somente para células em colunas não associadas.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Usado pelo controle para confirmar a entrada do usuário de uma célula para o cache de dados. Esse evento ocorre somente para células em colunas não associadas.<br /><br /> Chamar o <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> método ao alterar um valor armazenado em cache fora de um <xref:System.Windows.Forms.DataGridView.CellValuePushed> manipulador de eventos para garantir que o valor atual é exibido no controle e aplicar qualquer modos de dimensionamento automático atualmente em vigor.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Usado pelo controle para indicar a necessidade de uma nova linha no cache de dados.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Usado pelo controle para determinar se uma linha tem alterações não confirmadas.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Usado pelo controle para indicar que uma linha deve ser revertida para seus valores armazenados em cache.|  
  
 Os seguintes eventos são úteis no modo virtual, mas pode ser usados independentemente do <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> configuração de propriedade.  
  
|Eventos|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Usado pelo controle para indicar quando as linhas são excluídas ou adicionadas, permitindo a atualização do cache de dados adequadamente.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Usado pelo controle para formatar valores de célula para exibição e para analisar e validar a entrada do usuário.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Usado pelo controle para recuperar o texto de dica de ferramenta da célula quando o <xref:System.Windows.Forms.DataGridView.DataSource%2A> está definida ou o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é de propriedade `true`.<br /><br /> Dicas de ferramenta da célula são exibidas somente quando o <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> é o valor da propriedade `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Usado pelo controle para recuperar o texto da célula ou linha de erro quando o <xref:System.Windows.Forms.DataGridView.DataSource%2A> está definida ou o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é de propriedade `true`.<br /><br /> Chamar o <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> método ou o <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> método quando você alterar o texto de erro de célula ou linha para garantir que o valor atual é exibido no controle.<br /><br /> Célula e linha glifos de erro são exibidos quando o <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> e <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> valores de propriedade são `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Usado pelo controle para recuperar uma célula ou linha <xref:System.Windows.Forms.ContextMenuStrip> quando o controle <xref:System.Windows.Forms.DataGridView.DataSource%2A> está definida ou o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é de propriedade `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Usado pelo controle para recuperar ou armazenar informações de altura de linha no cache de dados. Chamar o <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> método ao alterar as informações de altura de linha em cache fora de um <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> manipulador de eventos para garantir que o valor atual é usado na exibição do controle.|  
  
## <a name="best-practices-in-virtual-mode"></a>Melhores práticas para o modo virtual  
 Se você estiver implementando o modo virtual para trabalhar com eficiência com grandes quantidades de dados, você também deseja garantir que você está trabalhando com eficiência com a <xref:System.Windows.Forms.DataGridView> próprio controle. Para mais informações sobre o uso eficiente dos estilos de célula, dimensionamento automático, seleções e compartilhamento de linhas, consulte [Melhores práticas para dimensionamento do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Ajuste de desempenho no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
