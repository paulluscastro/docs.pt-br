---
title: Message Security User Name
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: acf01818a697f2267307bdf7b9e469fec5741511
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-user-name"></a><span data-ttu-id="88eeb-102">Message Security User Name</span><span class="sxs-lookup"><span data-stu-id="88eeb-102">Message Security User Name</span></span>
<span data-ttu-id="88eeb-103">Este exemplo demonstra como implementar um aplicativo que usa o WS-Security com autenticação de nome de usuário para o cliente e requer a autenticação de servidor usando o certificado do servidor x. 509v3.</span><span class="sxs-lookup"><span data-stu-id="88eeb-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="88eeb-104">Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="88eeb-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="88eeb-105">Por padrão, o nome de usuário e a senha fornecidos pelo cliente são usados para fazer logon para uma conta válida do Windows.</span><span class="sxs-lookup"><span data-stu-id="88eeb-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="88eeb-106">Este exemplo se baseia o [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="88eeb-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="88eeb-107">Este exemplo consiste em um programa de console de cliente (Client.exe) e uma biblioteca de serviço (Service.dll) hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="88eeb-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="88eeb-108">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="88eeb-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88eeb-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="88eeb-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="88eeb-110">Este exemplo também demonstra:</span><span class="sxs-lookup"><span data-stu-id="88eeb-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="88eeb-111">O mapeamento padrão para contas do Windows para que a autorização adicional pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="88eeb-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="88eeb-112">Como acessar informações de identidade do chamador do código de serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="88eeb-113">O serviço expõe um ponto de extremidade de comunicação com o serviço, que é definido usando o arquivo de configuração Web. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="88eeb-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="88eeb-114">A associação está configurada com um padrão [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), que assume como padrão usando a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="88eeb-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="88eeb-115">Este exemplo define o padrão [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para usar a autenticação de nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="88eeb-116">O comportamento Especifica que as credenciais do usuário a ser usado para autenticação do serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="88eeb-117">O certificado do servidor deve conter o mesmo valor para o nome de entidade como o `findValue` atributo o [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="88eeb-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="88eeb-118">A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="88eeb-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="88eeb-119">A ligação do cliente é configurado com as `securityMode` e `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="88eeb-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="88eeb-120">Quando em execução em um cenário entre computadores, o endereço do ponto de extremidade de serviço deve ser alterado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="88eeb-121">A implementação de cliente define o nome de usuário e senha a ser usada.</span><span class="sxs-lookup"><span data-stu-id="88eeb-121">The client implementation sets the user name and password to use.</span></span>  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="88eeb-122">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="88eeb-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="88eeb-124">Arquivo em lotes bat incluído com os exemplos de MessageSecurity permite que você configure o servidor com um certificado apropriado para executar um aplicativo hospedado que exige a segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="88eeb-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="88eeb-125">O arquivo em lotes pode ser executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="88eeb-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="88eeb-126">Para executar o arquivo em lotes no modo único computador, digite `setup.bat` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="88eeb-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="88eeb-127">Para executá-lo no tipo de modo de serviço `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="88eeb-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="88eeb-128">Você usa este modo, ao executar a amostra entre computadores.</span><span class="sxs-lookup"><span data-stu-id="88eeb-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="88eeb-129">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="88eeb-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="88eeb-130">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote.</span><span class="sxs-lookup"><span data-stu-id="88eeb-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="88eeb-131">Criando o certificado do servidor</span><span class="sxs-lookup"><span data-stu-id="88eeb-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="88eeb-132">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="88eeb-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="88eeb-133">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="88eeb-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="88eeb-134">O certificado é armazenado no repositório de LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="88eeb-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="88eeb-135">Se o arquivo em lotes bat é executado com um argumento de serviço (como `setup.bat service`) % SERVER_NAME % contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="88eeb-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="88eeb-136">Caso contrário, o padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="88eeb-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="88eeb-137">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente</span><span class="sxs-lookup"><span data-stu-id="88eeb-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="88eeb-138">A linha a seguir copia o certificado do servidor para o armazenamento de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="88eeb-139">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="88eeb-140">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="88eeb-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="88eeb-141">Concedendo permissões de chave privada do certificado</span><span class="sxs-lookup"><span data-stu-id="88eeb-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="88eeb-142">As seguintes linhas no arquivo em lotes bat Verifique o certificado de servidor armazenado no repositório de LocalMachine acessível para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo do operador.</span><span class="sxs-lookup"><span data-stu-id="88eeb-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="88eeb-143">Se você estiver usando um fora dos EUA Edição em inglês do Windows, você deve editar o arquivo bat e substitui o `NT AUTHORITY\NETWORK SERVICE` nome da conta com seu equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="88eeb-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88eeb-144">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="88eeb-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="88eeb-145">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88eeb-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="88eeb-146">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88eeb-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="88eeb-147">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="88eeb-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="88eeb-148">Certifique-se de que o caminho inclui a pasta onde Makecert.exe e FindPrivateKey.exe estão localizados.</span><span class="sxs-lookup"><span data-stu-id="88eeb-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="88eeb-149">Execute bat da pasta de instalação de exemplo em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="88eeb-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="88eeb-150">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="88eeb-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88eeb-151">O arquivo em lotes bat foi projetado para ser executado a partir de um Prompt de comando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88eeb-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="88eeb-152">Isso requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="88eeb-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="88eeb-153">Essa variável de ambiente é definida automaticamente em um Prompt de comando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88eeb-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="88eeb-154">Verifique se o acesso ao serviço usando um navegador, digitando o endereço http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="88eeb-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="88eeb-155">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="88eeb-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="88eeb-156">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="88eeb-157">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="88eeb-157">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="88eeb-158">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="88eeb-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="88eeb-159">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-159">Create a directory on the service computer.</span></span> <span data-ttu-id="88eeb-160">Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="88eeb-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="88eeb-161">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="88eeb-162">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="88eeb-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="88eeb-163">Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="88eeb-164">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="88eeb-165">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="88eeb-166">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="88eeb-167">No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="88eeb-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="88eeb-168">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="88eeb-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="88eeb-169">Editar o Web. config para refletir o novo nome do certificado (o atributo findValue no elemento serviceCertificate) que é o mesmo que o nome de domínio totalmente qualificado do computador`.`</span><span class="sxs-lookup"><span data-stu-id="88eeb-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="88eeb-170">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="88eeb-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="88eeb-171">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="88eeb-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="88eeb-172">No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="88eeb-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="88eeb-173">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="88eeb-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="88eeb-174">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="88eeb-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="88eeb-175">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="88eeb-175">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="88eeb-176">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="88eeb-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="88eeb-177">Execute Cleanup.bat na pasta exemplos depois de terminar de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="88eeb-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88eeb-178">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="88eeb-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="88eeb-179">Se você tiver executado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="88eeb-179">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="88eeb-180">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="88eeb-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88eeb-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88eeb-181">See Also</span></span>