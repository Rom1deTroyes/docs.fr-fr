---
title: "Transport: WSE 3.0 TCP Interoperability | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Transport: WSE 3.0 TCP Interoperability
Cet exemple indique comment implémenter une session duplex TCP en tant que transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] personnalisé.Il décrit également comment utiliser l'extensibilité de la couche du canal pour assurer l'interface sur le câble avec les systèmes déployés existants.Les étapes suivantes indiquent comment générer ce transport [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] personnalisé :  
  
1.  À partir d'un socket TCP, créez les implémentations serveur et client de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> qui utilisent le tramage DIME pour définir les limites de message.  
  
2.  Créez une fabrique de canaux qui se connecte à un service TCP WSE et envoie des messages tramés sur le client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
3.  Créez un écouteur de canal pour accepter les connexions TCP entrantes et produire les canaux correspondants.  
  
4.  Assurez\-vous que les exceptions spécifiques au réseau sont normalisées selon la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.  
  
5.  Ajoutez un élément de liaison qui ajoute le transport personnalisé à une pile de canaux.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ajout d'un élément de liaison](#AddingABindingElement).  
  
## Création de IDuplexSessionChannel  
 La première étape de l'écriture du transport WSE 3.0 TCP Interoperability consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sur <xref:System.Net.Sockets.Socket>.`WseTcpDuplexSessionChannel` dérive de <xref:System.ServiceModel.Channels.ChannelBase>.La logique d'envoi d'un message comporte deux parties principales : \(1\) encodage du message en octets, et \(2\) tramage et envoi des octets sur le câble.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 En outre, un verrou est utilisé afin que les appels Send\(\) conservent la garantie de l'ordre IDuplexSessionChannel et afin que les appels du socket sous\-jacent soient correctement synchronisés.  
  
 `WseTcpDuplexSessionChannel` utilise <xref:System.ServiceModel.Channels.MessageEncoder> pour traduire <xref:System.ServiceModel.Channels.Message> vers et à partir de byte\[\].Dans la mesure où il s'agit d'un transport, `WseTcpDuplexSessionChannel` est également chargé d'appliquer l'adresse distante avec laquelle le canal a été configuré.`EncodeMessage` encapsule la logique de cette conversion.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Une fois que <xref:System.ServiceModel.Channels.Message> est encodé en octets, il doit être transmis sur le câble.Pour cela, un système permettant de définir des limites de message est nécessaire.WSE 3.0 utilise une version de [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) comme protocole de tramage.`WriteData` encapsule la logique de tramage afin d'encapsuler byte\[\] dans un ensemble d'enregistrements DIME.  
  
 La logique de réception des messages est très similaire.La principale difficulté consiste à gérer le fait qu'une lecture de socket peut retourner un nombre d'octets inférieur à celui demandé.Pour recevoir un message, `WseTcpDuplexSessionChannel` lit des octets du câble, décode le tramage DIME, puis utilise <xref:System.ServiceModel.Channels.MessageEncoder> pour transformer byte\[\] en <xref:System.ServiceModel.Channels.Message>.  
  
 Le `WseTcpDuplexSessionChannel` de base suppose qu'il reçoit un socket connecté.La classe de base gère l'arrêt du socket.Trois valeurs correspondent à la fermeture du socket :  
  
-   OnAbort : fermeture du socket de façon incorrecte \(fermeture stricte\).  
  
-   On\[Begin\]Close : fermeture du socket de façon correcte \(fermeture souple\).  
  
-   session.CloseOutputSession : arrêt du flux de données sortant \(fermeture partielle\).  
  
## Fabrique de canaux  
 L'étape suivante de l'écriture du transport TCP consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients.  
  
