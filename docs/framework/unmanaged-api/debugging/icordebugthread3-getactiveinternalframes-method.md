---
title: ICorDebugThread3::GetActiveInternalFrames, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac87de35478e5eabdc8cdc3568baf2086923e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423016"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames, méthode
Retourne un tableau de frames internes ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objets) sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cInternalFrames`  
 [in] Le nombre de frames internes prévus dans `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Un pointeur vers un `ULONG32` qui contient le nombre de frames internes sur la pile.  
  
 `ppInternalFrames`  
 [dans, out] Pointeur vers l’adresse d’un tableau de frames internes sur la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objet a été créé.|  
|E_INVALIDARG|`cInternalFrames` n’est pas zéro et `ppInternalFrames` est `null`, ou `pcInternalFrames` est `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` est inférieur au nombre de frames internes.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Les frames internes sont des structures de données placés sur la pile par le runtime pour stocker des données temporaires.  
  
 Lorsque vous appelez `GetActiveInternalFrames`, vous devez définir le `cInternalFrames` paramètre 0 (zéro) et le `ppInternalFrames` paramètre null. Lorsque `GetActiveInternalFrames` retourne tout d’abord, `pcInternalFrames` contient le nombre de frames internes sur la pile.  
  
 `GetActiveInternalFrames` doit ensuite être appelé une deuxième fois. Vous devez passer le nombre correct (`pcInternalFrames`) dans le `cInternalFrames` paramètre, et spécifier un pointeur vers un tableau de taille appropriée dans `ppInternalFrames`.  
  
 Utilisez le [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) frames de pile de retour réel de méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
