---
title: ICLRTask2, interface
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed0d2ff3b64bab026087e13d54314eca86181d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438806"
---
# <a name="iclrtask2-interface"></a>ICLRTask2, interface
Fournit toutes les fonctionnalités de la [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface ; en outre, fournit des méthodes qui permettent d’abandons de threads pour être retardée sur le thread actuel.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginPreventAsyncAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Nouveau thread de retards interrompre les requêtes sur le thread actuel.|  
|[EndPreventAsyncAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Permet de nouveau ou en attente de demandes d’abandon de thread de thread abandonne sur le thread actuel.|  
  
## <a name="remarks"></a>Notes  
 Le `ICLRTask2` interface hérite de la `ICLRTask` de l’interface et ajoute des méthodes qui permettent à l’hôte de différer les abandons de thread, pour protéger une région de code qui ne doit pas échouer. Appel de `BeginPreventAsyncAbort` incrémente le compteur de délai d’abandon de thread pour le thread actuel et l’appel `EndPreventAsyncAbort` décrémente il. Les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` peuvent être imbriquées. Tant que le compteur est supérieur à zéro, pour le thread actuel abandons de thread.  
  
 Si les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` sont ne pas associés, il est possible d’atteindre un état dans le thread abandons ne peut pas être remis au thread actuel.  
  
 Le délai d’attente d’un thread qui abandonne lui-même n’est pas reconnue.  
  
 La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle (VM). Utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle. Par exemple, l’appel `EndPreventAsyncAbort` sans appeler d’abord `BeginPreventAsyncAbort` Impossible de définir le compteur à zéro lorsque la machine virtuelle a précédemment incrémenté. De même, le compteur interne n’est pas vérifié pour le dépassement de capacité. Si elle dépasse sa limite intégrale, car il est incrémenté par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.  
  
 Pour plus d’informations sur les membres hérités de `ICLRTask` et sur les autres utilisations de cette interface, consultez la [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
