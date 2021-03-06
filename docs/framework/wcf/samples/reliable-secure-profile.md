---
title: "Perfil seguro confiável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 89a6d5c2e485699a55c77797c34eaca2c9848c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-secure-profile"></a>Perfil seguro confiável
Este exemplo demonstra como compor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [confiável perfil seguro](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Este exemplo demonstra a implementação de um [fazer Conexão](http://go.microsoft.com/fwlink/?LinkId=178141) canal que pode ser composto em conjunto com o sistema de mensagens confiável e, opcionalmente, um canal seguro para criar uma associação segura confiável com base na especificação RSP.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra um cenário de troca confiável de mensagens assíncronas bidirecional. O serviço tem um contrato duplex e o cliente implementa o contrato de retorno de chamada dúplex. O cliente inicia uma solicitação para um serviço, para que uma resposta é esperada em uma conexão separada. A mensagem de solicitação é enviada de forma confiável. O cliente não deseja abrir um ponto de extremidade de escutando seu final. Portanto, ele pesquisa o serviço com solicitações de 'Fazer Conexão' para o serviço enviar a resposta de volta no canal de retorno dessa solicitação de 'Fazer Conexão'. Este exemplo demonstra como ter comunicação duplex confiável segura via HTTP sem o cliente expor um ponto de extremidade de escutando (e criar uma exceção de firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **ReliableSecureProfile** solução.  
  
2.  Clique com botão direito do **Service** project no **Solution Explorer**, selecione **depurar**, **iniciar nova instância** no menu de contexto. Isso inicia o host de serviço.  
  
3.  Clique com botão direito do **cliente** project no **Solution Explorer**, selecione **depurar**, **iniciar nova instância** no menu de contexto. Isso inicia o backup do cliente.  
  
4.  Digite qualquer cadeia de caracteres no aviso na janela do console de cliente e clique em ENTER. Envia a cadeia de caracteres de entrada para o serviço, que calcula um hash da cadeia de caracteres.  
  
5.  Exiba o resultado no cliente windows quando o serviço de volta chama a operação do contrato de retorno de chamada duplex para exibir o resultado na janela do console de cliente. Há um atraso intencional no serviço para simular uma operação de longa execução do processamento de dados.  
  
6.  Monitorando o tráfego HTTP (por qualquer uma das ferramentas como o Monitor de rede, Fiddler e assim por diante de monitoramento de rede online) mostra que uma sequência para a comunicação é estabelecida entre o cliente e o serviço como dispostos pelo perfil seguro confiável e como o cliente sonda o serviço com solicitações de 'Fazer Conexão'. Quando o serviço obtém pronto para enviar de volta a resposta processada, ele usa o canal de retorno da última solicitação de 'Fazer Conexão' para enviar os resultados de volta.  
  
7.  Pressione ENTER na janela do console de serviço para fechar o serviço. Pressione ENTER na janela do console de cliente para fechar o cliente.
