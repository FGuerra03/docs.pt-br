---
title: "Práticas recomendadas de Acessibilidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 61f9ca1e8a79942b04afd8628282ceeb1e1b4b51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="accessibility-best-practices"></a>Práticas recomendadas de Acessibilidade
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Implementar os seguintes práticas recomendadas em controles ou aplicativos aumentará sua acessibilidade para pessoas que usam [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] dispositivos. Muitas dessas práticas recomendadas focalizam em bom [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] design. Cada recomendação inclui informações de implementação [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controles ou aplicativos. Em muitos casos, o trabalho para atender a estas práticas recomendadas já está incluído no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Acesso programático  
 Acesso programático envolve garantir que todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos são rotulados, valores de propriedade são expostos e eventos apropriados são gerados. Padrão [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles, a maioria desse trabalho já é feito por meio de <xref:System.Windows.Automation.Peers.AutomationPeer>. Controles personalizados exigem trabalho adicional para garantir que o acesso programático é implementado corretamente.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Habilitar o acesso programático a todos os elementos de interface do usuário e texto  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]elementos devem habilitar o acesso programático. Se o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] é um padrão [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] de controle, o suporte para o acesso programático é incluído no controle. Se o controle for um controle personalizado – um controle que tem sido derivado de um controle comum ou um controle que tem sido derivado de Control – você deve verificar o <xref:System.Windows.Automation.Peers.AutomationPeer> implementação para as áreas que talvez precisem de modificação.  
  
 Seguir essa recomendação permite [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] fornecedores para identificar e manipular os elementos de seu produto [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Coloque nomes, títulos e descrições em objetos de interface do usuário, quadros e páginas  
 Tecnologias auxiliares, especialmente leitores de tela, usam o título para entender o local do quadro, objeto ou página no esquema de navegação. Portanto, o título deve ser muito descritivo. Por exemplo, um título de página da Web de "página da Microsoft" é inútil se o usuário tem navegado profundamente em alguma área específica. Um título descritivo é fundamental para os usuários cegos e dependem de leitores de tela. Da mesma forma, para [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controles, <xref:System.Windows.Automation.AutomationProperties.NameProperty> e <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> são importantes para [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] dispositivos.  
  
 Seguir essa recomendação permite [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s para identificar e manipular [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] em controles de exemplo e aplicativos.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Certifique-se de que eventos programados são disparados por todas as atividades de interface do usuário  
 Seguir essa recomendação permite [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s para escuta de alterações a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] e notificar o usuário sobre essas alterações.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Configurações do usuário  
 A prática recomendada nesta seção garante que os controles ou aplicativos não substituir as configurações do usuário.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Respeitar todas as configurações do sistema e não interferir com as funções de acessibilidade  
 Os usuários podem usar o painel de controle para definir alguns sinalizadores de sistema; outros sinalizadores podem ser definidos programaticamente. Essas configurações não devem ser alteradas por controles ou aplicativos. Além disso, os aplicativos devem oferecer suporte as configurações de acessibilidade do sistema operacional do host.  
  
 Seguir essa recomendação permite aos usuários definir configurações de acessibilidade e saber que essas configurações não serão alteradas por aplicativos.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Design visual de interface do usuário  
 Certifique-se de práticas recomendadas nesta seção controles ou aplicativos usem cores e imagens com eficiência e podem ser usados por [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Não Embutir Cores  
 As pessoas que claramente, com pouca visão ou estiver usando uma tela preto e branca talvez não consigam usar aplicativos com cores embutido.  
  
 Seguir essa recomendação permite que os usuários ajuste combinações de cores com base nas necessidades individuais.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Suporte a alto contraste e todos os atributos de exibição do sistema  
 Aplicativos não devem interromper ou desabilitar as configurações de contraste selecionada pelo usuário, todo o sistema, seleções de cores, ou outras configurações de exibição de todo o sistema e atributos. Configurações do sistema adotadas por um usuário aprimoram a acessibilidade dos aplicativos, para que eles não devem ser desabilitados ou desconsiderados por aplicativos. Cor deve ser usada em combinação correta em primeiro plano no plano de fundo para fornecer contraste adequado. Cores não relacionadas não devem ser misturadas e cores não devem ser revertidas.  
  
 Muitos usuários requerem combinações específicas de alto contraste, como texto branco em um plano de fundo preto. Desenhar esses invertidos, como texto preto em um plano de fundo branco faz com que o plano de fundo Sangrar em primeiro plano e pode dificultar a leitura para alguns usuários.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Verifique todos os UI escala corretamente por qualquer configuração de DPI  
 Certifique-se de que todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pode ser dimensionado corretamente por qualquer [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] configuração. Além disso, verifique se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos cabem em uma tela de 1024 x 768 com 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navegação  
 Práticas recomendadas nesta seção asseguram que navegação foi abordada para controles e aplicativos.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Fornece a Interface do teclado para todos os elementos de interface do usuário  
 Paradas de tabulação, especialmente quando planejado com cuidado, oferecem aos usuários outra maneira navegar a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplicativos devem fornecer as interfaces de teclado a seguir:  
  
-   paradas de tabulação para todos os controles que o usuário pode interagir, como caixas de listagem, botões ou links  
  
-   ordem de tabulação lógica  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Mostrar o foco do teclado  
 Os usuários precisam saber qual objeto tem o foco do teclado para que eles podem prever o efeito de seus pressionamentos de teclas. Para realçar o foco do teclado, use cores, fontes ou elementos gráficos como retângulos ou ampliação. Para realçar audível o foco do teclado, altere o volume, densidade ou qualidade tons.  
  
 Para evitar confusão, aplicativos devem ocultar todos os indicadores de foco visual e seleções dim que estão localizadas em janelas inativas (ou painéis).  
  
 Aplicativos devem fazer o seguinte com foco do teclado:  
  
-   um item sempre deve ter o foco do teclado  
  
-   o foco do teclado deve ser visíveis e óbvio  
  
-   seleções e/ou itens atualmente focados devem ser visualmente realçados  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Suporte a esquemas avançados de navegação e padrões de navegação  
 Diferentes aspectos de navegação de teclado fornecem maneiras diferentes para os usuários navegar o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplicativos devem fornecer as interfaces de teclado a seguir:  
  
-   teclas de atalho e chaves de acesso sublinhada para todos os comandos, menus e controles  
  
-   atalhos de teclado para links importantes  
  
-   todos os itens de menu tem uma chave de acesso; todos os botões têm teclas de aceleração, todos os comandos têm uma tecla de aceleração.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Não deixe o Mouse local interferir com navegação de teclado  
 Local de mouse não deve interferir com navegação de teclado. Para o exemplo, se o mouse não está posicionado em algum lugar e o usuário está navegando com o teclado, um clique do mouse não deve ocorrer a menos que iniciadas pelo usuário.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Interface multimodal  
 Práticas recomendadas nesta seção garantem que o aplicativo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] inclui alternativas para elementos visuais.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Fornecer equivalentes selecionáveis pelo usuário para elementos de texto não  
 Para cada elemento de texto não fornece um equivalente selecionáveis pelo usuário para texto, transcrições ou descrições de áudio, como texto alt, legendas ou comentários visuais.  
  
 Elementos de texto não abrangem uma grande variedade de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos, incluindo: imagens, regiões de mapa de imagem, animações, miniaplicativos, quadros, scripts, botões gráficos, sons, arquivos autônomos de áudio e vídeo. Elementos de texto não são importantes quando elas contêm informações visuais, fala ou informações gerais de áudio que o usuário precise acessar para compreender o conteúdo do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Usar cor mas também forneça alternativas para cores  
 Usar cores para aperfeiçoar, enfatizar ou reiterar informações exibidas por outros meios, mas não se comunicam informações usando apenas cores. Usuários que têm claramente ou tem monocromático precisam de alternativas para cor.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Use APIs de entrada padrão com chamadas independente de dispositivo  
 Chamadas independente de dispositivo garantem que teclado e mouse ofereçam recursos igualmente, enquanto fornece [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] com informações necessárias sobre o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.Peers>  
 [Controle NumericUpDown personalizado com tema e exemplo de suporte de automação de interface do usuário](http://msdn.microsoft.com/library/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Diretrizes de Design de Interface de usuário do teclado](http://msdn2.microsoft.com/library/ms971323.aspx)
