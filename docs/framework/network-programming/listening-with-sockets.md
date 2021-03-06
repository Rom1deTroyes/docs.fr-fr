---
title: écoute avec des sockets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 640caf57638acae9bbe39d3f1039bc08c036785f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002656"
---
# <a name="listening-with-sockets"></a>écoute avec des sockets
Les sockets de serveur et d’écoute ouvrent un port sur le réseau, puis attendent qu’un client se connecte à ce port. Cet exemple montre comment créer un service distant pour un réseau TCP/IP, cependant, il existe d’autres protocoles et familles d’adresses réseau.  
  
 L’adresse unique d’un service TCP/IP peut être définie en combinant l’adresse IP de l’hôte avec le numéro de port du service afin de créer un point de terminaison pour ce service. La classe <xref:System.Net.Dns> fournit des méthodes qui retournent des informations sur les adresses réseau prises en charge par l’appareil du réseau local. Lorsque l’appareil du réseau local a plus d’une adresse réseau, ou si le système local prend en charge plusieurs appareils réseau, la classe **Dns** retourne des informations sur toutes les adresses réseau, et c’est à l’application de choisir l’adresse appropriée pour le service. L’IANA (Internet Assigned Numbers Authority) définit les numéros de port des services courants. Pour plus d’informations, consultez [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers). Les autres services peuvent avoir un numéro de port compris dans la plage 1 024 à 65 535.  
  
 L’exemple suivant crée un <xref:System.Net.IPEndPoint> pour un serveur en combinant la première adresse IP retournée par **Dns** pour l’ordinateur hôte, avec un numéro de port choisi dans la plage de numéros des ports inscrits.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Une fois le point de terminaison local déterminé, le <xref:System.Net.Sockets.Socket> doit être associé à ce point de terminaison à l’aide de la méthode <xref:System.Net.Sockets.Socket.Bind%2A>, puis configuré pour écouter le point de terminaison à l’aide de la méthode <xref:System.Net.Sockets.Socket.Listen%2A>. **Bind** lève une exception si la combinaison adresse-port est déjà utilisée. L’exemple suivant montre comment associer un **Socket** à un **IPEndPoint**.  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 La méthode **Listen** prend un seul paramètre qui spécifie combien de connexions au **Socket** peuvent être mises en attente avant qu’une erreur « Serveur occupé » soit retournée au client qui souhaite se connecter. Dans ce cas, jusqu’à 100 clients peuvent être placés dans la file d’attente de connexion avant qu’une réponse « Serveur occupé » ne soit retournée au 101e client.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’un socket serveur synchrone](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Utilisation d’un socket serveur asynchrone](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Utilisation de sockets clients](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Guide pratique pour créer un socket](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Sockets](../../../docs/framework/network-programming/sockets.md)
