---
title: "Vue d&#39;ensemble de BlockingCollection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BlockingCollection, vue d’ensemble"
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble de BlockingCollection
<xref:System.Collections.Concurrent.BlockingCollection%601> est une classe de collection thread\-safe qui fournit les fonctionnalités suivantes :  
  
-   Implémentation du modèle de producteur\-consommateur.  
  
-   Ajout et reprise d'éléments simultanés à partir de plusieurs threads.  
  
-   Capacité maximale facultative.  
  
-   Opérations d'insertion et de suppression qui se bloquent lorsque la collection est vide ou complète.  
  
-   Opérations « d'essai » d'insertion et de suppression qui ne se bloquent pas ou qui bloquent jusqu'à une période spécifiée dans le temps.  
  
-   Encapsule tout type de collection qui implémente <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   Annulation avec jetons d'annulation.  
  
-   Deux genres d'énumérations avec `foreach` \(`For Each` en Visual Basic\) :  
  
    1.  Énumération en lecture seule.  
  
    2.  Énumération qui supprime des éléments à mesure qu'ils sont énumérés.  
  
## Prise en charge de la délimitation et du blocage  
 Prend en charge<xref:System.Collections.Concurrent.BlockingCollection%601> délimitation et bloquant.  La délimitation signifie que vous pouvez définir la capacité maximale de la collection.  La délimitation est importante dans certains scénarios parce qu'elle vous permet de contrôler la taille maximale de la collection en mémoire, et qu'elle empêche les threads producteurs de trop s'éloigner des threads consommateurs.  
  
 Plusieurs threads ou tâches peuvent ajouter simultanément des éléments à la collection, et si la collection atteint sa capacité maximale spécifiée, les threads producteurs se bloqueront jusqu'à ce qu'un élément soit supprimé.  Plusieurs consommateurs peuvent supprimer des éléments simultanément, et si la collection devient vide, les threads consommateurs se bloqueront jusqu'à ce qu'un producteur ajoute un élément.  Un thread producteur peut appeler <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> pour indiquer qu'aucun autre élément ne sera ajouté.  Les consommateurs surveillent la propriété <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> pour savoir quand la collection est vide et quand aucun autre élément ne sera plus ajouté.  L'exemple suivant affiche un BlockingCollection simple avec une capacité limitée à 100.  Une tâche de producteur ajoute des éléments à la collection tant qu'une certaine condition externe est remplie, puis appelle <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>.  La tâche du consommateur prend les éléments jusqu'à ce que la propriété <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> ait pour valeur True.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Pour obtenir un exemple complet, consultez [Comment : ajouter et prendre des éléments individuellement dans un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## Opérations de blocage chronométré  
 Lors d'opérations de blocage chronométré <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> sur les collections délimitées, la méthode essaie d'ajouter ou de prendre un élément.  Si un élément est disponible, il est placé dans la variable passée par référence, et la méthode retourne la valeur True.  Si aucun élément n'est extrait après un délai d'attente spécifié, la méthode retourne la valeur False.  Le thread est ensuite libre d'accomplir un autre travail utile avant de réessayer d'accéder à la collection.  Pour obtenir un exemple d'accès bloquant chronométré, consultez le deuxième exemple dans [Comment : ajouter et prendre des éléments individuellement dans un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## Annulation des opérations d'ajout et de reprise  
 Les opérations d'ajout et de reprise sont généralement exécutées dans une boucle.  Vous pouvez annuler une boucle en passant un <xref:System.Threading.CancellationToken> à la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ou <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>puis en vérifiant la valeur de la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> du jeton pour chaque itération.  Si la valeur est True, vous pouvez, si vous le souhaitez, répondre à la demande d'annulation en nettoyant toutes les ressources et en quittant la boucle.  L'exemple suivant montre une surcharge d' <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> qui prend un jeton d'annulation, et le code qui l'utilise :  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Pour obtenir un exemple sur la façon d'ajouter la prise en charge de l''annulation, consultez le deuxième exemple dans [Comment : ajouter et prendre des éléments individuellement dans un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## Spécification du type de collection  
 Lorsque vous créez une <xref:System.Collections.Concurrent.BlockingCollection%601>, vous pouvez spécifier non seulement la capacité limitée mais aussi le type de collection à utiliser.  Par exemple, vous pourriez spécifier un <xref:System.Collections.Concurrent.ConcurrentQueue%601> pour le comportement de premier entré premier sorti \(FIFO, First\-In\-First\-Out\), ou un <xref:System.Collections.Concurrent.ConcurrentStack%601> pour le comportement de dernier entré premier sorti \(LIFO, Last\-In\-First\-Out\).  Vous pouvez utiliser toute classe de collection qui implémente l'interface <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.  Le type de collection par défaut pour <xref:System.Collections.Concurrent.BlockingCollection%601> est <xref:System.Collections.Concurrent.ConcurrentQueue%601>.  L'exemple de code suivant indique comment créer une <xref:System.Collections.Concurrent.BlockingCollection%601> de chaînes avec une capacité de 1000 et utiliser un <xref:System.Collections.Concurrent.ConcurrentBag%601> :  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Pour plus d'informations, consultez [Comment : ajouter des fonctionnalités de liaison et de blocage à une collection](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## Prise en charge d'IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601> fournit une méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> qui permet aux consommateurs d'utiliser `foreach` \(`For Each` dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\) pour supprimer des éléments jusqu'à ce que la collection soit effectuée, ce qui signifie qu'il est vide et qu'aucun autre élément ne sera ajouté.  Pour plus d'informations, consultez [Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## Utilisation de nombreux BlockingCollections en tant qu'un  
 Pour les scénarios dans lesquels un consommateur doit prendre simultanément des éléments à partir de plusieurs collections, vous pouvez créer des tableaux de <xref:System.Collections.Concurrent.BlockingCollection%601> et utiliser les méthodes statiques telles que <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> qui ajouteront ou prendront à partir de chacune des collections du tableau.  Si une collection se bloque, la méthode en essaie immédiatement une autre jusqu'à ce qu'elle en trouve une qui soit susceptible d'exécuter l'opération.  Pour plus d'informations, consultez [Comment : utiliser des tableaux de collections de blocage dans un pipeline](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Collections et structures de données](../../../../docs/standard/collections/index.md)   
 [Collections thread\-safe](../../../../docs/standard/collections/thread-safe/index.md)