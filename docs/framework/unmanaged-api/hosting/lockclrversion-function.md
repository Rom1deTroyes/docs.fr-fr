---
title: LockClrVersion, fonction
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6956d73be0380baef96d94584f007e0683331784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446084"
---
# <a name="lockclrversion-function"></a>LockClrVersion, fonction
Permet à l’hôte déterminer quelle version du common language runtime (CLR) sera utilisée au sein du processus avant d’initialiser le CLR explicitement.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hostCallback`  
 [in] La fonction d’être appelée par le CLR lors de l’initialisation.  
  
 `pBeginHostSetup`  
 [in] La fonction peut être appelée par l’hôte pour informer le CLR que l’initialisation démarre.  
  
 `pEndHostSetup`  
 [in] La fonction peut être appelée par l’hôte pour informer le CLR que l’initialisation est terminée.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|Un ou plusieurs des arguments sont null.|  
  
## <a name="remarks"></a>Notes  
 L’hôte appelle `LockClrVersion` avant d’initialiser le CLR. `LockClrVersion` accepte trois paramètres, qui sont tous des rappels de type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Ce type est défini comme suit.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Les étapes suivantes se produisent lors de l’initialisation du runtime :  
  
1.  L’hôte appelle [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou l’une des autres fonctions de l’initialisation du runtime. L’hôte peut également initialiser le runtime à l’aide d’activation d’un objet COM.  
  
2.  Le runtime appelle la fonction spécifiée par le `hostCallback` paramètre.  
  
3.  La fonction spécifiée par `hostCallback` fait ensuite la séquence d’appels suivante :  
  
    -   La fonction spécifiée par le `pBeginHostSetup` paramètre.  
  
    -   `CorBindToRuntimeEx` (ou une autre fonction de l’initialisation du runtime).  
  
    -   [ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   La fonction spécifiée par le `pEndHostSetup` paramètre.  
  
 Tous les appels de `pBeginHostSetup` à `pEndHostSetup` doit se produire sur un seul thread ou d’une fibre, avec la même pile logique. Ce thread peut être différent du thread sur lequel `hostCallback` est appelée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
