---
title: ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ac041db64a874cc143657c601f30e4482dd2462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434433"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
Fournit une fonction de rappel qui est appelée lorsqu’une version du common language runtime (CLR) est chargée en premier, mais pas encore démarrée. Cette méthode remplace la [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallbackFunction`  
 [in] La fonction de rappel qui est appelée lorsqu’un nouveau runtime a été chargé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pCallbackFunction` a la valeur null.|  
  
## <a name="remarks"></a>Notes  
 Le rappel fonctionne de la façon suivante :  
  
-   Le rappel est appelé uniquement lorsqu’un runtime est chargé pour la première fois.  
  
-   Le rappel n’est pas appelé pour les chargements réentrants du même runtime.  
  
-   Pour les chargements de runtime non réentrants, les appels à la fonction de rappel sont sérialisés.  
  
 La fonction de rappel a le prototype suivant :  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Les prototypes de fonction de rappel sont les suivantes :  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Si l’hôte projette de charger ou de provoquer une autre exécution à charger de manière réentrante, la `pfnCallbackThreadSet` et `pfnCallbackThreadUnset` les paramètres qui sont fournis dans le rappel de fonction doit être utilisée de la façon suivante :  
  
-   `pfnCallbackThreadSet` doit être appelé par le thread qui peut entraîner une charge de l’exécution avant la tentative de type de charge.  
  
-   `pfnCallbackThreadUnset` doit être appelé lorsque le thread ne provoquera plus tel chargement de runtime (et avant le retour du rappel initial).  
  
-   `pfnCallbackThreadSet` et `pfnCallbackThreadUnset` sont tous deux non réentrante.  
  
> [!NOTE]
>  Héberger des applications ne doivent pas appeler `pfnCallbackThreadSet` et `pfnCallbackThreadUnset` en dehors de la `pCallbackFunction` paramètre.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRMetaHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
