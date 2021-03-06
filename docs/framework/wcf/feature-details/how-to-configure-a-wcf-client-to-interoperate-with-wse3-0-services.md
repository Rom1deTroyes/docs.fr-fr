---
title: 'Comment : configurer un client WCF pour interagir avec les services WSE 3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 9d7cb4869e9e460373bffbf33f61f61ecb6e9948
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505453"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Comment : configurer un client WCF pour interagir avec les services WSE 3.0
Les clients Windows Communication Foundation (WCF) sont compatible au niveau câble avec Web Services Enhancements 3.0 pour les services Microsoft .NET (WSE) lorsque les clients WCF sont configurés pour utiliser la version d’août 2004 de la spécification WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Configurer un client WCF pour interagir avec un service Web WSE 3.0  
  
1.  Exécutez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un client WCF pour le service Web WSE 3.0.  
  
     Pour un service Web WSE, une classe de client WCF est créée.  
  
     Pour plus d’informations sur la création d’un client WCF, consultez le [Comment : créer un Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Créez une classe qui représente une liaison pouvant communiquer avec les services Web WSE 3.0.  
  
     La classe suivante fait partie de la [interopérabilité avec WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemple.  
  
    1.  Créez une classe qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         L'exemple de code suivant crée une classe nommée `WseHttpBinding` qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Ajoutez à la classe des propriétés spécifiant l'assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, et les paramètres de protection des messages.  
  
         L’exemple de code suivant définit `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` propriétés qui spécifient l’assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises et les paramètres de protection de message, respectivement.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituez la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pour définir les propriétés de la liaison.  
  
         L'exemple de code suivant spécifie le transport, l'encodage de message et les paramètres de protection des messages en obtenant les valeurs des propriétés `SecurityAssertion` et `MessageProtectionOrder`.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  Dans le code d’application cliente, ajoutez le code pour définir les propriétés de la liaison.  
  
     L’exemple de code suivant spécifie que le client WCF doit utiliser l’authentification et protection des messages tel que défini par le WSE 3.0 `AnonymousForCertificate` assertion de sécurité clé en main. En outre, des sessions sécurisées et des clés dérivées sont requises.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit une liaison personnalisée qui expose des propriétés correspondant à celles d’une assertion de sécurité clé en main WSE 3.0. La liaison personnalisée, qui est nommée `WseHttpBinding`, est ensuite utilisé pour spécifier les propriétés de liaison pour un client WCF.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.Binding>  
 [Interopérabilité avec WSE](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
