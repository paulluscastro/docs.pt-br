---
title: "Como chamar um servi&#231;o Web de forma ass&#237;ncrona (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "chamadas assíncronas"
  - "Serviços Web, acessando"
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um servi&#231;o Web de forma ass&#237;ncrona (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo conecta um manipulador a um evento de manipulador assíncrono do serviço Web, para que ele possa recuperar o resultado de uma chamada de método assíncrono.  Este exemplo usou o serviço Web DemoTemperatureService em http:\/\/www.xmethods.  net.  
  
 Quando você faz referência a um serviço Web em seu projeto no Ambiente de Desenvolvimento Integrado \(IDE\) do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ele é adicionado ao objeto `My.WebServices` e o IDE gera uma classe proxy do cliente para acesso a um serviço Web especificado  
  
 A classe proxy permite chamar os métodos de serviço Web de forma síncrona, em que seu aplicativo aguarda até que a função seja concluída.  Além disso, o proxy cria membros adicionais para ajudar a chamar o método de forma assíncrona.  Para cada função de serviço Web, *NameOfWebServiceFunction*, o proxy cria uma sub\-rotina *NameOfWebServiceFunction*`Async`, um evento *NameOfWebServiceFunction*`Completed` e uma classe *NameOfWebServiceFunction*`CompletedEventArgs`.  Este exemplo demonstra como usar os membros assíncronos para acessar a função `getTemp` do serviço Web DemoTemperatureService.  
  
> [!NOTE]
>  Esse código não funciona em aplicativos Web, pois o ASP.NET não oferece suporte ao objeto `My.WebServices`.  
  
### Para chamar um serviço Web de forma assíncrona  
  
1.  Faça referência ao serviço Web DemoTemperatureService em http:\/\/www.xmethods.  net.  O endereço é  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Adicione um manipulador de eventos ao evento `getTempCompleted`:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Você não pode usar a instrução `Handles` para associar um manipulador de eventos aos eventos do objeto `My.WebServices`.  
  
3.  Adicione um campo para acompanhar se o manipulador de eventos tiver sido adicionado ao evento `getTempCompleted`:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Adicione um método para adicionar ao manipulador de eventos ao evento `getTempCompleted`, se necessário, e para chamar o método `getTempAsynch`:  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     Para chamar o método Web `getTemp` de forma assíncrona, chame o método `CallGetTempAsync`.  Quando o método Web for concluído, seu valor retornado será transmitido ao manipulador de eventos `getTempCompletedHandler`.  
  
## Consulte também  
 [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)   
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)