---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: a93474a4f86fac2a6b211652e3ddc86901cf197f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbindingelementextensionsgt"></a>&lt;bindingElementExtensions&gt;
Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo. Você pode adicionar um elemento de associação personalizada para esta coleção usando o `add` palavra-chave e a configuração a `type` atributo do elemento para uma extensão de elemento de associação, bem como a `name` de atributo para o elemento de associação personalizada.  
  
 Extensões de associação permitem que o usuário criar elementos de associação definida pelo usuário para uso como parte de associações personalizadas. Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.BindingElement>. No arquivo de configuração, o `bindingElementExtensions` seção é usada para definir um elemento de extensão.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Para adicionar recursos de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingElementExtensionSection` elemento. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma associação personalizada, conforme mostrado no exemplo a seguir.  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
