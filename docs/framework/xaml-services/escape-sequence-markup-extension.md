---
title: "Sequência de escape {} - extensão de marcação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>Sequência de escape {}/extensão de marcação
Fornece a sequência de escape XAML para valores de atributo. A sequência de escape permite que os valores subsequentes no atributo sejam interpretados como um literal.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Uso do elemento propriedade XAML  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*literalValue*|A cadeia de caracteres literal que segue a sequência de escape. Normalmente, essa cadeia de caracteres contém uma chave de abertura ou fechamento ({ou}).|  
  
## <a name="remarks"></a>Comentários  
 A sequência de escape ({}) é usada para que uma chave de abertura ({}) pode ser usada como um caractere literal em XAML.  
  
 Leitores XAML normalmente usam a chave de abertura ({}) para indicar o ponto de entrada de uma extensão de marcação; no entanto, eles primeiro verifique o próximo caractere para determinar se ele é uma chave de fechamento (}). Somente quando as duas chaves ({}) são adjacentes, eles são considerados uma sequência de escape.  
  
 Se a sequência de escape for encontrada, o leitor XAML deve processar o restante da cadeia de caracteres como uma cadeia de caracteres. No entanto, se a sequência de escape é aplicada a um membro que tem um conversor de tipo, a cadeia de caracteres pode passar por conversão de tipo quando ele é interpretado por um autor XAML.  
  
 A sequência de escape não é uma extensão de marcação e não é feita por uma classe. No entanto, é uma convenção que devem respeitar leitores XAML (incluindo leitores XAML personalizados).  
  
 Aspas (") não pode ser usada como uma sequência de escape dessa maneira. Se você precisar definir aspas como um valor de propriedade para uma propriedade não-conteúdo, usar a sintaxe de elemento de propriedade e coloque as aspas como uma cadeia de caracteres dentro do elemento de propriedade ou usar uma entidade de caracteres XML. Para uma propriedade de conteúdo, as aspas podem ser todo o conteúdo.  
  
 A sequência de escape ({}) é frequentemente necessária ao especificar um tipo XML que deve incluir um qualificador de namespace em um local onde uma extensão de marcação XAML pode aparecer. Isso inclui o início de um valor de atributo XAML e em uma extensão de marcação, imediatamente após o sinal de igual (=). O exemplo a seguir mostra as sequências de escape para um namespace XML que aparece no início de um valor de atributo XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Consulte também  
 [Conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Entidades e XAML de caractere XML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
