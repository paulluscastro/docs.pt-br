---
title: "Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 330ee213e147cfef709c919c95cb0e58159bc37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] executado em uma área restrita de segurança de confiança parcial que é restrita ao conjunto de permissões da zona da Internet. Esse conjunto de permissões restringe as chamadas de serviço Web para apenas os serviços Web que estão localizados no site de origem do aplicativo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Quando um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é depurado do [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], no entanto, ele não é considerado como tendo o mesmo site de origem que o serviço Web que ele referencia. Isso faz com que exceções de segurança sejam geradas quando o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tenta chamar o serviço Web. No entanto, um projeto [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] pode ser configurado para simular o mesmo site de origem do serviço Web que ele chama durante a depuração. Isso permite que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] chame com segurança o serviço Web sem causar exceções de segurança.  
  
## <a name="configuring-visual-studio"></a>Configurando o Visual Studio  
 Para configurar [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] para depurar um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] que chama um serviço Web:  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  No **Designer de Projeto**, clique na guia **Depurar**.  
  
3.  Na seção **Iniciar Ação**, selecione **Iniciar programa externo** e insira o seguinte:  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  Na seção **Opções de inicialização**, digite o seguinte na caixa de texto **Argumentos da linha de comando**:  
  
     `-debug`  *nome de arquivo*  
  
     O valor *filename* para o parâmetro **-debug** é o nome do arquivo .xbap; por exemplo:  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  Essa é a configuração padrão para soluções criadas com o modelo de projeto [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)].  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  No **Designer de Projeto**, clique na guia **Depurar**.  
  
3.  Na seção **Opções de inicialização**, adicione o seguinte parâmetro de linha de comando para a caixa de texto **Argumentos de linha de comando**:  
  
     `-debugSecurityZoneURL`  *URL*  
  
     O valor da *URL* para o parâmetro **-debugSecurityZoneURL** é o [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] para o local que você deseja simular como sendo o site de origem do seu aplicativo.  
  
 Por exemplo, considere um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] que usa um serviço Web com o seguinte [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 O site de origem [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] para esse serviço Web é:  
  
 `http://services.msdn.microsoft.com`  
  
 Consequentemente, o parâmetro de linha de comando completo **-debugSecurityZoneURL** e seu valor é:  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>Consulte também  
 [Host do WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
