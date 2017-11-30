---
title: "Visão geral do componente ContextMenu (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6c2542ca7ee27bec96bb5010bcdb2fcd7416f72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="54970-102">Visão geral do componente ContextMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="54970-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="54970-103">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> controles de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para uso futuro e compatibilidade com versões anteriores, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="54970-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="54970-104">Com o Windows Forms <xref:System.Windows.Forms.ContextMenu> componente, você pode fornecer aos usuários um menu de atalho facilmente acessível de comandos usados com frequência que estão associados com o objeto selecionado.</span><span class="sxs-lookup"><span data-stu-id="54970-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="54970-105">Os itens em um menu de atalho frequentemente são um subconjunto dos itens de menus principais que aparecem em outro lugar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54970-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="54970-106">Um usuário geralmente pode acessar um menu de atalho clicando com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="54970-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="54970-107">nos Windows Forms, menus de atalho são associados a controles.</span><span class="sxs-lookup"><span data-stu-id="54970-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="54970-108">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="54970-108">Key Properties</span></span>  
 <span data-ttu-id="54970-109">Você pode associar um menu de atalho com um controle, definindo o controle <xref:System.Windows.Forms.Control.ContextMenu%2A> propriedade para o <xref:System.Windows.Forms.ContextMenu> componente.</span><span class="sxs-lookup"><span data-stu-id="54970-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="54970-110">Um único menu de atalho pode ser associado a vários controles, mas cada controle pode ter apenas um menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="54970-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="54970-111">A propriedade de chave de <xref:System.Windows.Forms.ContextMenu> componente é a <xref:System.Windows.Forms.Menu.MenuItems%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="54970-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="54970-112">Você pode adicionar itens de menu programaticamente criando <xref:System.Windows.Forms.MenuItem> objetos e adicioná-los para o <xref:System.Windows.Forms.Menu.MenuItemCollection> do menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="54970-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="54970-113">Como os itens em um menu de atalho geralmente são retirados de outros menus, você provavelmente adicionará itens ao menu de atalho copiando-os.</span><span class="sxs-lookup"><span data-stu-id="54970-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54970-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54970-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>