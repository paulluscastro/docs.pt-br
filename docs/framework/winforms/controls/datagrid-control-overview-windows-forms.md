---
title: Visão geral do controle DataGrid (Windows Forms)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd74ed0e31fff211f0197ad27f297f9fbecf5cab
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="datagrid-control-overview-windows-forms"></a>Visão geral do controle DataGrid (Windows Forms)
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> controle exibe dados em uma série de linhas e colunas. O caso mais simples é quando a grade está associada a uma fonte de dados com uma única tabela que não contém relações. Nesse caso, os dados aparecem em linhas e colunas simples, como em uma planilha. Para obter mais informações sobre a vinculação de dados a outros controles, consulte [Vinculação de dados e Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
 Se o <xref:System.Windows.Forms.DataGrid> está associada aos dados com várias tabelas relacionadas e se a grade a navegação está habilitada, a grade exibirá expansores em cada linha. Com um expansor, o usuário pode se mover de uma tabela pai para uma tabela filho. A tabela filho é exibida ao clicar em um nó; a tabela pai original é exibida ao clicar em um botão Voltar. Dessa forma, a grade exibe as relações hierárquicas entre tabelas.  
  
 A captura de tela a seguir mostra um DataGrid associado a dados com várias tabelas.  
  
 ![Um DataGrid associado a dados com várias tabelas](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
Um DataGrid associado a dados com várias tabelas  
  
 O <xref:System.Windows.Forms.DataGrid> pode fornecer uma interface do usuário para um conjunto de dados, a navegação entre tabelas relacionadas e avançados recursos de edição e formatação.  
  
 A exibição e a manipulação de dados são funções separadas: o controle manipula a interface do usuário, enquanto as atualizações de dados são manipuladas pela arquitetura de associação de dados dos Windows Forms e por provedores de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Portanto, vários controles associados à mesma fonte de dados permanecerão em sincronia.  
  
> [!NOTE]
>  Se você estiver familiarizado com o controle DataGrid no Visual Basic 6.0, você encontrará algumas diferenças significativas no Windows Forms <xref:System.Windows.Forms.DataGrid> controle.  
  
 Quando a grade é associada a um <xref:System.Data.DataSet>, as colunas e linhas são criadas automaticamente, formatadas e preenchidas. Para obter mais informações, consulte [Vinculação de dados e Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md). Após a geração do <xref:System.Windows.Forms.DataGrid> controle, você pode adicionar, excluir, reorganizar e formatar colunas e linhas, dependendo de suas necessidades.  
  
## <a name="binding-data-to-the-control"></a>Associação de dados ao controle  
 Para o <xref:System.Windows.Forms.DataGrid> controlar funcione, ele deve ser associado a uma fonte de dados usando o <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades em tempo de design ou o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método em tempo de execução. Essa associação aponta o <xref:System.Windows.Forms.DataGrid> a um objeto de fonte de dados instanciada, como um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>). O <xref:System.Windows.Forms.DataGrid> controle mostra os resultados das ações que são executadas nos dados. A maioria das ações de específicos de dados não são executadas por meio de <xref:System.Windows.Forms.DataGrid> , mas em vez disso, por meio da fonte de dados.  
  
 Se os dados no conjunto de dados associado são atualizados por meio de qualquer mecanismo de <xref:System.Windows.Forms.DataGrid> controle reflete as alterações. Se a grade de dados e seus estilos de tabela e coluna tiver o `ReadOnly` propriedade definida como `false`, os dados no conjunto de dados podem ser atualizados por meio de <xref:System.Windows.Forms.DataGrid> controle.  
  
 Uma única tabela pode ser mostrada no <xref:System.Windows.Forms.DataGrid> por vez. Se uma relação pai-filho é definida entre tabelas, o usuário pode mover entre as tabelas relacionadas para selecionar a tabela a ser exibida no <xref:System.Windows.Forms.DataGrid> controle. Para obter informações sobre associação de um <xref:System.Windows.Forms.DataGrid> o controle para um [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] fonte de dados em tempo de design ou em tempo de execução, consulte [como: associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Fontes de dados válidos para o <xref:System.Windows.Forms.DataGrid> incluem:  
  
-   Classe <xref:System.Data.DataTable>  
  
-   Classe <xref:System.Data.DataView>  
  
-   Classe <xref:System.Data.DataSet>  
  
-   Classe <xref:System.Data.DataViewManager>  
  
 Se a fonte for um conjunto de dados, ele poderá ser um objeto no formulário ou um objeto passado para o formulário por um serviço Web XML. É possível associar a conjuntos de dados tipados ou não tipados.  
  
 Você também pode associar um <xref:System.Windows.Forms.DataGrid> controle estruturas adicionais se os objetos na estrutura, como os elementos de uma matriz, expõem as propriedades públicas. A grade exibirá todas as propriedades públicas dos elementos na estrutura. Por exemplo, se você associar o <xref:System.Windows.Forms.DataGrid> objetos de controle para uma matriz de cliente, a grade exibirá todas as propriedades públicas desses objetos de cliente. Em alguns casos, isso significa que, apesar de ser possível associar à estrutura, a estrutura associada resultante poderá não ter aplicação prática. Você pode, por exemplo, associar a uma matriz de inteiros, mas, como o tipo de dados `Integer` não dá suporte a uma propriedade pública, a grade não consegue exibir nenhum dado.  
  
 Será possível se associar às estruturas a seguir se seus elementos expuserem propriedades públicas:  
  
-   Qualquer componente que implementa o <xref:System.Collections.IList> interface. Isso inclui matrizes de dimensão única.  
  
-   Qualquer componente que implementa o <xref:System.ComponentModel.IListSource> interface.  
  
-   Qualquer componente que implementa o <xref:System.ComponentModel.IBindingList> interface.  
  
 Para obter mais informações sobre possíveis fontes de dados, consulte [Fontes de dados com suporte dos Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Exibição de grade  
 Um uso comum de <xref:System.Windows.Forms.DataGrid> é de controle exibir uma única tabela de dados de um conjunto de dados. No entanto, o controle também pode ser usado para exibir várias tabelas, incluindo tabelas relacionadas. A exibição da grade é ajustada automaticamente de acordo com a fonte de dados. A tabela a seguir mostra o que é exibido para várias configurações.  
  
|Conteúdo do conjunto de dados|O que é exibido|  
|--------------------------|-----------------------|  
|Tabela única.|A tabela é exibida em uma grade.|  
|Várias tabelas.|A grade pode exibir um modo de exibição de árvore em que os usuários podem navegar para localizar a tabela que desejam exibir.|  
|Várias tabelas relacionadas.|A grade pode exibir um modo de exibição de árvore para selecionar tabelas ou é possível especificar para a grade exibir a tabela pai. Os registros na tabela pai permitem que os usuários naveguem até linhas filho relacionadas.|  
  
> [!NOTE]
>  Tabelas em um conjunto de dados relacionadas usando um <xref:System.Data.DataRelation>.  Consulte também [HYPERLINK "http://msdn.microsoft.com/library/dbwcse3d(v=vs.110)" relacionamentos em conjuntos de dados](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\)) ou [relacionamentos em conjuntos de dados](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\)).  
  
 Quando o <xref:System.Windows.Forms.DataGrid> controle está exibindo uma tabela e o <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> está definida como `true`, dados podem ser classificados clicando-se os cabeçalhos de coluna. O usuário também pode adicionar linhas e editar células.  
  
 As relações entre um conjunto de tabelas são exibidas aos usuários por meio do uso de uma estrutura pai/filho de navegação. As tabelas pai são o nível mais alto de dados; as tabelas filho são as tabelas de dados derivadas de listagens de individuais nas tabelas pai. Os expansores são exibidos em cada linha pai que contém uma tabela filho. Ao clicar em um expansor, é gerada uma lista de links semelhantes a links Web para as tabelas filho. Quando o usuário seleciona um link, a tabela filho é exibida. Ao clicar no ícone de exibir/ocultar linhas pai, (![show&#47;hide parent rows icon](../../../../docs/framework/winforms/controls/media/vbicon.gif "vbIcon")), as informações sobre a tabela pai serão ocultadas ou serão exibidas novamente se o usuário as tiver ocultado antes. O usuário pode clicar no botão Voltar para retornar à tabela visualizada anteriormente.  
  
## <a name="columns-and-rows"></a>Colunas e linhas  
 O <xref:System.Windows.Forms.DataGrid> consiste em uma coleção de <xref:System.Windows.Forms.DataGridTableStyle> objetos que estão contidos no <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade. Um estilo de tabela pode conter uma coleção de <xref:System.Windows.Forms.DataGridColumnStyle> objetos que estão contidos no <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade o <xref:System.Windows.Forms.DataGridTableStyle>... Você pode editar o <xref:System.Windows.Forms.DataGrid.TableStyles%2A> e <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedades usando editores de coleção acessados por meio de **propriedades** janela.  
  
 Qualquer <xref:System.Windows.Forms.DataGridTableStyle> associados a <xref:System.Windows.Forms.DataGrid> controle pode ser acessado por meio de <xref:System.Windows.Forms.GridTableStylesCollection>. O <xref:System.Windows.Forms.GridTableStylesCollection> podem ser editados no designer com o <xref:System.Windows.Forms.DataGridTableStyle> editor de coleção, ou programaticamente por meio de <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade.  
  
 ![Objetos incluídos no controle DataGrid](../../../../docs/framework/winforms/controls/media/vbcolumns1.gif "vbColumns1")  
A ilustração a seguir mostra os objetos incluídos no controle DataGrid.  
  
 Estilos de tabela e coluna são sincronizados com <xref:System.Data.DataTable> objetos e <xref:System.Data.DataColumn> objetos definindo suas `MappingName` propriedades ao apropriado <xref:System.Data.DataTable.TableName%2A> e <xref:System.Data.DataColumn.ColumnName%2A> propriedades. Quando um <xref:System.Windows.Forms.DataGridTableStyle> que não possui nenhuma coluna estilos é adicionado a um <xref:System.Windows.Forms.DataGrid> controle associado a uma fonte de dados válidos e o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade desse estilo de tabela está definida como uma opção válida <xref:System.Data.DataTable.TableName%2A> propriedade, uma coleção de <xref:System.Windows.Forms.DataGridColumnStyle> objetos é criado para que estilo de tabela. Para cada <xref:System.Data.DataColumn> encontrado no <xref:System.Data.DataTable.Columns%2A> coleção do <xref:System.Data.DataTable>, correspondente <xref:System.Windows.Forms.DataGridColumnStyle> é adicionada para o <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> é acessada por meio de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade o <xref:System.Windows.Forms.DataGridTableStyle>. Colunas podem ser adicionadas ou excluídas da grade usando o <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> ou <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> método sobre o <xref:System.Windows.Forms.GridColumnStylesCollection>. Para obter mais informações, consulte [Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) e [Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Uma coleção de tipos de coluna estende o <xref:System.Windows.Forms.DataGridColumnStyle> classe com formatação sofisticada e recursos de edição. Todos os tipos de coluna herdam o <xref:System.Windows.Forms.DataGridColumnStyle> classe base. A classe que é criada depende o <xref:System.Data.DataColumn.DataType%2A> propriedade do <xref:System.Data.DataColumn> do qual o <xref:System.Web.UI.WebControls.DataGridColumn> baseia-se. Por exemplo, um <xref:System.Data.DataColumn> com seus <xref:System.Data.DataColumn.DataType%2A> propriedade definida como <xref:System.Boolean> será associado a <xref:System.Windows.Forms.DataGridBoolColumn>. A tabela a seguir descreve cada um desses tipos de coluna.  
  
|Tipo de coluna|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Aceita e exibe os dados como cadeias de caracteres formatadas ou não formatadas. Recursos de edição são os mesmos para editar dados em uma simples <xref:System.Windows.Forms.TextBox>. Herda de <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Aceita e exibe `true`, `false` e valores nulos. Herda de <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Ao clicar duas vezes na borda direita de uma coluna, a coluna é redimensionada para exibir a legenda completa e a maior entrada.  
  
## <a name="table-styles-and-column-styles"></a>Estilos de tabela e de coluna  
 Como o formato padrão de estabelecer o <xref:System.Windows.Forms.DataGrid> controle, você pode personalizar as cores que serão usadas quando determinadas tabelas são exibidas na grade de dados.  
  
 Isso é feito por meio da criação de instâncias da <xref:System.Windows.Forms.DataGridTableStyle> classe. Estilos de tabela de especificam a formatação de tabelas específicas, diferentes do que a formatação padrão da <xref:System.Windows.Forms.DataGrid> próprio controle. Cada tabela poderá ter apenas um estilo de tabela definido para ela de cada vez.  
  
 Às vezes, queremos que uma coluna específica tenha uma aparência diferente do restante das colunas de uma tabela de dados específica. Você pode criar um conjunto personalizado de estilos de coluna usando o <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade.  
  
 Os estilos de coluna estão relacionados às colunas em um conjunto de dados, assim como os estilos de tabelas estão relacionados às tabelas de dados. Assim como cada tabela poderá ter apenas um estilo de tabela definido para ela por vez, cada coluna poderá ter apenas um estilo de coluna definido para ela, em um estilo de tabela específico. Essa relação é definida na coluna de <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriedade.  
  
 Se você tiver criado um estilo de tabela sem estilos de coluna adicionados a ele, o Visual Studio adicionará estilos de coluna padrão quando o formulário e a grade são criados em tempo de execução. No entanto, se você tiver criado um estilo de tabela e adicionado os estilos de coluna, o Visual Studio não criará os estilos de coluna. Além disso, será necessário definir estilos de coluna e atribuí-los com o nome de mapeamento para que as colunas desejadas sejam exibidas na grade.  
  
 Como as colunas que serão incluídas na grade de dados são especificadas por meio da atribuição de um estilo de coluna e como nenhum estilo de coluna foi atribuído às colunas, é possível incluir colunas de dados no conjunto de dados que não são exibidas na grade. Porém, já que a coluna de dados está incluída no conjunto de dados, os dados não exibidos podem ser editados programaticamente.  
  
> [!NOTE]
>  Em geral, crie estilos de coluna e adicione-os à coleção de estilos de coluna antes de adicionar os estilos de tabela à coleção de estilos de tabela. Quando você adiciona um estilo de tabela vazio à coleção, os estilos de coluna são gerados automaticamente. Consequentemente, uma exceção será lançada se você tentar adicionar novos estilos de coluna com duplicata <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valores para a coleção de estilos de coluna.  
>   
>  Às vezes, será necessário ajustar somente uma coluna entre muitas colunas; por exemplo, o conjunto de dados contém 50 colunas e você quer apenas 49. Nesse caso, é mais fácil importar as 50 colunas e remover uma programaticamente, em vez de adicionar programaticamente cada uma das 49 colunas individuais desejadas.  
  
## <a name="formatting"></a>Formatação  
 Formatação que podem ser aplicadas para o <xref:System.Windows.Forms.DataGrid> controle inclui estilos de borda, estilos de linha de grade, fontes, propriedades da legenda, alinhamento de dados e as cores de plano de fundo entre linhas alternadas. Para obter mais informações, consulte [Como formatar o controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Eventos  
 Além de comuns controlar eventos como <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, e <xref:System.Windows.Forms.DataGrid.Scroll>, o <xref:System.Windows.Forms.DataGrid> controle oferece suporte a eventos associados a edição e navegação dentro da grade. O <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> propriedade determina a célula que está selecionada. O <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> é gerado quando o usuário navega para outra célula. Quando o usuário navega para uma nova tabela por meio de relações pai/filho, o <xref:System.Windows.Forms.DataGrid.Navigate> é gerado. O <xref:System.Windows.Forms.DataGrid.BackButtonClick> é gerado quando o usuário clica no botão Voltar quando o usuário está exibindo uma tabela filho e o <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> é gerado quando o ícone de linhas pai Mostrar/ocultar é clicado.  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Como formatar o controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)
