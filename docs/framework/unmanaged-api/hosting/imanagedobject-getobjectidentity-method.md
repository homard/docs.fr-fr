---
title: IManagedObject::GetObjectIdentity, méthode
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1975e5bf20453a3bcd6761d9734be7ddd2ceef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440325"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity, méthode
Obtient l’identité de cet objet managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBSTRGUID`  
 [out] Pointeur vers le GUID du processus dans lequel réside l’objet.  
  
 `AppDomainID`  
 [out] Pointeur vers l’ID de l’objet domaine d’application.  
  
 `pCCW`  
 [out] Pointeur vers l’index de l’objet dans la v-table classique COM.  
  
## <a name="remarks"></a>Notes  
 L’identité d’un objet managé inclut des ID de domaine d’application, des processus GUID et des index de l’objet dans la v-table classique COM.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IManagedObject, interface](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
