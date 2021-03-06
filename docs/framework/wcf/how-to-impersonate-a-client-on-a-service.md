---
title: Como personificar um cliente em um serviço
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 096a3dd1ae5035f6b015ec88ccd8f1ada1dc55ea
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Como personificar um cliente em um serviço
Representar um cliente em um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço permite que o serviço executar ações em nome do cliente. Para ações sujeitos a acesso (ACL) da lista de controle verifica, como acesso a diretórios e arquivos em um computador ou acesso a um banco de dados do SQL Server, a verificação ACL é em relação à conta de usuário do cliente. Este tópico mostra as etapas básicas necessárias para permitir que um cliente em um domínio do Windows definir um nível de representação do cliente. Para um exemplo de isso, consulte [representar o cliente](../../../docs/framework/wcf/samples/impersonating-the-client.md). Para obter mais informações sobre representação do cliente, consulte [delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Quando o cliente e o serviço estiverem em execução no mesmo computador e o cliente é executado sob uma conta de sistema (ou seja, `Local System` ou `Network Service`), o cliente não pode ser representado quando uma sessão segura é estabelecida com tokens de contexto de segurança com monitoração de estado. Um aplicativo de console ou WinForms normalmente é executado sob a conta conectada no momento, para que a conta pode ser representada por padrão. No entanto, quando o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página e que é hospedado no [!INCLUDE[iis601](../../../includes/iis601-md.md)] ou IIS 7.0 e, em seguida, o cliente é executado sob o `Network Service` conta por padrão. Todas as associações fornecidas pelo sistema que oferecem suporte a sessões seguras usam um token de contexto de segurança sem monitoração de estado por padrão. No entanto, se o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sessões seguras com tokens de contexto de segurança com monitoração de estado e página são usadas, o cliente não pode ser representado. Para obter mais informações sobre o uso de tokens de contexto de segurança com monitoração de estado em uma sessão segura, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Para habilitar a representação de um cliente de um token do Windows em cache em um serviço  
  
1.  Crie o serviço. Para obter um tutorial deste procedimento básico, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2.  Usar uma associação que usa a autenticação do Windows e cria uma sessão, como <xref:System.ServiceModel.NetTcpBinding> ou <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Ao criar a implementação da interface do serviço, se aplicam a <xref:System.ServiceModel.OperationBehaviorAttribute> classe para o método que requer a representação do cliente. Defina a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> como <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Para definir o nível de representação permitidos no cliente  
  
1.  Criar código de cliente de serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Para obter mais informações, consulte [Acessando serviços usando um cliente WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2.  Depois de criar o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente, definir o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade o <xref:System.ServiceModel.Security.WindowsClientCredential> classe para um do <xref:System.Security.Principal.TokenImpersonationLevel> valores de enumeração.  
  
    > [!NOTE]
    >  Para usar <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negociado a autenticação Kerberos (às vezes chamado de *multi-segmento* ou *várias etapas* Kerberos) deve ser usado. Para obter uma descrição de como implementar isso, consulte [práticas recomendadas de segurança](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [Representar o cliente](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
