---
title: "Otimizando desempenho: vinculação de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36f7f1fa5aee672caea7d79fabfc0408c4186cdd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-data-binding"></a><span data-ttu-id="f052e-102">Otimizando desempenho: vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="f052e-102">Optimizing Performance: Data Binding</span></span>
<span data-ttu-id="f052e-103">A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] data binding provides a simple and consistent way for applications to present and interact with data.</span></span> <span data-ttu-id="f052e-104">Os elementos podem ser associados aos dados de uma variedade de fontes de dados na forma de objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] e [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f052e-104">Elements can be bound to data from a variety of data sources in the form of [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objects and [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span></span>  
  
 <span data-ttu-id="f052e-105">Este tópico apresenta recomendações de desempenho de vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-105">This topic provides data binding performance recommendations.</span></span>  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a><span data-ttu-id="f052e-106">Como as referências de vinculação de dados são resolvidas</span><span class="sxs-lookup"><span data-stu-id="f052e-106">How Data Binding References are Resolved</span></span>  
 <span data-ttu-id="f052e-107">Antes de discutir os problemas de desempenho da vinculação de dados, vale a pena explorar como o mecanismo de vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] resolve referências de objeto para associação.</span><span class="sxs-lookup"><span data-stu-id="f052e-107">Before discussing data binding performance issues, it is worthwhile to explore how the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] data binding engine resolves object references for binding.</span></span>  
  
 <span data-ttu-id="f052e-108">A origem de uma vinculação de dados [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode ser qualquer objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f052e-108">The source of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] data binding can be any [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object.</span></span> <span data-ttu-id="f052e-109">Você pode associar a propriedades, subpropriedades ou indexadores de um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f052e-109">You can bind to properties, sub-properties, or indexers of a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object.</span></span> <span data-ttu-id="f052e-110">As referências de associação são resolvidas usando [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] reflexão ou um <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="f052e-110">The binding references are resolved by using either [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] reflection or an <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="f052e-111">Aqui estão três métodos para resolver referências de objeto para associação.</span><span class="sxs-lookup"><span data-stu-id="f052e-111">Here are three methods for resolving object references for binding.</span></span>  
  
 <span data-ttu-id="f052e-112">O primeiro método envolve o uso de reflexão.</span><span class="sxs-lookup"><span data-stu-id="f052e-112">The first method involves using reflection.</span></span> <span data-ttu-id="f052e-113">Nesse caso, o <xref:System.Reflection.PropertyInfo> objeto é usado para descobrir os atributos da propriedade e fornece acesso aos metadados de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f052e-113">In this case, the <xref:System.Reflection.PropertyInfo> object is used to discover the attributes of the property and provides access to property metadata.</span></span> <span data-ttu-id="f052e-114">Ao usar o <xref:System.ComponentModel.ICustomTypeDescriptor> interface, o mecanismo de associação de dados usa esta interface para acessar os valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f052e-114">When using the <xref:System.ComponentModel.ICustomTypeDescriptor> interface, the data binding engine uses this interface to access the property values.</span></span> <span data-ttu-id="f052e-115">O <xref:System.ComponentModel.ICustomTypeDescriptor> interface é especialmente útil em casos onde o objeto não tem um conjunto estático de propriedades.</span><span class="sxs-lookup"><span data-stu-id="f052e-115">The <xref:System.ComponentModel.ICustomTypeDescriptor> interface is especially useful in cases where the object does not have a static set of properties.</span></span>  
  
 <span data-ttu-id="f052e-116">As notificações de alteração de propriedade podem ser fornecidas implementando a <xref:System.ComponentModel.INotifyPropertyChanged> interface ou usando as notificações de alteração associadas a <xref:System.ComponentModel.TypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="f052e-116">Property change notifications can be provided either by implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface or by using the change notifications associated with the <xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="f052e-117">No entanto, a estratégia preferencial para implementar notificações de alteração de propriedade é usar <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="f052e-117">However, the preferred strategy for implementing property change notifications is to use <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
 <span data-ttu-id="f052e-118">Se o objeto de origem for um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto e a propriedade de origem é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedade, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mecanismo de associação de dados deve primeiro usar reflexão no objeto de origem para obter o <xref:System.ComponentModel.TypeDescriptor>e, em seguida, consultar um <xref:System.ComponentModel.PropertyDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="f052e-118">If the source object is a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object and the source property is a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] data binding engine has to first use reflection on the source object to get the <xref:System.ComponentModel.TypeDescriptor>, and then query for a <xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="f052e-119">Essa sequência de operações de reflexão é potencialmente muito demorada de uma perspectiva de desempenho.</span><span class="sxs-lookup"><span data-stu-id="f052e-119">This sequence of reflection operations is potentially very time-consuming from a performance perspective.</span></span>  
  
 <span data-ttu-id="f052e-120">O segundo método para resolver referências de objeto envolve um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto de origem que implementa o <xref:System.ComponentModel.INotifyPropertyChanged> interface e uma propriedade de fonte que é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedade.</span><span class="sxs-lookup"><span data-stu-id="f052e-120">The second method for resolving object references involves a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] source object that implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface, and a source property that is a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property.</span></span> <span data-ttu-id="f052e-121">Nesse caso, o mecanismo de vinculação de dados usa reflexão diretamente no tipo de fonte e obtém a propriedade necessária.</span><span class="sxs-lookup"><span data-stu-id="f052e-121">In this case, the data binding engine uses reflection directly on the source type and gets the required property.</span></span> <span data-ttu-id="f052e-122">Este ainda não é o melhor método, mas ele custará menos nos requisitos de conjunto de trabalho do que o primeiro método.</span><span class="sxs-lookup"><span data-stu-id="f052e-122">This is still not the optimal method, but it will cost less in working set requirements than the first method.</span></span>  
  
 <span data-ttu-id="f052e-123">O terceiro método para resolver referências de objeto envolve um objeto de fonte que é uma <xref:System.Windows.DependencyObject> e uma propriedade de fonte que é um <xref:System.Windows.DependencyProperty>.</span><span class="sxs-lookup"><span data-stu-id="f052e-123">The third method for resolving object references involves a source object that is a <xref:System.Windows.DependencyObject> and a source property that is a <xref:System.Windows.DependencyProperty>.</span></span> <span data-ttu-id="f052e-124">Nesse caso, o mecanismo de vinculação de dados não precisa usar reflexão.</span><span class="sxs-lookup"><span data-stu-id="f052e-124">In this case, the data binding engine does not need to use reflection.</span></span> <span data-ttu-id="f052e-125">Em vez disso, o mecanismo de propriedade e o mecanismo de vinculação de dados resolvem juntos a referência da propriedade independentemente.</span><span class="sxs-lookup"><span data-stu-id="f052e-125">Instead, the property engine and the data binding engine together resolve the property reference independently.</span></span> <span data-ttu-id="f052e-126">Esse é o melhor método para resolver referências de objeto usadas para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-126">This is the optimal method for resolving object references used for data binding.</span></span>  
  
 <span data-ttu-id="f052e-127">A tabela abaixo compara a velocidade da associação de dados de <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade de mil <xref:System.Windows.Controls.TextBlock> elementos usando esses três métodos.</span><span class="sxs-lookup"><span data-stu-id="f052e-127">The table below compares the speed of data binding the <xref:System.Windows.Controls.TextBlock.Text%2A> property of one thousand <xref:System.Windows.Controls.TextBlock> elements using these three methods.</span></span>  
  