-   `WseTcpChannelFactory` dérive de <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel\>.Il s'agit d'une fabrique qui substitue `OnCreateChannel` pour produire des canaux clients.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` ajoute la logique au `WseTcpDuplexSessionChannel`de base afin de se connecter à un serveur TCP à l'heure `channel.Open`.Le nom d'hôte est d'abord résolu en une adresse IP, comme indiqué dans le code suivant.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Ensuite, le nom d'hôte est connecté à la première adresse IP disponible dans une boucle, comme indiqué dans le code suivant.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Dans le cadre du contrat de canal, les exceptions spécifiques du domaine sont incluses dans un wrapper, comme `SocketException` dans <xref:System.ServiceModel.CommunicationException>.  
  
## Écouteur de canal  
 L'étape suivante de l'écriture du transport TCP consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelListener> permettant d'accepter les canaux serveur.  
  
-   `WseTcpChannelListener` dérive de <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel\> et substitue On\[Begin\]Open et On\[Begin\]Close pour contrôler la durée de vie de son socket d'écoute.Dans OnOpen, un socket est créé pour écouter sur IP\_ANY.Des implémentations plus avancées peuvent créer un deuxième socket pour écouter également sur IPv6.Elles permettent également de spécifier l'adresse IP dans le nom d'hôte.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Lorsqu'un nouveau socket est accepté, un canal serveur est initialisé avec celui\-ci.Toutes les entrées et sorties étant déjà implémentées dans la classe de base, ce canal est donc chargé d'initialiser le socket.  
  
## Ajout d'un élément de liaison  
 Maintenant que les fabriques de canaux sont générées, elles doivent être exposées à l'exécution de ServiceModel via une liaison.Une liaison est une collection d'éléments de liaison qui représente la pile de communication associée à une adresse de service.Chaque élément de la pile est représenté par un élément de liaison.  
  
 Dans notre exemple, l'élément de liaison est `WseTcpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>.Il prend en charge <xref:System.ServiceModel.Channels.IDuplexSessionChannel> et substitue les méthodes suivantes pour générer les fabriques associées à notre liaison.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Notre exemple contient également des membres permettant de cloner l'élément `BindingElement` et de retourner notre schéma \(wse.tcp\).  
  
## Console de test TCP WSE  
 Le code de test permettant d'utiliser cet exemple de transport est disponible dans TestCode.cs.Les instructions suivantes indiquent comment installer l'exemple WSE `TcpSyncStockService`.  
  
 Le code de test crée une liaison personnalisée qui utilise MTOM comme encodage et `WseTcpTransport` comme transport.Il installe également AddressingVersion afin d'assurer la conformité avec WSE 3.0, comme indiqué dans le code suivant.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Il se compose de deux tests : le premier installe un client typé à l'aide du code généré à partir de WSDL WSE 3.0.Le deuxième utilise [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à la fois comme client et serveur en envoyant directement des messages sur les API de canal.  
  
 L'exécution de l'exemple est censée donner le résultat suivant.  
  
 Client :  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 Serveur :  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Pour que vous puissiez exécuter cet exemple, WSE 3.0 doit être installé et vous devez disposer de l'exemple `TcpSyncStockService` WSE.Vous pouvez télécharger [WSE 3.0 à partir de MSDN](http://go.microsoft.com/fwlink/?LinkId=95000) \(page pouvant être en anglais\).  
  
> [!NOTE]
>  Étant donné que WSE 3.0 n'est pas pris en charge sur [!INCLUDE[lserver](../../../../includes/lserver-md.md)], vous ne pouvez pas installer ou exécuter l'exemple `TcpSyncStockService` sur ce système d'exploitation.  
  
1.  Après avoir installé l'exemple `TcpSyncStockService`, procédez comme suit :  
  
    1.  Ouvrez `TcpSyncStockService` dans Visual Studio \(notez que l'exemple TcpSyncStockService est installé avec WSE 3.0.Il ne fait pas partie du code de cet exemple\).  
  
    2.  Définissez StockService comme projet de démarrage.  
  
    3.  Ouvrez StockService.cs dans le projet StockService et commentez l'attribut \[Policy\] sur la classe `StockService`.Cette opération désactive la sécurité de l'exemple.Bien que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puisse interagir avec des points de terminaison sécurisés WSE 3.0, la sécurité est désactivée afin que cet exemple reste axé sur le transport TCP personnalisé.  
  
    4.  Appuyez sur F5 pour démarrer `TcpSyncStockService`.Le service démarre dans une nouvelle fenêtre de console.  
  
    5.  Ouvrez cet exemple de transport TCP dans Visual Studio.  
  
    6.  Dans TestCode.cs, mettez la variable « hostname » à jour afin qu'elle corresponde au nom de l'ordinateur qui exécute `TcpSyncStockService`.  
  
    7.  Appuyez sur F5 pour démarrer l'exemple de transport TCP.  
  
    8.  Le client test du transport TCP démarre dans une nouvelle console.Le client demande les cotations boursières au service, puis affiche les résultats dans sa fenêtre de console.  
  
## Voir aussi