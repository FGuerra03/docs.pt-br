---
title: Criar um aplicativo do WPF no Visual Studio
ms.custom: 04/12/2018
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edc7a22a7b108731e08c5d67ef8b8a52e9959ddc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF

Este artigo mostra como desenvolver um aplicativo simples do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos do WPF: marcação Extensible Application Markup idioma (XAML), por trás do código, definições de aplicativo controles de layout, associação de dados e estilos.

Este passo a passo inclui as seguintes etapas:

- Use XAML para criar a aparência da interface do usuário do aplicativo (IU).

- Escreva código para criar o comportamento do aplicativo.

- Crie uma definição de aplicativo para gerenciar o aplicativo.

- Adicionar controles e crie o layout para compor o interface do usuário do aplicativo.

- Crie estilos de uma aparência consistente em toda a interface de usuário do aplicativo.

- Associe a interface do usuário aos dados ao popular a interface do usuário de dados e manter os dados e a interface do usuário sincronizado.

No final do passo a passo, você vai ter criado um aplicativo do Windows que permite aos usuários exibir relatórios de despesa para pessoas selecionadas autônomo. O aplicativo é composto de várias páginas WPF que são hospedadas em uma janela com estilo de navegador.

> [!TIP]
> O código de exemplo que é usado para este passo a passo de compilação está disponível para o Visual Basic e c# em [Introdução ao criar aplicativos do WPF](http://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2012 ou posterior

Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instale o Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Criar o projeto de aplicativo

A primeira etapa é criar a infraestrutura de aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.

