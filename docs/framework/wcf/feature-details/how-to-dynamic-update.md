---
title: Como atualizar dinamicamente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 748286b4f6fa22b23423ff5c176c76d11fbe742d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamic-update"></a>Como atualizar dinamicamente
Este tópico descreve as etapas básicas necessárias para criar e atualizar dinamicamente a configuração de roteamento. Neste exemplo, a configuração de roteamento inicial é obtida do arquivo de configuração e encaminha todas as mensagens para o serviço da Calculadora regularCalc; No entanto, ele é subsequentemente atualizado por meio de programação para alterar o ponto de extremidade de destino o serviço roundingCalc.  
  
> [!NOTE]
>  Em muitas implementações, a configuração será totalmente dinâmica e não irá contar com uma configuração padrão; No entanto, há alguns cenários, como aquele neste tópico, em que é desejável ter um estado de configuração padrão quando o serviço é iniciado.  
  
> [!NOTE]
>  Atualizações dinâmicas ocorrerem apenas na memória e não resultam na modificação de arquivos de configuração.  
  
 RegularCalc e roundingCalc suportam as mesmas operações de adicionar, subtrair, multiplicar e dividem; No entanto, roundingCalc Arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar. Um arquivo de configuração é usado para configurar o serviço para rotear todas as mensagens para o serviço regularCalc. Depois que o serviço de roteamento foi iniciado, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> é usado para reconfigurar o serviço para rotear mensagens para o serviço roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implementar a configuração inicial  
  
1.  Crie a configuração básica do serviço de roteamento, especificando os pontos de extremidade do serviço expostos pelo serviço. O exemplo a seguir define um ponto de extremidade de serviço único, que será usado para receber mensagens. Ele também define um ponto de extremidade do cliente que será usado para enviar mensagens para o regularCalc.  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2.  Defina o filtro usado para rotear mensagens para os pontos de extremidade de destino. Neste exemplo, o filtro de MatchAll é usado para rotear todas as mensagens para o regularCalcEndpoint definida anteriormente. O exemplo a seguir define o filtro e a tabela de filtro.  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3.  Para avaliar as mensagens de entrada com os filtros contidos na tabela de filtro, você deve associar a tabela de filtro com os pontos de extremidade de serviço usando o comportamento de roteamento. O exemplo a seguir demonstra a associação "filterTable1" com o ponto de extremidade de serviço.  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a>Implementar a configuração dinâmica  
 Configuração dinâmica do serviço de roteamento só pode ser executada no código, criando um novo <xref:System.ServiceModel.Routing.RoutingConfiguration> e usando <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> para substituir a configuração atual.  Neste exemplo, o serviço de roteamento é hospedado automaticamente dentro de um aplicativo de console. Depois que o aplicativo foi iniciado, você pode modificar a configuração de roteamento inserindo 'regular' ou 'arredondamento' na janela do console para configurar o ponto de extremidade de destino que as mensagens são roteadas. regularCalc quando 'regular' é inserido, caso contrário roundingCalc quando 'arredondamento' é inserido.  
  
1.  O seguinte usando instruções deve ser adicionado para oferecer suporte ao serviço de roteamento.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  O código a seguir é usado para hospedar automaticamente o serviço de roteamento de mensagens como um aplicativo de console. Isso inicia o serviço de roteamento usando a configuração descrita na etapa anterior, que está contida no arquivo de configuração do aplicativo. While loop contém o código usado para alterar a configuração de roteamento.  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners           
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3.  Para atualizar dinamicamente a configuração de roteamento, uma nova configuração de roteamento deve ser criada. Isso deve conter todos os pontos de extremidade, filtros e filtrar tabelas que são necessárias para a nova configuração de roteamento, como completamente, ela substituirá a configuração de roteamento existente. Para usar a nova configuração de roteamento, você deve chamar <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> e passar a nova configuração.  
  
     Adicione o seguinte código para while loop definida anteriormente para permitir que o serviço ser reconfigurados com base na entrada do usuário.  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    >  Como o método para fornecer uma nova RoutingConfiguration está contida na extensão de serviço do RoutingExtension, nova RoutingConfiguration objetos podem ser fornecidos em qualquer lugar no modelo de extensibilidade do WCF ou pode obter uma referência ao ServiceHost ou ServiceExtensions (como em outro ServiceExtension). Para obter um exemplo de atualização dinâmica de RoutingConfiguration dessa maneira, consulte [reconfiguração dinâmica](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).  
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa do aplicativo de console usado neste exemplo.  
  
```  
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {             
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners           
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa da configuração do arquivo usado neste exemplo.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de roteamento](../../../../docs/framework/wcf/samples/routing-services.md)
