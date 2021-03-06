---
title: 'Résolution des problèmes : débogage des services Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510135"
---
# <a name="troubleshooting-debugging-windows-services"></a>Résolution des problèmes : débogage des services Windows
Quand vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagissent. Le **Gestionnaire des services** démarre votre service en appelant la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, puis attend 30 secondes que la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retourne une valeur. Si la méthode ne retourne aucune valeur au terme de ce délai, le gestionnaire affiche une erreur indiquant que le service ne peut pas être démarré.  
  
 Quand vous déboguez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> comme décrit dans [Guide pratique pour déboguer des applications de service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), tenez compte de ce délai de 30 secondes. Si vous placez un point d’arrêt dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et que vous n’effectuez aucun pas à pas détaillé dans un délai de 30 secondes, le gestionnaire ne démarre pas le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour déboguer les applications de service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
