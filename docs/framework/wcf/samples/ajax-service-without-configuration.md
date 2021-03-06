---
title: Serviço AJAX sem configuração
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae16dc38c5508eac4a94d464e818f0b97d3b9e3b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-without-configuration"></a>Serviço AJAX sem configuração
Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um básico ASP.NET Asynchronous JavaScript e XML (AJAX) serviço (um serviço que você pode acessar por meio de código JavaScript de um cliente de navegador da Web) sem usar as definições de configuração. O serviço usa a sintaxe especial no arquivo. svc para ativar automaticamente um ponto de extremidade AJAX.  
  
 Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [Ajax exemplos](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo tem como base o AJAX Service usando HTTP POST. Conforme descrito no [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> para o serviço. Se nenhuma alteração na configuração precisa ser feitas para o ponto de extremidade, o `<system.ServiceModel>` seção pode ser completamente removida do arquivo Web. config para o serviço. O arquivo Web. config contém algumas configurações do ASP.NET, que são usadas pelo ConfigFreeClientPage.aspx. Se não fosse esse o caso, todo o arquivo Web. config foi removido.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você execute as instruções de instalação em [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução ConfigFreeAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (não abrir ConfigFreeClientPage.aspx no navegador de dentro do diretório do projeto).  
  
> [!NOTE]
>  Ao executar este exemplo, certifique-se de que a autenticação anônima e autenticação do Windows não estão habilitados simultaneamente para a pasta ServiceModelSamples no IIS. Se esse for o caso, desative a autenticação do Windows. Depois de executar o exemplo, habilitar a autenticação do Windows e execute "iisreset".  
  
## <a name="see-also"></a>Consulte também  
 [Serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