1. Criar um novo projeto de aplicativo do WPF no Visual Basic ou Visual c# denominado **ExpenseIt**:

   1. Abra o Visual Studio e selecione **arquivo** > **novo** > **projeto**.

      O **novo projeto** caixa de diálogo é aberta.

   2. Sob o **instalado** categoria, expanda o **Visual C#** ou **Visual Basic** nó e selecione **área de trabalho clássica do Windows**.

   3. Selecione o **aplicativo WPF (.NET Framework)** modelo. Digite o nome **ExpenseIt** e, em seguida, selecione **Okey**.

      ![Caixa de diálogo Nova projeto com o aplicativo do WPF selecionado](media/new-project-dialog.png)

      O Visual Studio cria o projeto e abre o designer para a janela de aplicativo padrão chamado **MainWindow**.

   > [!NOTE]
   > Este passo a passo usa o <xref:System.Windows.Controls.DataGrid> controle que está disponível no .NET Framework 4 e posterior. Ser-se de que seu projeto se destina ao .NET Framework 4 ou posterior. Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Abra *Application* (Visual Basic) ou *App* (c#).

    Esse arquivo XAML define um aplicativo do WPF e quaisquer recursos do aplicativo. Você também usar esse arquivo para especificar a interface do usuário que mostra automaticamente quando o aplicativo é iniciado; Nesse caso, *MainWindow*.

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Ou assim no C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Abra *MainWindow*.

    Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado nas páginas. O <xref:System.Windows.Window> classe define as propriedades de uma janela, como título, tamanho ou no ícone e trata os eventos, como fechar ou ocultar.

4. Alterar o <xref:System.Windows.Window> elemento para uma <xref:System.Windows.Navigation.NavigationWindow>, como mostra o XAML a seguir:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Este aplicativo navega para um conteúdo diferente dependendo da entrada do usuário. É por isso que o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> herda todas as propriedades de <xref:System.Windows.Window>. O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância de <xref:System.Windows.Navigation.NavigationWindow> classe. Para obter mais informações, consulte [visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Alterar as propriedades a seguir sobre o <xref:System.Windows.Navigation.NavigationWindow> elemento:

    - Definir o <xref:System.Windows.Window.Title%2A> propriedade como "ExpenseIt".

    - Definir o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.

    - Definir o <xref:System.Windows.FrameworkElement.Height%2A> propriedade 350 pixels.

    - Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Ou assim no C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Abra *MainWindow.xaml.vb* ou *MainWindow.xaml.cs*.

    Esse arquivo é um arquivo de code-behind que contém o código para manipular os eventos declarados em *MainWindow*. Esse arquivo contém uma classe parcial para a janela definida no XAML.

7. Se você estiver usando c#, altere o `MainWindow` classe para derivar de <xref:System.Windows.Navigation.NavigationWindow>. (No Visual Basic, isso ocorre automaticamente quando você altera a janela em XAML.)

   Seu código deve ter esta aparência:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Você pode alternar a linguagem de código do código de exemplo entre c# e Visual Basic no **idioma** suspensa no canto superior direito deste artigo.

## <a name="add-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

1. Adicione uma nova página do WPF para o projeto e nomeie- *ExpenseItHome.xaml*:

   1. Em **Solution Explorer**, com o botão direito no **ExpenseIt** nó do projeto e escolha **adicionar** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado. Digite o nome **ExpenseItHome**e, em seguida, selecione **adicionar**.

    Esta página é a primeira página exibida quando o aplicativo é iniciado. Ele mostrará uma lista de pessoas a serem selecionadas, para mostrar um relatório de despesas para.

2. Abra *ExpenseItHome.xaml*.

3. Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - Home".

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Abra *MainWindow*.

5. Definir o <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade o <xref:System.Windows.Navigation.NavigationWindow> para "ExpenseItHome.xaml".

    Isso define *ExpenseItHome.xaml* como a primeira página aberta quando o aplicativo é iniciado. O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Você também pode definir o **fonte** propriedade o **diversos** categoria do **propriedades** janela.
   >
   > ![Propriedade de origem na janela Propriedades](media/properties-source.png)

6. Adicionar outra página WPF novo ao projeto e nomeie- *ExpenseReportPage*::

   1. Em **Solution Explorer**, com o botão direito no **ExpenseIt** nó do projeto e escolha **adicionar** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado. Digite o nome **ExpenseReportPage**e, em seguida, selecione **adicionar**.

    Essa página mostrará o relatório de despesas para a pessoa que está selecionada no **ExpenseItHome** página.

7. Abra *ExpenseReportPage.xaml*.

8. Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - despesas de exibição".

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Abra *ExpenseItHome.xaml.vb* e *ExpenseReportPage.xaml.vb*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.

    Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente um *por trás do código* arquivo. Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.

    Seu código deverá parecer como este para **ExpenseItHome**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    E como este para **ExpenseReport**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Adicione uma imagem chamada *watermark* ao projeto. Você pode criar sua própria imagem, copie o arquivo de código de exemplo ou obtê-lo [aqui](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Clique com botão direito no nó do projeto e selecione **adicionar** > **Item existente**, ou pressione **Shift**+**Alt** + **Um**.

   2. No **Add Existing Item** caixa de diálogo, navegue até o arquivo de imagem que você deseja usar e, em seguida, selecione **adicionar**.

## <a name="build-and-run-the-application"></a>Compilar e executar o aplicativo

1. Para compilar e executar o aplicativo, pressione **F5** ou selecione **iniciar depuração** do **depurar** menu.

    A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões:

    ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Feche o aplicativo para retornar ao Visual Studio.

## <a name="create-the-layout"></a>Criar o layout

Layout oferece uma maneira ordenada para colocar elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionado. Normalmente, você cria um layout com um dos seguintes controles de layout:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Cada um desses controles de layout dá suporte a um tipo especial de layout para seus elementos filhos. As páginas ExpenseIt podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos. Consequentemente, o <xref:System.Windows.Controls.Grid> é o elemento de layout ideal para o aplicativo.

> [!TIP]
> Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md). Para obter mais informações sobre o layout, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md).

Na seção, você criar uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de coluna e linha para o <xref:System.Windows.Controls.Grid> na *ExpenseItHome.xaml*.

1. Abra *ExpenseItHome.xaml*.

2. Definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade o <xref:System.Windows.Controls.Grid> elemento para "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Você também pode definir o **margem** valores no **propriedades** janela, sob o **Layout** categoria:
   >
   > ![Valores de margem na janela Propriedades](media/properties-margin.png)

3. Adicionar o XAML a seguir entre a <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, que significa que as linhas são dimensionadas de base no conteúdo de linhas. O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível. Por exemplo, se duas linhas tiverem uma <xref:System.Windows.Controls.RowDefinition.Height%2A> de "*", cada um deles tem uma altura de metade do espaço disponível.

    Seu <xref:System.Windows.Controls.Grid> agora deve se parecer com o XAML a seguir:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Adicionar controles

Nesta seção, você atualizará a home page da interface do usuário para mostrar uma lista de pessoas que um usuário pode selecionar para exibir o relatório de despesas para. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../../../../docs/framework/wpf/controls/index.md).

