---
title: '&lt;NET. pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: c054cf0e4110051bb4a9ce49003fd0099b111c21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetpipegt"></a>&lt;NET. pipe&gt;
Especifica as configurações para o serviço de ativação de Pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e manipula solicitações de ativação que chegam através de pipes nomeados.  
  
 \<system.serviceModel.activation>  
\<NET. pipe >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maxPendingAccepts`|Um inteiro que especifica o máximo threads de aceitação simultâneas pendentes no ponto de extremidade escutando para o serviço de compartilhamento. O padrão é 2.|  
|`maxPendingConnections`|Um inteiro que especifica o número máximo de conexões que podem esperar por expedição. O padrão é 100.|  
|`receiveTimeout`|Um `TimeSpan` que especifica o tempo limite para ler os dados de enquadramento e executar a expedição de conexão das conexões sublinhado. O padrão é "00: 00:10"|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
