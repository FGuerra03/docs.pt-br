---
title: Como imprimir a área cliente de um formulário (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>Como imprimir a área cliente de um formulário (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument> componente. O procedimento a seguir mostra como imprimir apenas a área cliente de um formulário, sem a barra de título, bordas e barras de rolagem.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-client-area-of-a-form"></a>Para imprimir a área cliente de um formulário  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  Em alguns sistemas operacionais, texto ou gráfico desenhado pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente. Nesse caso, use o método de impressão compatível: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Como imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
