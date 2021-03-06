---
title: Exemplo de serviço de AJAX utilizando tipos complexos
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b821a252e202f0fef719e1545b38b4423237d0c7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-complex-types-sample"></a>Exemplo de serviço de AJAX utilizando tipos complexos
Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um serviço ASP.NET Asynchronous JavaScript e XML (AJAX) que cria instâncias de tipos complexos e envia-os entre o cliente como JSON JavaScript Object Notation () e de serviço. Você pode acessar um serviço de AJAX usando código JavaScript de um cliente de navegador da Web. Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de <xref:System.Web.UI.ScriptManager> controle. Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O serviço no exemplo a seguir está uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço sem nenhum código específico do AJAX. Porque o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("POST") é usado. O serviço tem uma operação, `DoMath`, que retorna um tipo complexo chamado `MathResult`. O tipo complexo é um tipo de contrato de dados padrão, que também não contém nenhum código específico do AJAX.  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 Crie um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como o exemplo de serviço AJAX básico.  
  
 O cliente ComplexTypeClientPage.aspx de página da Web contém código ASP.NET e JavaScript para invocar o serviço quando o usuário clica o **cálculos** botão na página. O código para chamar o serviço constrói um corpo JSON e a envia usando HTTP POST, semelhante do [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.  
  
 Após a chamada de serviço concluído com êxito, você pode acessar os membros de dados individuais (`sum`, `difference`, `product` e `quotient`) em JavaScript resultante do objeto.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução ComplexTypeAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (não abrir ComplexTypeClientPage.aspx no navegador do diretório do projeto).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Consulte também  
 [Serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
