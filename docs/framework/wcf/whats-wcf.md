---
title: Présentation de Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: f202d922b441d86838dd41992104ceecfc9bbabf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197628"
---
# <a name="what-is-windows-communication-foundation"></a>Présentation de Windows Communication Foundation

Windows Communication Foundation (WCF) est une infrastructure pour la création d’applications orientées service. À l’aide de WCF, vous pouvez envoyer données sous forme de messages asynchrones à partir d’un point de terminaison à un autre. Un point de terminaison de service peut faire partie d'un service disponible en continu et hébergé par IIS, ou il peut s'agir d'un service hébergé dans une application. Un point de terminaison peut être un client d'un service qui demande des données auprès d'un point de terminaison de service. Les messages peuvent être simplement constitués d'un caractère ou d'un mot unique envoyé au format XML, ou se présenter sous la forme d'un flux de données binaires plus complexe. Voici quelques exemples de scénarios :

-   Service sécurisé pour traiter des transactions commerciales.

-   Service qui fournit des données actuelles à d'autres services, comme un rapport sur le trafic ou tout autre service de surveillance.

-   Service de conversation qui permet à deux personnes de communiquer ou d'échanger des données en temps réel.

-   Application de tableau de bord qui interroge les données d'un ou de plusieurs services et les présente de manière logique.

-   Exposition d'un workflow implémenté à l'aide de Windows Workflow Foundation en tant que service WCF.

-   Application Silverlight pour interroger un service afin d'obtenir les flux de données les plus récents.

Création de telles applications était possible avant l’existence de WCF, WCF simplifie le développement de points de terminaison plus facile que jamais. En résumé, WCF est conçu pour offrir une approche gérable à la création de services Web et les clients de service Web.

## <a name="features-of-wcf"></a>Fonctions de WCF

WCF inclut l’ensemble de fonctionnalités suivant. Pour plus d’informations, consultez [informations sur les fonctionnalités WCF](../../../docs/framework/wcf/feature-details/index.md).

-   **Orientation services**

     Une des conséquences de l’utilisation de normes WS est que WCF vous permet de créer *orientée* applications. L'architecture orientée services (SOA, Service-Oriented Architecture) dépend de services Web pour envoyer et recevoir des données. Les services présentent l'avantage d'être faiblement couplés, au lieu d'être encodés de manière irréversible d'une application à une autre. Une relation faiblement couplée implique que tout client créé sur une plate-forme peut se connecter à n'importe quel service, dans la mesure où les contrats essentiels sont respectés.

-   **Interopérabilité**

     WCF implémente les normes industrielles modernes pour l’interopérabilité des services Web. Pour plus d’informations sur les normes prises en charge, consultez [interopérabilité et intégration](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).

-   **Modèles de messages variés**

     Les messages sont échangés selon l'un des différents modèles disponibles. Le modèle le plus courant est de type demande/réponse, dans lequel un point de terminaison demande des données auprès d'un second point de terminaison. Le second point de terminaison répond. Il existe d'autres modèles, comme un message unidirectionnel dans lequel un seul point de terminaison envoie un message sans attendre de réponse. Le modèle d'échange en duplex constitue un modèle plus complexe dans la mesure où deux points de terminaison établissent une connexion et envoient des données de part et d'autre, à la manière d'un programme de messagerie instantanée. Pour plus d’informations sur l’implémentation de l’échange de messages différents motifs à l’aide de WCF, consultez [contrats](../../../docs/framework/wcf/feature-details/contracts.md).

-   **Métadonnées de service**

     WCF prend en charge la publication des métadonnées de service à l’aide de formats spécifiés dans les normes industrielles telles que WSDL, schéma XML et WS-Policy. Ces métadonnées peuvent être utilisées pour générer et configurer les clients pour accéder aux services WCF automatiquement. Les métadonnées peuvent être publiées via HTTP et HTTPS ou à l'aide de la norme d'échange de métadonnées de service Web. Pour plus d’informations, consultez [métadonnées](../../../docs/framework/wcf/feature-details/metadata.md).

-   **Contrats de données**

     Étant donné que WCF est créé à l’aide de la [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], il inclut également des méthodes faciles à coder de fournir les contrats que vous souhaitez appliquer. Le contrat de données représente l'un des types universels de contrats. Par nature, lorsque vous codez votre service à l'aide de Visual C# ou de Visual Basic, la méthode la plus simple de gérer les données consiste à créer des classes qui représentent une entité de données dotée de propriétés. WCF inclut un système complet pour travailler avec des données de cette manière facile. Une fois que vous avez créé les classes qui représentent les données, votre service génère automatiquement les métadonnées qui permettent aux clients de se conformer aux types de données que vous avez conçus. Pour plus d’informations, consultez [à l’aide de contrats de données](../../../docs/framework/wcf/feature-details/using-data-contracts.md)

-   **Sécurité**

     Les messages peuvent être chiffrés afin de protéger la confidentialité. Par ailleurs, vous pouvez demander aux utilisateurs de s'authentifier avant de pouvoir recevoir des messages. La sécurité peut être implémentée à l'aide de normes célèbres, telles que SSL ou WS-SecureConversation. Pour plus d’informations, consultez l’article [Sécurité](../../../docs/framework/wcf/feature-details/security.md).

