---
title: Como converter uma imagem BMP em uma imagem PNG
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee2669c41f4ee558d9457cee7df0ae8425cf065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Como converter uma imagem BMP em uma imagem PNG
Muitas vezes, você deve converter do formato de arquivo de uma imagem para outra. Você pode fazer essa conversão facilmente chamando o <xref:System.Drawing.Image.Save%2A> método o <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo da imagem desejada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um aplicativo Windows Forms.  
  
-   Uma referência para o `System.Drawing.Imaging` namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Como Listar os Codificadores Instalados](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [Tipos de Bitmaps](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
