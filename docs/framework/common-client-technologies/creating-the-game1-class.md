---
title: Criando a classe Game1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7453c4f650e2dcadd3b8fac27b66f4db97fa0136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-game1-class"></a>Criando a classe Game1
Como com todos os projetos de Microsoft XNA, a classe Game1 é derivada da classe [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx), que fornece a inicialização do dispositivo de gráficos básicos, lógica de jogo e processamento de código para jogos XNA. A classe Game1 é bastante simples, pois a maioria do trabalho é realizado nas classes GamePiece e GamePieceCollection.  
  
## <a name="creating-the-code"></a>Criando o código  
 Os membros particulares da classe consistem em um objeto **GamePieceCollection** para conter as partes do jogo, um objeto [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) e um objeto [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) usado para renderizar as partes do jogo.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Durante a inicialização do jogo, esses objetos são instanciados.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Quando o método [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) é chamado, as partes do jogo são criadas e atribuídas ao objeto **GamePieceCollection**. Existem dois tipos de partes do jogo. A escala das partes é ligeiramente alterada para permitir partes menores e maiores.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 O método [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) é chamado repetidamente com o XNA Framework durante a execução do jogo. O método [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) chama os métodos **ProcessInertia** e **UpdateFromMouse** na coleção de partes do jogo. Esses métodos são descritos em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 O método [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) também é chamado repetidamente pelo XNA Framework durante a execução do jogo. O método [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) realiza a renderização das partes do jogo chamando o método **Draw** do objeto **GamePieceCollection**. Esses método é descrito em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Consulte também  
 [Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Uso de manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Criação da classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Criação da classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listagens de códigos completas](../../../docs/framework/common-client-technologies/full-code-listings.md)