-   **Transports et encodages variés**

     Les messages peuvent être envoyés via l'un des différents encodages et protocoles de transport intégrés. Les plus courants de protocole et de codage consiste à envoyer le texte encodé des messages SOAP à l’aide du protocole HTTP (HyperText Transfer) pour une utilisation sur le World Wide Web. Vous pouvez également, WCF vous permet d’envoyer des messages sur TCP, canaux nommés ou MSMQ. Ces messages peuvent être encodés en tant que texte ou à l'aide d'un format binaire optimisé.  Les données binaires peuvent être envoyées efficacement à l'aide de la norme MTOM. Si aucun des transports ou encodages fournis ne convient à vos besoins, vous avez la possibilité de créer votre propre encodage ou transport personnalisé. Pour plus d’informations sur les transports et encodages pris en charge par WCF, consultez [Transports](../../../docs/framework/wcf/feature-details/transports.md).

-   **Messages fiables et mis en file d'attente**

     WCF prend en charge l’échange de messages fiables à l’aide de sessions fiables implémentées via WS-Reliable Messaging et MSMQ. Pour plus d’informations sur le support de messagerie fiable et en file d’attente dans WCF, consultez [files d’attente et Sessions fiables](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).

-   **Messages durables**

     Un message durable est un message qui n'est jamais perdu suite à une interruption de la communication. Les messages conformes au modèle de message durable sont toujours enregistrés dans une base de données. En cas d'interruption, la base de données vous permet de reprendre l'échange de messages une fois la connexion restaurée. Vous pouvez également créer un message durable à l’aide de Windows Workflow Foundation (WF). Pour plus d’informations, consultez [Services de Workflow](../../../docs/framework/wcf/feature-details/workflow-services.md).

-   **Transactions**

     WCF prend également en charge les transactions à l'aide de trois modèles de transaction : WS-AtomicTtransactions, les interfaces API dans l'espace de noms <xref:System.Transactions> et MSDTC (Microsoft Distributed Transaction Coordinator). Pour plus d’informations sur la transaction prise en charge dans WCF consultez [Transactions](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).

-   **Prise en charge d'AJAX et de REST**

     REST est un exemple d'une technologie évoluant vers le Web 2.0. WCF peut être configuré pour traiter les données XML « ordinaires » qui ne sont pas encapsulées dans une enveloppe SOAP. WCF peut également être étendu pour prendre en charge les formats XML spécifiques, tels que ATOM (une norme populaire RSS) et même des formats non-XML, tels que JavaScript Objet Notation (JSON).

-   **Extensibilité**

     L’architecture WCF a un nombre de points d’extensibilité. Si une capacité supplémentaire est requise, il existe un certain nombre de points d'entrée qui vous permettent de personnaliser le comportement d'un service. Pour plus d’informations sur l’extensibilité disponible points, consultez [Extending WCF](../../../docs/framework/wcf/extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Intégration WCF avec d'autres technologies Microsoft

WCF est une plateforme flexible. En raison de cette flexibilité extrême, WCF est également utilisé dans plusieurs autres produits Microsoft. En comprenant les principes fondamentaux de WCF, vous avez un avantage immédiat si vous utilisez également un de ces produits.

La première technologie associée à WCF a été Windows Workflow Foundation (WF). Les workflows simplifient le développement d’applications en encapsulant les étapes dans le flux de travail en tant que « activités ». Dans la première version de Windows Workflow Foundation, un développeur devait créer un hôte pour le flux de travail. La prochaine version de Windows Workflow Foundation a été intégrée à WCF. Cela a permis tout workflow être hébergés facilement dans un service WCF. Vous pouvez le faire automatiquement en choisissant le type de projet WF/WCF dans Visual Studio 2012 ou version ultérieure.

Microsoft BizTalk Server R2 utilise également WCF comme une technologie de communication. BizTalk a été conçu pour recevoir et transformer des données d'un format standardisé en un autre. Les messages doivent être remis dans leur boîte de message centrale, où ils peuvent être transformés suivant un mappage strict ou à l'aide de l'une des fonctionnalités BizTalk, telles que le moteur de workflow. BizTalk peut maintenant utiliser l’adaptateur WCF métier (LOB) pour remettre des messages à la boîte de message.

Microsoft Silverlight est une plate-forme de création d'applications Web enrichies interopérables qui permettent aux développeurs de créer des sites Web comportant de nombreux médias (tels que la vidéo en continu). Depuis la version 2, Silverlight a intégré WCF comme une technologie de communication pour connecter les applications Silverlight aux points de terminaison WCF.

Le [!INCLUDE[dublin](../../../includes/dublin-md.md)] application server est spécifiquement conçu pour déployer et gérer des applications qui utilisent WCF pour la communication. Le [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] inclut des options de configuration et des outils riches, spécialement conçues pour les applications WCF.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel>
- [Concepts fondamentaux de Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
- [Architecture Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)
- [Conseils et bonnes pratiques](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [Didacticiel Bien démarrer](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Guide de la documentation](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Exemples Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
