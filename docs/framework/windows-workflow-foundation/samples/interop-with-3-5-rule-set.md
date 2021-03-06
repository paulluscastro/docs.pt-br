---
title: Interoperabilidade com conjunto de regras 3,5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854aeac936d3f911f2613c6e315ab81347f64a25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="interop-with-35-rule-set"></a>Interoperabilidade com conjunto de regras 3,5
Este exemplo demonstra o uso do <xref:System.Activities.Statements.Interop> atividade integrar uma atividade personalizada no [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] usando <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` e regras. Passar dados para a atividade personalizado associando variáveis de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] às propriedades de dependência exposta pela atividade personalizado.  
  
## <a name="requirements"></a>Requisitos  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.Activities.Statements.Interop>atividade, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` atividade em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] com propriedades de dependência  
  
## <a name="discussion"></a>Discussão  
 O exemplo demonstra um dos cenários de integração para integrar uma atividade de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] . Este exemplo inclui uma [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] atividade personalizada que invoca um <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` atividade.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Abrindo TravelRuleSet.cs no designer mostra uma atividade sequencial personalizado que contém uma atividade de política como segue  
  
 ![Atividade de interoperabilidade](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Clique duas vezes o **DiscountPolicy** atividade de política para examinar as regras. O editor das regras aparece para mostrar as regras.  
  
 ![Editor de conjunto de regras](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Clique com botão direito do **DiscountPolicy** atividade e selecione o **Exibir código** opção para examinar ao lado do código c# código que acompanha esta atividade. Observe a configuração da propriedade de dependência para `DiscountLevel`. Isso é equivalente a <xref:System.Activities.Argument> em [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Este é um projeto de fluxo de trabalho sequencial de [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar com o conjunto de regra personalizada criado no projeto de TravelRuleLibrary. As variáveis são criados em <xref:System.Activities.Statements.Sequence> de nível superior como segue.  
  
 ![Variáveis](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Gerenciador de soluções](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Finalmente, a atividade de <xref:System.Activities.Statements.Interop> é usada para integrar com o TravelRuleSet. Variáveis que foram declarados anteriores em <xref:System.Activities.Statements.Sequence> são usados para associar a propriedades de dependência.  
  
 ![Tipo de atividade](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![Seta](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Propriedades](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