|<span data-ttu-id="f052e-128">**Associando a propriedade Text de um TextBlock**</span><span class="sxs-lookup"><span data-stu-id="f052e-128">**Binding the Text property of a TextBlock**</span></span>|<span data-ttu-id="f052e-129">**Tempo de associação (ms)**</span><span class="sxs-lookup"><span data-stu-id="f052e-129">**Binding time (ms)**</span></span>|<span data-ttu-id="f052e-130">**Tempo de renderização – inclui associação (ms)**</span><span class="sxs-lookup"><span data-stu-id="f052e-130">**Render time -- includes binding (ms)**</span></span>|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|<span data-ttu-id="f052e-131">Para uma propriedade de um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f052e-131">To a property of a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object</span></span>|<span data-ttu-id="f052e-132">115</span><span class="sxs-lookup"><span data-stu-id="f052e-132">115</span></span>|<span data-ttu-id="f052e-133">314</span><span class="sxs-lookup"><span data-stu-id="f052e-133">314</span></span>|  
|<span data-ttu-id="f052e-134">Para uma propriedade de um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto que implementa<xref:System.ComponentModel.INotifyPropertyChanged></span><span class="sxs-lookup"><span data-stu-id="f052e-134">To a property of a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object which implements <xref:System.ComponentModel.INotifyPropertyChanged></span></span>|<span data-ttu-id="f052e-135">115</span><span class="sxs-lookup"><span data-stu-id="f052e-135">115</span></span>|<span data-ttu-id="f052e-136">305</span><span class="sxs-lookup"><span data-stu-id="f052e-136">305</span></span>|  
|<span data-ttu-id="f052e-137">Para uma <xref:System.Windows.DependencyProperty> de um <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="f052e-137">To a <xref:System.Windows.DependencyProperty> of a <xref:System.Windows.DependencyObject>.</span></span>|<span data-ttu-id="f052e-138">90</span><span class="sxs-lookup"><span data-stu-id="f052e-138">90</span></span>|<span data-ttu-id="f052e-139">263</span><span class="sxs-lookup"><span data-stu-id="f052e-139">263</span></span>|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a><span data-ttu-id="f052e-140">Associando a objetos CLR grandes</span><span class="sxs-lookup"><span data-stu-id="f052e-140">Binding to Large CLR Objects</span></span>  
 <span data-ttu-id="f052e-141">Há um impacto significativo no desempenho ao associar dados a um único objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com milhares de propriedades.</span><span class="sxs-lookup"><span data-stu-id="f052e-141">There is a significant performance impact when you data bind to a single [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object with thousands of properties.</span></span> <span data-ttu-id="f052e-142">Você pode minimizar esse impacto dividindo o objeto único em vários objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com menos propriedades.</span><span class="sxs-lookup"><span data-stu-id="f052e-142">You can minimize this impact by dividing the single object into multiple [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objects with fewer properties.</span></span> <span data-ttu-id="f052e-143">A tabela mostra os tempos de renderização e associação da vinculação de dados para um único objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] grande em comparação com vários objetos menores.</span><span class="sxs-lookup"><span data-stu-id="f052e-143">The table shows the binding and rendering times for data binding to a single large [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object versus multiple smaller objects.</span></span>  
  
|<span data-ttu-id="f052e-144">**Vinculação de dados de mil objetos TextBlock**</span><span class="sxs-lookup"><span data-stu-id="f052e-144">**Data binding 1000 TextBlock objects**</span></span>|<span data-ttu-id="f052e-145">**Tempo de associação (ms)**</span><span class="sxs-lookup"><span data-stu-id="f052e-145">**Binding time (ms)**</span></span>|<span data-ttu-id="f052e-146">**Tempo de renderização – inclui associação (ms)**</span><span class="sxs-lookup"><span data-stu-id="f052e-146">**Render time -- includes binding (ms)**</span></span>|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|<span data-ttu-id="f052e-147">Para um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com mil propriedades</span><span class="sxs-lookup"><span data-stu-id="f052e-147">To a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object with 1000 properties</span></span>|<span data-ttu-id="f052e-148">950</span><span class="sxs-lookup"><span data-stu-id="f052e-148">950</span></span>|<span data-ttu-id="f052e-149">1200</span><span class="sxs-lookup"><span data-stu-id="f052e-149">1200</span></span>|  
|<span data-ttu-id="f052e-150">Para mil objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com uma propriedade</span><span class="sxs-lookup"><span data-stu-id="f052e-150">To 1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objects with one property</span></span>|<span data-ttu-id="f052e-151">115</span><span class="sxs-lookup"><span data-stu-id="f052e-151">115</span></span>|<span data-ttu-id="f052e-152">314</span><span class="sxs-lookup"><span data-stu-id="f052e-152">314</span></span>|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a><span data-ttu-id="f052e-153">Associando a um ItemsSource</span><span class="sxs-lookup"><span data-stu-id="f052e-153">Binding to an ItemsSource</span></span>  
 <span data-ttu-id="f052e-154">Considere um cenário em que você tenha um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto que contém uma lista de funcionários que você deseja exibir em um <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="f052e-154">Consider a scenario in which you have a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> object that holds a list of employees that you want to display in a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="f052e-155">Para criar uma correspondência entre esses dois objetos, você deve vincular sua lista de funcionários para o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="f052e-155">To create a correspondence between these two objects, you would bind your employee list to the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="f052e-156">No entanto, suponha que você tenha um novo funcionário ingressando em seu grupo.</span><span class="sxs-lookup"><span data-stu-id="f052e-156">However, suppose you have a new employee joining your group.</span></span> <span data-ttu-id="f052e-157">Você pode pensar que para inserir essa nova pessoa em seu limite <xref:System.Windows.Controls.ListBox> valores, você simplesmente adicionar esta pessoa à sua lista de funcionários e esperar que essa alteração seja reconhecida pelo mecanismo de associação de dados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f052e-157">You might think that in order to insert this new person into your bound <xref:System.Windows.Controls.ListBox> values, you would simply add this person to your employee list and expect this change to be recognized by the data binding engine automatically.</span></span> <span data-ttu-id="f052e-158">Essa suposição iria se provar falsa; Na realidade, a alteração não será refletida no <xref:System.Windows.Controls.ListBox> automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f052e-158">That assumption would prove false; in actuality, the change will not be reflected in the <xref:System.Windows.Controls.ListBox> automatically.</span></span> <span data-ttu-id="f052e-159">Isso ocorre porque o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto não gera automaticamente um evento de alteração de coleção.</span><span class="sxs-lookup"><span data-stu-id="f052e-159">This is because the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> object does not automatically raise a collection changed event.</span></span> <span data-ttu-id="f052e-160">Para obter o <xref:System.Windows.Controls.ListBox> para acompanhar as alterações, você precisaria recriar sua lista de funcionários e reanexá-lo para o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="f052e-160">In order to get the <xref:System.Windows.Controls.ListBox> to pick up the changes, you would have to recreate your list of employees and re-attach it to the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="f052e-161">Embora essa solução funcione, ela ocasiona um grande impacto no desempenho.</span><span class="sxs-lookup"><span data-stu-id="f052e-161">While this solution works, it introduces a huge performance impact.</span></span> <span data-ttu-id="f052e-162">Sempre que você reatribuir o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ListBox> para um novo objeto, o <xref:System.Windows.Controls.ListBox> primeiro joga fora de seus itens anteriores e regenera sua lista inteira.</span><span class="sxs-lookup"><span data-stu-id="f052e-162">Each time you reassign the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of <xref:System.Windows.Controls.ListBox> to a new object, the <xref:System.Windows.Controls.ListBox> first throws away its previous items and regenerates its entire list.</span></span> <span data-ttu-id="f052e-163">O impacto no desempenho é ampliado se sua <xref:System.Windows.Controls.ListBox> é mapeado para um complexo <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="f052e-163">The performance impact is magnified if your <xref:System.Windows.Controls.ListBox> maps to a complex <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="f052e-164">Uma solução muito eficiente para esse problema é fazer o funcionário listar um <xref:System.Collections.ObjectModel.ObservableCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="f052e-164">A very efficient solution to this problem is to make your employee list an <xref:System.Collections.ObjectModel.ObservableCollection%601>.</span></span> <span data-ttu-id="f052e-165">Um <xref:System.Collections.ObjectModel.ObservableCollection%601> objeto gera uma notificação de alteração que o mecanismo de associação de dados pode receber.</span><span class="sxs-lookup"><span data-stu-id="f052e-165">An <xref:System.Collections.ObjectModel.ObservableCollection%601> object raises a change notification which the data binding engine can receive.</span></span> <span data-ttu-id="f052e-166">O evento adiciona ou remove um item de um <xref:System.Windows.Controls.ItemsControl> sem precisar gerar a lista inteira.</span><span class="sxs-lookup"><span data-stu-id="f052e-166">The event adds or removes an item from an <xref:System.Windows.Controls.ItemsControl> without the need to regenerate the entire list.</span></span>  
  
 <span data-ttu-id="f052e-167">A tabela abaixo mostra o tempo necessário para atualizar o <xref:System.Windows.Controls.ListBox> (com virtualização de interface do usuário desativada) quando um item é adicionado.</span><span class="sxs-lookup"><span data-stu-id="f052e-167">The table below shows the time it takes to update the <xref:System.Windows.Controls.ListBox> (with UI virtualization turned off) when one item is added.</span></span> <span data-ttu-id="f052e-168">O número da primeira linha representa o tempo decorrido quando o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto está associado a <xref:System.Windows.Controls.ListBox> do elemento <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="f052e-168">The number in the first row represents the elapsed time when the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> object is bound to <xref:System.Windows.Controls.ListBox> element's <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.</span></span> <span data-ttu-id="f052e-169">O número na segunda linha representa o tempo decorrido quando uma <xref:System.Collections.ObjectModel.ObservableCollection%601> está associada ao <xref:System.Windows.Controls.ListBox> do elemento <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="f052e-169">The number in the second row represents the elapsed time when an <xref:System.Collections.ObjectModel.ObservableCollection%601> is bound to the <xref:System.Windows.Controls.ListBox> element's <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.</span></span> <span data-ttu-id="f052e-170">Observe que a economia de tempo significativo usando o <xref:System.Collections.ObjectModel.ObservableCollection%601> estratégia de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-170">Note the significant time savings using the <xref:System.Collections.ObjectModel.ObservableCollection%601> data binding strategy.</span></span>  
  
|<span data-ttu-id="f052e-171">**Vinculação de dados de ItemsSource**</span><span class="sxs-lookup"><span data-stu-id="f052e-171">**Data binding the ItemsSource**</span></span>|<span data-ttu-id="f052e-172">**Atualizar tempo para 1 item (ms)**</span><span class="sxs-lookup"><span data-stu-id="f052e-172">**Update time for 1 item (ms)**</span></span>|  
|--------------------------------------|---------------------------------------|  
|<span data-ttu-id="f052e-173">Para uma [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objeto</span><span class="sxs-lookup"><span data-stu-id="f052e-173">To a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> object</span></span>|<span data-ttu-id="f052e-174">1656</span><span class="sxs-lookup"><span data-stu-id="f052e-174">1656</span></span>|  
|<span data-ttu-id="f052e-175">Para um<xref:System.Collections.ObjectModel.ObservableCollection%601></span><span class="sxs-lookup"><span data-stu-id="f052e-175">To an <xref:System.Collections.ObjectModel.ObservableCollection%601></span></span>|<span data-ttu-id="f052e-176">20</span><span class="sxs-lookup"><span data-stu-id="f052e-176">20</span></span>|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a><span data-ttu-id="f052e-177">Associar IList a ItemsControl não IEnumerable</span><span class="sxs-lookup"><span data-stu-id="f052e-177">Bind IList to ItemsControl not IEnumerable</span></span>  
 <span data-ttu-id="f052e-178">Se você tem a opção de associar um <xref:System.Collections.Generic.IList%601> ou um <xref:System.Collections.IEnumerable> para um <xref:System.Windows.Controls.ItemsControl> de objeto, escolha o <xref:System.Collections.Generic.IList%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="f052e-178">If you have a choice between binding an <xref:System.Collections.Generic.IList%601> or an <xref:System.Collections.IEnumerable> to an <xref:System.Windows.Controls.ItemsControl> object, choose the <xref:System.Collections.Generic.IList%601> object.</span></span> <span data-ttu-id="f052e-179">Associação <xref:System.Collections.IEnumerable> para um <xref:System.Windows.Controls.ItemsControl> força [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para criar um wrapper <xref:System.Collections.Generic.IList%601> objeto, o que significa que o desempenho é afetado pela sobrecarga desnecessária de um segundo objeto.</span><span class="sxs-lookup"><span data-stu-id="f052e-179">Binding <xref:System.Collections.IEnumerable> to an <xref:System.Windows.Controls.ItemsControl> forces [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to create a wrapper <xref:System.Collections.Generic.IList%601> object, which means your performance is impacted by the unnecessary overhead of a second object.</span></span>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a><span data-ttu-id="f052e-180">Não converta objetos CLR em XML apenas para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-180">Do not Convert CLR objects to XML Just for Data Binding.</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="f052e-181"> permite associar dados a conteúdo [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. No entanto, a vinculação de dados ao conteúdo [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] é mais lenta que a vinculação de dados a objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f052e-181"> allows you to data bind to [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] content; however, data binding to [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] content is slower than data binding to [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objects.</span></span> <span data-ttu-id="f052e-182">Não converta os dados de objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] em XML se o único objetivo for a vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="f052e-182">Do not convert [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object data to XML if the only purpose is for data binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f052e-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f052e-183">See Also</span></span>  
 [<span data-ttu-id="f052e-184">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="f052e-184">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="f052e-185">Planejando para desempenho do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f052e-185">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [<span data-ttu-id="f052e-186">Aproveitando o hardware</span><span class="sxs-lookup"><span data-stu-id="f052e-186">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [<span data-ttu-id="f052e-187">Layout e design</span><span class="sxs-lookup"><span data-stu-id="f052e-187">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [<span data-ttu-id="f052e-188">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="f052e-188">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="f052e-189">Comportamento do objeto</span><span class="sxs-lookup"><span data-stu-id="f052e-189">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [<span data-ttu-id="f052e-190">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f052e-190">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [<span data-ttu-id="f052e-191">Texto</span><span class="sxs-lookup"><span data-stu-id="f052e-191">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [<span data-ttu-id="f052e-192">Outras recomendações de desempenho</span><span class="sxs-lookup"><span data-stu-id="f052e-192">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [<span data-ttu-id="f052e-193">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="f052e-193">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f052e-194">Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="f052e-194">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)