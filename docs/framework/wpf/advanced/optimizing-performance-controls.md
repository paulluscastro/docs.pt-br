---
title: 'Otimizando desempenho: controles'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b8008d104437454f36f6f425634c40968d5481a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-controls"></a>Otimizando desempenho: controles
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inclui muitos dos componentes comuns de interface do usuário que são usados na maioria dos aplicativos do Windows. Este tópico contém técnicas para melhorar o desempenho de sua interface do usuário.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Exibindo conjuntos de dados grandes  
 WPF controla como o <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ComboBox> são usados para exibir listas de itens em um aplicativo. Se a lista a ser exibida for grande, o desempenho do aplicativo poderá ser afetado. Isso ocorre porque o sistema de layout padrão cria um contêiner de layout para cada item associado ao controle de lista e computa a posição e tamanho do layout. Normalmente, você não precisa exibir todos os itens ao mesmo tempo. Em vez disso, você exibe um subconjunto e o usuário rola pela lista. Nesse caso, faz sentido usar a *virtualização* da interface do usuário, o que significa que a geração de contêiner do item e a computação do layout associado a um item são adiadas até que o item esteja visível.  
  
 A virtualização da interface do usuário é um aspecto importante dos controles de lista. A virtualização da interface do usuário não deve ser confundida com a virtualização de dados. A virtualização da interface do usuário armazena somente os itens visíveis na memória, mas em um cenário de associação de dados, armazena toda a estrutura de dados na memória. Em contraste, a virtualização de dados armazena somente os itens de dados visíveis na tela na memória.  
  
 Por padrão, a virtualização de interface do usuário está habilitada para o <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ListBox> controla quando seus itens de lista estão associados aos dados. <xref:System.Windows.Controls.TreeView>a virtualização pode ser habilitada definindo o <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` anexado a propriedade `true`. Se você deseja habilitar a virtualização de interface do usuário para controles personalizados que derivam de <xref:System.Windows.Controls.ItemsControl> ou controles de item existente que usam o <xref:System.Windows.Controls.StackPanel> classe, como <xref:System.Windows.Controls.ComboBox>, você pode definir o <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> para <xref:System.Windows.Controls.VirtualizingStackPanel> e defina <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> para `true`. Infelizmente, você pode desabilitar a virtualização da interface do usuário para esses controles sem perceber. A seguir, temos uma lista de condições que desabilitam a virtualização da interface do usuário.  
  
-   Contêineres de itens são adicionados diretamente para o <xref:System.Windows.Controls.ItemsControl>. Por exemplo, se um aplicativo explicitamente adiciona <xref:System.Windows.Controls.ListBoxItem> objetos para um <xref:System.Windows.Controls.ListBox>, o <xref:System.Windows.Controls.ListBox> não virtualizar o <xref:System.Windows.Controls.ListBoxItem> objetos.  
  
-   Contêineres de item de <xref:System.Windows.Controls.ItemsControl> são de tipos diferentes. Por exemplo, um <xref:System.Windows.Controls.Menu> que usa <xref:System.Windows.Controls.Separator> objetos não podem implementar o item de reciclagem porque o <xref:System.Windows.Controls.Menu> contém objetos do tipo <xref:System.Windows.Controls.Separator> e <xref:System.Windows.Controls.MenuItem>.  
  
-   Configuração <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> para `false`.  
  
-   Configuração <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` para `false`.  
  
 Uma consideração importante quando você virtualiza contêineres de itens é se você tem informações de estado adicionais associadas a um contêiner de item que pertence ao item. Nesse caso, você precisa salvar o estado adicional. Por exemplo, você pode ter um item contido em um <xref:System.Windows.Controls.Expander> controle e o <xref:System.Windows.Controls.Expander.IsExpanded%2A> estado associado ao contêiner do item e não para o próprio item. Quando o contêiner é reutilizado para um novo item, o valor atual de <xref:System.Windows.Controls.Expander.IsExpanded%2A> é usado para o novo item. Além disso, o item antigo perde corretas <xref:System.Windows.Controls.Expander.IsExpanded%2A> valor.  
  
 Atualmente, nenhum controle do WPF dá suporte interno para a virtualização de dados.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Reciclagem de Contêineres  
 Uma otimização para virtualização de interface de usuário adicionada no .NET Framework 3.5 SP1 para controles que herdam de <xref:System.Windows.Controls.ItemsControl> é *reciclagem de contêiner,* que também podem melhorar o desempenho da rolagem.  Quando um <xref:System.Windows.Controls.ItemsControl> que usa a virtualização de interface do usuário é preenchida, ele cria um contêiner de itens para cada item é movido para a exibição e destrói o contêiner de itens para cada item que rola para fora da exibição. *Reciclagem de contêiner* permite que o controle reutilizar os contêineres de item existente para itens de dados diferentes, para que os contêineres de itens não constantemente são criados e destruídos quando o usuário rolar a <xref:System.Windows.Controls.ItemsControl>. Você pode optar por habilitar o item de reciclagem definindo o <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> anexado propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Qualquer <xref:System.Windows.Controls.ItemsControl> que ofereça suporte a virtualização pode usar a reciclagem de contêiner.  Para obter um exemplo de como habilitar a reciclagem de contêiner em uma <xref:System.Windows.Controls.ListBox>, consulte [melhorar o desempenho de rolagem de uma caixa de listagem](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Suporte à virtualização bidirecional  
 <xref:System.Windows.Controls.VirtualizingStackPanel>oferece suporte interno para virtualização de interface do usuário em uma direção, horizontal ou verticalmente. Se você deseja usar virtualização bidirecional para os controles, você deve implementar um painel personalizado que estende o <xref:System.Windows.Controls.VirtualizingStackPanel> classe. O <xref:System.Windows.Controls.VirtualizingStackPanel> classe expõe os métodos virtuais, como <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, e <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Esses métodos virtuais permitem detectar uma alteração na parte visível de uma lista e manipulá-lo adequadamente.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Otimizando modelos  
 A árvore visual contém todos os elementos visuais de um aplicativo.  Além dos objetos criados diretamente, ela também contém objetos decorrentes da expansão do modelo.  Por exemplo, quando você cria um <xref:System.Windows.Controls.Button>, você também pode obter <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> e <xref:System.Windows.Controls.ContentPresenter> objetos na árvore visual.  Se ainda não tiver otimizado seus modelos de controle, você poderá estar criando muitos objetos extra desnecessários na árvore visual.   Para obter mais informações sobre a árvore visual, consulte [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Rolagem Adiada  
 Por padrão, quando o usuário arrasta o controle de posição em uma barra de rolagem, a exibição de conteúdo é atualizada continuamente.  Se a rolagem estiver lenta em seu controle, considere usar a rolagem adiada.  Com a rolagem adiada, o conteúdo é atualizado somente quando o usuário libera o controle de posição.  
  
 Para implementar a rolagem adiada, defina o <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> propriedade `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>é uma propriedade anexada e pode ser definida em <xref:System.Windows.Controls.ScrollViewer> e qualquer controle que possui um <xref:System.Windows.Controls.ScrollViewer> em seu modelo de controle.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Controles que implementam recursos de desempenho  
 A tabela a seguir lista os controles comuns para exibir dados e seu suporte a recursos de desempenho.  Consulte as seções anteriores para obter informações sobre como habilitar esses recursos.  
  
|Controle|Virtualização|Reciclagem de contêineres|Rolagem adiada|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ContextMenu>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.DocumentViewer>|Não disponível|Não disponível|Pode ser habilitado|  
|<xref:System.Windows.Controls.ListBox>|Padrão|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ListView>|Padrão|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.TreeView>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ToolBar>|Não disponível|Não disponível|Pode ser habilitado|  
  
> [!NOTE]
>  Para obter um exemplo de como habilitar a virtualização e o contêiner de reciclagem em um <xref:System.Windows.Controls.TreeView>, consulte [melhorar o desempenho de um modo de exibição de árvore](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Layout](../../../../docs/framework/wpf/advanced/layout.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Controles](../../../../docs/framework/wpf/controls/index.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
