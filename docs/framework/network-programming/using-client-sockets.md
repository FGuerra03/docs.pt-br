---
title: Usando soquetes de cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 25c033ae46abc65040c00b6beb105c8ebb6b1d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-client-sockets"></a>Usando soquetes de cliente
Antes de iniciar uma conversa por meio de um <xref:System.Net.Sockets.Socket>, crie um pipe de dados entre o aplicativo e o dispositivo remoto. Embora existam outros protocolos e famílias de endereços de rede, este exemplo mostra como criar uma conexão TCP/IP com um serviço remoto.  
  
 O TCP/IP usa um endereço de rede e um número da porta de serviço para identificar um serviço exclusivamente. O endereço de rede identifica um dispositivo específico na rede; o número da porta identifica o serviço específico nesse dispositivo ao qual se conectar. A combinação do endereço de rede e da porta de serviço é chamada de um ponto de extremidade, que é representado no .NET Framework pela classe <xref:System.Net.EndPoint>. Um descendente de **EndPoint** está definido para cada família de endereços com suporte; para a família de endereços IP, a classe é <xref:System.Net.IPEndPoint>.  
  
 A classe <xref:System.Net.Dns> fornece serviços de nome de domínio para aplicativos que usam os serviços TCP/IP da Internet. O método <xref:System.Net.Dns.Resolve%2A> consulta um servidor DNS para mapear um nome de domínio amigável (como “host.contoso.com”) para um endereço numérico na Internet (por exemplo, 192.168.1.1). **Resolve** retorna um <xref:System.Net.IPHostEntry> que contém uma lista de endereços e aliases para o nome solicitado. Na maioria dos casos, é possível usar o primeiro endereço retornado na matriz <xref:System.Net.IPHostEntry.AddressList%2A>. O código a seguir obtém um <xref:System.Net.IPAddress> que contém o endereço IP do servidor host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (para obter mais informações, consulte www.iana.org/assignments/port-numbers). Outros serviços podem ter números de porta registrados no intervalo de 1.024 a 65.535. O código a seguir combina o endereço IP de host.contoso.com com um número da porta para criar um ponto de extremidade remoto para uma conexão.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Depois de determinar o endereço do dispositivo remoto e escolher uma porta a ser usada para a conexão, o aplicativo pode tentar estabelecer uma conexão com o dispositivo remoto. O exemplo a seguir usa um **IPEndPoint** existente para se conectar a um dispositivo remoto e captura todas as exceções geradas.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando um soquete de cliente síncrono](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Usando um soquete de cliente assíncrono](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Como criar um soquete](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Soquetes](../../../docs/framework/network-programming/sockets.md)
