---
title: '&lt;httpWebRequest&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d1dce38e5188824ba1412d3f2a285bd2304f147
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt; elemento (configurações de rede)
Personaliza os parâmetros de solicitação da Web.  
  
 \<configuration>  
\<system.net>  
\<Configurações >  
\<httpWebRequest >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Especifica o comprimento máximo de um cabeçalho de resposta, em quilobytes. O padrão é 64. Um valor de -1 indica que não há limite de tamanho será imposto os cabeçalhos de resposta.|  
|`maximumErrorResponseLength`|Especifica o comprimento máximo de uma resposta de erro, em quilobytes. O padrão é 64. Um valor de -1 indica que não há limite de tamanho será imposto a resposta de erro.|  
|`maximumUnauthorizedUploadLength`|Especifica o comprimento máximo de um carregamento em resposta a um código de erro não autorizado, em bytes. O padrão é -1. Um valor de -1 indica que não há limite de tamanho será imposto sobre o carregamento.|  
|`useUnsafeHeaderParsing`|Especifica se a análise de cabeçalho não seguro está habilitada. O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o .NET Framework estritamente impõe RFC 2616 para análise do URI. Algumas respostas do servidor podem incluir caracteres de controle em campos proibidos, o que fará com que o <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> método para lançar um <xref:System.Net.WebException>. Se **useUnsafeHeaderParsing** é definido como **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> não lançará nesse caso; no entanto, seu aplicativo estará vulnerável a várias formas de ataques de análise de URI. A melhor solução é alterar o servidor de modo que a resposta não inclui caracteres de controle.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar uma maior que o tamanho máximo do cabeçalho normal.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
