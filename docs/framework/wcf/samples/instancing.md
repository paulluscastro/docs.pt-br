---
title: "Instanciação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b38d70a4f4c3938d6cc6116c94a009ec0f34dc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="instancing"></a><span data-ttu-id="5cb64-102">Instanciação</span><span class="sxs-lookup"><span data-stu-id="5cb64-102">Instancing</span></span>
<span data-ttu-id="5cb64-103">O exemplo de Instancing demonstra a configuração de comportamento de instância, que controla como as instâncias de uma classe de serviço são criadas em resposta a solicitações de cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="5cb64-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5cb64-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5cb64-105">Este exemplo define um novo contrato, `ICalculatorInstance`, que herda de `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="5cb64-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="5cb64-106">O contrato especificado pelo `ICalculatorInstance` fornece três operações adicionais para inspecionar o estado da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="5cb64-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="5cb64-107">Alterando a configuração de instância, você pode observar a alteração no comportamento executando o cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="5cb64-108">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5cb64-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cb64-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5cb64-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5cb64-110">Os seguintes modos de instância estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="5cb64-110">The following instancing modes are available:</span></span>  
  
-   <span data-ttu-id="5cb64-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Uma nova instância de serviço é criada para cada solicitação de cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
-   <span data-ttu-id="5cb64-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Uma nova instância é criada para cada nova sessão de cliente e mantida pela duração da sessão (requer uma associação que dá suporte à sessão).</span><span class="sxs-lookup"><span data-stu-id="5cb64-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
-   <span data-ttu-id="5cb64-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Uma única instância da classe de serviço manipula todas as solicitações de cliente para o tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5cb64-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="5cb64-114">A classe de serviço Especifica o comportamento de instância com o `[ServiceBehavior(InstanceContextMode=<setting>)]` atributo conforme mostrado no exemplo de código que segue.</span><span class="sxs-lookup"><span data-stu-id="5cb64-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="5cb64-115">Alterando as linhas que são comentadas, você pode observar o comportamento de cada um dos modos de instância.</span><span class="sxs-lookup"><span data-stu-id="5cb64-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="5cb64-116">Lembre-se recriar o serviço depois de alterar o modo de instanciamento.</span><span class="sxs-lookup"><span data-stu-id="5cb64-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="5cb64-117">Há nenhuma configuração de instância relacionados para especificar no cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="5cb64-118">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5cb64-119">O serviço está em execução sob o modo de instância é exibido.</span><span class="sxs-lookup"><span data-stu-id="5cb64-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="5cb64-120">Depois de cada operação, a contagem de ID e a operação de instância são exibidas para refletir o comportamento do modo de instanciamento.</span><span class="sxs-lookup"><span data-stu-id="5cb64-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="5cb64-121">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5cb64-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5cb64-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5cb64-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5cb64-123">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cb64-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5cb64-124">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cb64-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5cb64-125">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cb64-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5cb64-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5cb64-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5cb64-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5cb64-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5cb64-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5cb64-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5cb64-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5cb64-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a><span data-ttu-id="5cb64-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cb64-130">See Also</span></span>