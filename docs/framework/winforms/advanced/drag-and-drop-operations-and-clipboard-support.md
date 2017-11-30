---
title: "Operações de arrastar e soltar e suporte à área de transferência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722c37645d95009ce03bbbf813bc9f9fb2418e60
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a>Operações de arrastar e soltar e suporte à área de transferência
Você pode habilitar operações arrastar e soltar do usuário dentro de um aplicativo baseado em Windows manipulando uma série de eventos, particularmente o <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos.  
  
 Você também pode implementar o suporte ao usuário recortar/copiar/colar e a transferência de dados do usuário para a área de transferência em seus aplicativos baseados no Windows usando chamadas de método simples.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Instruções Passo a Passo: Executando uma Operação do Tipo "Arrastar e Soltar" nos Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 Explica como iniciar uma operação do tipo "arrastar e soltar".  
  
 [Como Executar Operações de do Tipo "Arrastar e Soltar" entre Aplicativos](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 Ilustra como realizar operações do tipo "arrastar e soltar" entre aplicativos.  
  
 [Como Adicionar Dados à Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 Descreve uma maneira de inserir via programação informações na área de transferência.  
  
 [Como Recuperar Dados da Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 Descreve como acessar os dados armazenados na área de transferência.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funcionalidade do tipo "arrastar e soltar" nos Windows Forms](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 Descreve os métodos, os eventos e as classes usados para implementar o comportamento do tipo "arrastar e soltar".  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 Descreve a complexidade do evento que pede permissão para continuar a operação de arrastar.  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 Descreve a complexidade do método essencial para começar a operação de arrastar.  
  
 <xref:System.Windows.Forms.Clipboard>  
 Veja também [Como enviar dados para o filho MDI ativo](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).