---
title: IHostSyncManager, interface
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa9f039cb7eaa7ccd22bad36098c00a697d818d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443971"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager, interface
Fournit des méthodes qui permettent le common language runtime (CLR) pour créer des primitives de synchronisation en appelant l’hôte au lieu d’utiliser les fonctions de synchronisation Win32.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateAutoEvent, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Crée un objet d’événement de réinitialisation automatique.|  
|[CreateCrst, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Crée un objet de section critique pour la synchronisation.|  
|[CreateCrstWithSpinCount, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Crée un objet de section critique dont le nombre de sélection numérique pour la synchronisation.|  
|[CreateManualEvent, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Crée un objet d’événement de réinitialisation manuelle.|  
|[CreateMonitorEvent, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|Crée un objet d’événement de réinitialisation automatique surveillé.|  
|[CreateRWLockReaderEvent, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.|  
|[CreateRWLockWriterEvent, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Crée un objet d’événement de réinitialisation automatique pour l’implémentation d’un verrou de writer.|  
|[CreateSemaphore, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Crée un [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objet pour le CLR à utiliser en tant que sémaphore pour les événements d’attente.|  
|[SetCLRSyncManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Définit le [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance à associer à actuel `IHostSyncManager` instance.|  
  
## <a name="remarks"></a>Notes  
 Le CLR détecte l’implémentation de l’hôte de `IHostSyncManager` en appelant le [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) méthode avec un `IID` de IID_IHostSyncManager.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
