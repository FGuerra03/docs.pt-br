---
title: '&lt;Adicionar&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a>\<Adicionar > elemento \<appSettings >

Adiciona uma configuração de aplicativo personalizado.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Adicionar >**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Atributos

|           | Descrição |
| --------- | ----------- |
| **key**   | Atributo obrigatório.<br><br>Especifica o nome da chave para adicionar. |
| **value** | Atributo obrigatório.<br><br>Especifica o valor da chave para adicionar. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como adicionar uma configuração personalizada para o nome do aplicativo:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)