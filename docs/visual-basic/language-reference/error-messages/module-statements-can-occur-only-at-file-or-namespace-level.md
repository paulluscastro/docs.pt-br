---
title: '&#39; Módulo &#39; instruções só podem ocorrer no nível de namespace ou arquivo'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39; Módulo &#39; instruções só podem ocorrer no nível de namespace ou arquivo
`Module`instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.  
  
 **ID do erro:** BC30617  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Module` à parte superior do seu arquivo de origem ou de declaração de namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
