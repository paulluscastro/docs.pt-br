---
title: "Referência de assembly Friend &lt;referência&gt; é inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Referência de assembly Friend &lt;referência&gt; é inválido
Referência de assembly Friend \<referência > é inválido. O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.  
  
 **ID do erro:** BC31535  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine a chave pública do assembly friend com nome forte. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName>  
 [Assemblies Amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

