---
title: Como inspecionar ou modificar mensagens no cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 164e19891e576b6d310839a1221ad8ed0d315444
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="0097e-102">Como inspecionar ou modificar mensagens no cliente</span><span class="sxs-lookup"><span data-stu-id="0097e-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="0097e-103">Você pode inspecionar ou modificar as mensagens de entrada ou saídas em uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente implementando um <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> e inseri-lo no tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="0097e-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="0097e-104">Para obter mais informações, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0097e-104">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="0097e-105">O recurso equivalente do serviço é o <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0097e-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0097e-106">Para obter um exemplo de código completo, consulte o [inspetores de mensagem](../../../../docs/framework/wcf/samples/message-inspectors.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="0097e-106">For a complete code example see the [Message Inspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="0097e-107">Para inspecionar ou modificar as mensagens</span><span class="sxs-lookup"><span data-stu-id="0097e-107">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="0097e-108">Implementar a interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0097e-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="0097e-109">Implementar um <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> dependendo do escopo no qual você deseja inserir o Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="0097e-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="0097e-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>permite que você altere o comportamento no nível do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0097e-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="0097e-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>permite que você altere o comportamento no nível do contrato.</span><span class="sxs-lookup"><span data-stu-id="0097e-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3.  <span data-ttu-id="0097e-112">Inserir o comportamento antes de chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método sobre o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0097e-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0097e-113">Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="0097e-113">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0097e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0097e-114">Example</span></span>  
 <span data-ttu-id="0097e-115">Os exemplos de código a seguir mostram, em ordem:</span><span class="sxs-lookup"><span data-stu-id="0097e-115">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="0097e-116">Uma implementação de Inspetor de cliente.</span><span class="sxs-lookup"><span data-stu-id="0097e-116">A client inspector implementation.</span></span>  
  
-   <span data-ttu-id="0097e-117">Um comportamento de ponto de extremidade que insere o Inspetor.</span><span class="sxs-lookup"><span data-stu-id="0097e-117">An endpoint behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="0097e-118">Um <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-derivada da classe que permite que você adicionar o comportamento de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0097e-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
-   <span data-ttu-id="0097e-119">Um arquivo de configuração que adiciona o comportamento de ponto de extremidade que insere o Inspetor de mensagem do cliente em tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="0097e-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"  
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0097e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0097e-120">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="0097e-121">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="0097e-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)