---
title: "Sessão confiável de associação personalizada através de HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dfd417bc04bcbcabda70618aff9db3605556b068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="2a22f-102">Sessão confiável de associação personalizada através de HTTPS</span><span class="sxs-lookup"><span data-stu-id="2a22f-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="2a22f-103">Este exemplo demonstra o uso da segurança de transporte SSL com sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2a22f-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="2a22f-104">Sessões confiáveis implementa o protocolo WS-confiável de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2a22f-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="2a22f-105">Você pode ter uma sessão confiável segura ao compor o WS-Security sobre sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2a22f-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="2a22f-106">Mas, às vezes, você pode optar por usar em vez disso, a segurança de transporte HTTP com SSL.</span><span class="sxs-lookup"><span data-stu-id="2a22f-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a22f-107">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2a22f-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a22f-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2a22f-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2a22f-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2a22f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a22f-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2a22f-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="2a22f-111">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="2a22f-111">Sample Details</span></span>  
 <span data-ttu-id="2a22f-112">SSL garante que os pacotes em si são protegidos.</span><span class="sxs-lookup"><span data-stu-id="2a22f-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="2a22f-113">É importante observar que isso é diferente de proteger a sessão confiável usando o WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="2a22f-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="2a22f-114">Para usar a sessão confiável via HTTPS, você deve criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2a22f-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="2a22f-115">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="2a22f-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2a22f-116">Uma associação personalizada é criada usando o elemento de associação de sessão confiável e o [ \<httpsTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="2a22f-117">É a seguinte configuração da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2a22f-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="2a22f-118">O código do programa no exemplo é idêntico do [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) serviço.</span><span class="sxs-lookup"><span data-stu-id="2a22f-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="2a22f-119">Você deve criar um certificado e atribuí-lo usando o Assistente de certificado de servidor da Web antes de criar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2a22f-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="2a22f-120">A definição de ponto de extremidade e a definição de associação nas configurações do arquivo de configuração permitem o uso de associação personalizada, conforme mostrado no seguinte exemplo de configuração para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2a22f-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"   
                binding="customBinding"   
                bindingConfiguration="reliableSessionOverHttps"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>        
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="2a22f-121">O endereço especificado usa o esquema de https://.</span><span class="sxs-lookup"><span data-stu-id="2a22f-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="2a22f-122">Como o certificado usado neste exemplo é um certificado de teste criado com o Makecert.exe, um alerta de segurança é exibida quando você tentar acessar um https: endereço, como https://localhost/servicemodelsamples/service.svc do seu navegador.</span><span class="sxs-lookup"><span data-stu-id="2a22f-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="2a22f-123">Para permitir que o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente para trabalhar com um certificado de teste no lugar, foi adicionado um código adicional para o cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="2a22f-123">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="2a22f-124">Esse código e a classe que o acompanha, não é necessário ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="2a22f-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  
  
```  
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="2a22f-125">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2a22f-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2a22f-126">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2a22f-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2a22f-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2a22f-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2a22f-128">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a22f-128">Install  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="2a22f-129">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="2a22f-130">Certifique-se de que você executou o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="2a22f-131">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="2a22f-132">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a22f-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a22f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a22f-133">See Also</span></span>