---
title: Création d'un modèle de chiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964382"
---
# <a name="creating-a-cryptographic-scheme"></a>Création d'un modèle de chiffrement
Les composants de chiffrement de .NET Framework peuvent être combinés pour créer différents modèles permettant de chiffrer et de déchiffrer des données.  
  
 Un simple modèle de chiffrement pour chiffrer et déchiffrer des données peut spécifier les étapes suivantes :  
  
1.  Chaque partie génère une paire de clés publique/privée.  
  
2.  Les parties échangent leurs clés publiques.  
  
3.  Chaque partie génère une clé secrète pour le chiffrement TripleDES (par exemple), et chiffre la clé nouvellement créée à l'aide de la clé publique de l'autre.  
  
4.  Chaque partie envoie les données à l'autre et combine la clé secrète de l'autre avec la sienne, dans un ordre spécifique, pour créer une clé secrète.  
  
5.  Les parties lancent ensuite une conversation à l'aide du chiffrement symétrique.  
  
 La création d’un modèle de chiffrement n’est pas une tâche facile. Pour plus d’informations sur l’utilisation du chiffrement, consultez la rubrique de cryptographie dans la documentation Platform SDK à http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Voir aussi

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