Para criar essa interface do usuário, você adicionará os seguintes elementos para *ExpenseItHome.xaml*:

- <xref:System.Windows.Controls.ListBox> (para obter a lista de pessoas).
- <xref:System.Windows.Controls.Label> (para o cabeçalho de lista).
- <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).

Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [visão geral de propriedades anexado](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Abra *ExpenseItHome.xaml*.

2. Adicionar o XAML a seguir em algum ponto entre o <xref:System.Windows.Controls.Grid> marcas:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Você também pode criar os controles arrastando-os do **caixa de ferramentas** janela para a janela de design e, em seguida, definindo suas propriedades no **propriedades** janela.

3. Crie e execute o aplicativo.

A ilustração a seguir mostra os controles que você acabou de criar:

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Adicionar um título e uma imagem

Nesta seção, você atualizará a home page da interface do usuário com uma imagem e título da página.

1. Abra *ExpenseItHome.xaml*.

2. Adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Mover os controles para a segunda coluna, definindo o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade para 1 em cada um dos três controles (borda, caixa de listagem e botão).

5. Mover cada controle para baixo de uma linha, aumentando seu <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valor por 1.

   O XAML para os três controles agora esta aparência:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Definir o <xref:System.Windows.Controls.Panel.Background%2A> do <xref:System.Windows.Controls.Grid> para ser o *watermark* arquivo de imagem, adicionando o XAML a seguir em algum ponto entre o `<Grid>` e `<\/Grid>` marcas:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Antes do <xref:System.Windows.Controls.Border> elemento, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas". Este é o título da página.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Crie e execute o aplicativo.

A ilustração a seguir mostra os resultados de que você acabou de adicionar:

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Adicione código para manipular eventos

1. Abra *ExpenseItHome.xaml*.

2. Adicionar um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento. Para obter mais informações, consulte [como: criar um manipulador de eventos simples](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Abra *ExpenseItHome.xaml.vb* ou *ExpenseItHome.xaml.cs*.

4. Adicione o seguinte código para o `ExpenseItHome` classe para adicionar um botão de manipulador de evento. O manipulador de eventos abre o **ExpenseReportPage** página.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Criar a interface do usuário para ExpenseReportPage

*ExpenseReportPage* exibe o relatório de despesas para a pessoa que está selecionada no **ExpenseItHome** página. Nesta seção, você vai controles e criar a interface do usuário para **ExpenseReportPage**. Você também adicionará o plano de fundo e cores de preenchimento para os vários elementos de interface do usuário.

1. Abra *ExpenseReportPage.xaml*.

2. Adicionar o XAML a seguir entre a <xref:System.Windows.Controls.Grid> marcas:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Essa interface do usuário é semelhante a *ExpenseItHome.xaml*, exceto os dados de relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.

3. Crie e execute o aplicativo.

    > [!NOTE]
    > Se você receber um erro que o <xref:System.Windows.Controls.DataGrid> não foi encontrado ou não existir, certifique-se de que seu projeto direcionado ao .NET Framework 4 ou posterior. Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Selecione o **exibição** botão.

    A página de relatório de despesas é exibida. Além disso, observe que o botão de navegação está habilitado.

A ilustração a seguir mostra os elementos de interface do usuário adicionados ao *ExpenseReportPage*.

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Controles de estilo

A aparência de vários elementos geralmente é o mesmo para todos os elementos do mesmo tipo em uma interface do usuário. Interface do usuário usa [estilos](../../../../docs/framework/wpf/controls/styling-and-templating.md) para fazer aparências reutilizáveis entre vários elementos. A capacidade de reutilização dos estilos ajuda a simplificar o gerenciamento e criação de XAML. Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.

1. Abra *Application* ou *App*.

2. Adicionar o XAML a seguir entre a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Esse XAML adiciona os seguintes estilos:

    - `headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>.

    - `labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>.

    - `columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista.

    - `listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Para formatar o <xref:System.Windows.Controls.Button> em ExpenseItHome.xaml.

    Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento property. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para obter um exemplo de uso de recursos em um aplicativo do .NET Framework, consulte [usar recursos de aplicativo](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Abra *ExpenseItHome.xaml*.

4. Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.

5. Abra *ExpenseReportPage.xaml*.

6. Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Isso adiciona estilos aos elementos <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border>.

## <a name="bind-data-to-a-control"></a>Associar dados a um controle

Nesta seção, você criará os dados XML que estão associados a vários controles.

1. Abra *ExpenseItHome.xaml*.

2. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicionar o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados para cada pessoa:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos. Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos.

3. Dentro de `<Grid.Resources>` elemento, adicione o seguinte <xref:System.Windows.DataTemplate>, que define como exibir os dados a <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Substituir o <xref:System.Windows.Controls.ListBox> com o XAML a seguir:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Este XAML associa o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Conecte-se a dados a controles

Em seguida, você adicionará código para recuperar o nome selecionado no **ExpenseItHome** página e passá-lo para o construtor de **ExpenseReportPage**. **ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos em *ExpenseReportPage* associar.

1. Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Abra *ExpenseItHome.xaml.vb* ou *ExpenseItHome.xaml.cs*.

4. Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passar os dados de relatório de despesas da pessoa que está selecionado.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dados de estilo com modelos de dados

Nesta seção, você atualizará a interface do usuário para cada item nas listas de associação de dados usando modelos de dados.

1. Abra *ExpenseReportPage.xaml*.

2. Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> a propriedade de fonte de elementos para os dados apropriados. Para obter mais informações sobre associação de dados, consulte [visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Aplicar os modelos para o <xref:System.Windows.Controls.DataGrid> colunas que exibem a despesa de dados de relatório.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Crie e execute o aplicativo.

6. Selecione uma pessoa e, em seguida, selecione o **exibição** botão.

A ilustração a seguir mostra ambas as páginas do aplicativo ExpenseIt com controles, layout, estilos, associação de dados e modelos de dados aplicados:

![Capturas de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade. Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativo do .NET Framework, consulte os tópicos a seguir:
>
> - [Acessibilidade](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Segurança](../../../../docs/framework/wpf/security-wpf.md)
>
> - [Localização e globalização de WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Desempenho do WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo, você aprendeu várias técnicas para a criação de uma interface do usuário usando o Windows Presentation Foundation (WPF). Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo do .NET Framework de associação de dados. Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:

- [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Visão geral XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Visão geral de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Layout](../../../../docs/framework/wpf/advanced/layout.md)

Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:

- [Desenvolvimento de aplicativos](../../../../docs/framework/wpf/app-development/index.md)
- [Controles](../../../../docs/framework/wpf/controls/index.md)
- [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Consulte também

- [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Criar um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Os estilos e modelos](../../../../docs/framework/wpf/controls/styles-and-templates.md)
