---
title: Como adicionar controles sem uma interface do usuário aos Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e900c1c34f69531a14cfa11803ef5a6afb4783c6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Como adicionar controles sem uma interface do usuário aos Windows Forms
Um controle (ou componente) não visual fornece funcionalidade ao seu aplicativo. Diferente de outros controles, os componentes não fornecem uma interface do usuário ao usuário e, portanto, não precisam ser exibido na superfície do Designer de Formulários do Windows. Quando um componente é adicionado a um formulário, o Designer de Formulários do Windows exibe uma bandeja redimensionável na parte inferior do formulário em que todos os componentes são exibidos. Quando um controle é adicionado à bandeja de componentes, você pode selecionar o componente e definir suas propriedades como faria com qualquer outro controle no formulário.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Adicionar um componente a um Windows Form  
  
1.  Abra o formulário. Para ver mais detalhes, consulte [Como exibir Windows Forms no Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Na **Caixa de ferramentas**, clique em um componente e arraste-o para o formulário.  
  
     O componente aparece na bandeja de componentes.  
  
 Além disso, os componentes podem ser adicionados a um formulário no tempo de execução. Esse é um cenário comum, especialmente porque os componentes não têm uma expressão visual, diferente de controles que têm uma interface do usuário. No exemplo a seguir, um <xref:System.Windows.Forms.Timer> componente é adicionado em tempo de execução. (Observe que o Visual Studio contém um número de timers diferentes; nesse caso, use um Windows Forms <xref:System.Windows.Forms.Timer> componente. Para obter mais informações sobre os temporizadores diferentes no Visual Studio, consulte [Introdução a Timers baseados em servidor](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Componentes geralmente têm propriedades específicas de controle que devem ser definidas para o componente funcionar com eficiência. No caso do <xref:System.Windows.Forms.Timer> abaixo do componente, definir o `Interval` propriedade. Verifique se as propriedades necessárias para o componente foram definidas ao adicioná-lo ao projeto.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Adicionar um componente a um Windows Form com programação  
  
1.  Criar uma instância do <xref:System.Windows.Forms.Timer> classe no código.  
  
2.  Defina a propriedade `Interval` para determinar o tempo entre os tiques do temporizador.  
  
3.  Configure as outras propriedades necessárias para seu componente.  
  
     O código a seguir mostra a criação de um <xref:System.Windows.Forms.Timer> com seus `Interval` conjunto de propriedades.  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Você poderia expor seu computador local a um risco de segurança por meio da rede referenciando um UserControl mal-intencionado. Isso seria um problemas apenas no caso de uma pessoa mal-intencionada criar um controle personalizado prejudicial e você adicioná-lo por engano ao seu projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Como adicionar controles do ActiveX ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Como copiar controles entre Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Colocando controles nos Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
