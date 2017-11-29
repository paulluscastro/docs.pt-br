---
title: Construindo e desenhando curvas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 801af10f7b9e5e7998fc061537977c5bced6bdb3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="d37c2-102">Construindo e desenhando curvas</span><span class="sxs-lookup"><span data-stu-id="d37c2-102">Constructing and Drawing Curves</span></span>
<span data-ttu-id="d37c2-103">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dá suporte a vários tipos de curvas: elipses, arcos, splines cardinais e splines de Bézier.</span><span class="sxs-lookup"><span data-stu-id="d37c2-103">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="d37c2-104">Uma elipse é definida por seu retângulo delimitador; um arco é uma parte de uma elipse definida por um ângulo inicial e um ângulo de flecha.</span><span class="sxs-lookup"><span data-stu-id="d37c2-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="d37c2-105">Um spline cardinal é definido por uma matriz de pontos e um parâmetro de tensão – a curva passa suavemente por cada ponto na matriz e o parâmetro de tensão influencia a maneira como a curva se dobra.</span><span class="sxs-lookup"><span data-stu-id="d37c2-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="d37c2-106">Um spline de Bézier é definido por dois pontos de extremidade e dois pontos de controle. A curva não passa pelos pontos de controle, mas os pontos de controle influenciam a direção e dobram conforme a curva passa de um ponto de extremidade para o outro.</span><span class="sxs-lookup"><span data-stu-id="d37c2-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d37c2-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d37c2-107">In This Section</span></span>  
 [<span data-ttu-id="d37c2-108">Como Desenhar Splines Cardinais</span><span class="sxs-lookup"><span data-stu-id="d37c2-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="d37c2-109">Descreve splines cardinais e como desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="d37c2-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="d37c2-110">Como Desenhar um Único Spline de Bézier</span><span class="sxs-lookup"><span data-stu-id="d37c2-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="d37c2-111">Descreve um spline de Bézier e como desenhá-lo.</span><span class="sxs-lookup"><span data-stu-id="d37c2-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="d37c2-112">Como Desenhar uma Sequência de Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="d37c2-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="d37c2-113">Explica como desenhar vários splines de Bézier em sequência.</span><span class="sxs-lookup"><span data-stu-id="d37c2-113">Explains how to draw several Bézier splines in sequence.</span></span>