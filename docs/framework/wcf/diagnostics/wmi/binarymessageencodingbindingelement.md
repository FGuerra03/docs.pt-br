---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adac65808853ec75e37245c8c9fa031a533c22a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe BinaryMessageEncodingBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.  
  
## <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.  
  
## <a name="maxsessionsize"></a>maxSessionSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.  
  
## <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Tipo de dados: XmlDictionaryReaderQuotas  
  
 Tipo de acesso: somente leitura  
  
 As cotas dos leitores.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
