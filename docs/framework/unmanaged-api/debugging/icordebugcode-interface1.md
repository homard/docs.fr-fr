---
title: ICorDebugCode Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37917577c802514fcebc3ea0792cbce9bb8a7345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414077"
---
# <a name="icordebugcode-interface1"></a>ICorDebugCode Interface1
Représente un segment de code MSIL ou de code natif.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Crée un point d’arrêt à l’offset spécifié.|  
|[GetAddress, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Obtient l’adresse virtuelle relative (RVA) du segment de code que cela `ICorDebugCode` représente.|  
|[GetCode, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Obtient tout le code pour la fonction spécifiée, la mise en forme pour le code machine. Cette méthode est déconseillée ; Utilisez [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) à la place.|  
|[GetEnCRemapSequencePoints, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Non implémenté.|  
|[GetFunction, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Obtient la « ICorDebugFunction » associée à ce `ICorDebugCode`.|  
|[GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages des offsets MSIL aux offsets natifs.|  
|[GetSize, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Obtient la taille, en octets, du code binaire représenté par ce `ICorDebugCode`.|  
|[GetVersionNumber, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Obtient le nombre de base 1 qui identifie la version du code par ce `ICorDebugCode` représente.|  
|[IsIL, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Obtient une valeur qui indique si cette `ICorDebugCode` est compilé dans le langage MSIL.|  
  
## <a name="remarks"></a>Notes  
 `ICorDebugCode` peut représenter le MSIL ou le code natif. Un objet « ICorDebugFunction » qui représente le code MSIL peut avoir zéro ou un `ICorDebugCode` objets associés. Un objet « ICorDebugFunction » qui représente le code natif peut avoir un nombre quelconque de `ICorDebugCode` objets associés.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
    
 [ICorDebugCode3, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
