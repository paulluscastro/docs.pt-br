---
title: Atividade personalizado para iniciar um intervalo de valores
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13c409865846acdf7b557c20330f9a2fd62d47d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Atividade personalizado para iniciar um intervalo de valores
Este exemplo demonstra como criar uma atividade personalizado que estende o uso de <xref:System.Activities.Statements.Switch%601>. Uma declaração convencional de <xref:System.Activities.Statements.Switch%601> permite alternar baseado em um único valor. Mas, há situações onde comerciais uma atividade deve alternar baseado em um intervalo de valores. Por exemplo, uma atividade pode executar uma ação quando o valor que está sendo alternado na está entre 1 e 5, outra ação quando o valor está entre 6 e 10, e uma ação padrão para todos os outros valores. Esta atividade personalizado permite exatamente esse cenário.  
  
## <a name="the-switchrange-activity"></a>A atividade de SwitchRange  
 As agendas de atividade de `SwitchRange` uma atividade filho quando o valor do resultado da expressão é incluído dentro do intervalo de um do seu `Cases`.  
  
 O exemplo de código é uma atividade personalizado que alterne baseado em um intervalo de valores.  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|Propriedade|Descrição|  
|-|-|  
|Expressão|Esta é a expressão a ser avaliada e comparado com os intervalos na lista select case. O resultado da expressão é do tipo T.|  
|Casos|Cada caso consistem em um intervalo (e) e uma atividade (corpo). A expressão é avaliada e comparada com os intervalos. Se o resultado da expressão está dentro do intervalo de uma dos casos, a atividade correspondente é executada.|  
|Padrão|A atividade que é executado quando nenhum caso for correspondente. Quando definida como `null`, nenhuma ação é executada.|  
  
## <a name="caserange-class"></a>Classe de CaseRange  
 A classe de `CaseRange` representa um intervalo dentro de uma atividade de `SwitchRange` . Cada instância de `CaseRange` contém um intervalo (composta de `From` e de `To`) e uma atividade de `Body` que está agendada se a expressão é avaliada em `SwitchRange` dentro do intervalo.  
  
 O exemplo de código é a definição da classe de `CaseRange` .  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  As classes de `SwitchRange` e de `CaseRange` , que são definidas no exemplo são as classes genéricas que podem trabalhar com qualquer tipo que implementa `IComparable`, como a classe de <xref:System.Activities.Statements.Switch%601> .  
  
## <a name="sample-usage"></a>Uso de exemplo  
 O exemplo de código demonstra como usar a atividade de `SwitchRange` .  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de SwitchRange.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`