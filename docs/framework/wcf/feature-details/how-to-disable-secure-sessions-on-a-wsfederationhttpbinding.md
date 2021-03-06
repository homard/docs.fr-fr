---
title: 'Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
author: BrucePerlerMS
ms.openlocfilehash: e81469f5ac55b1c698dc99af0782dbdedab33339
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036565"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding
Certains services peuvent requérir des informations d'identification fédérées mais ne prennent pas en charge les sessions sécurisées. Dans ce cas, vous devez désactiver la fonctionnalité de session sécurisée. Contrairement à la <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, la <xref:System.ServiceModel.WSFederationHttpBinding> classe ne fournit pas la possibilité de désactiver des sessions sécurisées lors de la communication avec un service. À la place, vous devez créer une liaison personnalisée qui remplace les paramètres de session sécurisée par un démarrage.  
  
 Cette rubrique montre comment modifier les éléments de liaison contenus dans une <xref:System.ServiceModel.WSFederationHttpBinding> pour créer une liaison personnalisée. Le résultat est identique à <xref:System.ServiceModel.WSFederationHttpBinding> mais n'utilise pas de sessions sécurisées.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Pour créer une liaison fédérée personnalisée sans session sécurisée  
  
1.  Créez une instance de la classe <xref:System.ServiceModel.WSFederationHttpBinding> soit impérativement dans du code, soit en la chargeant à partir du fichier de configuration.  
  
2.  Clonez la <xref:System.ServiceModel.WSFederationHttpBinding> dans une <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Recherchez <xref:System.ServiceModel.Channels.SecurityBindingElement> dans <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Recherchez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> dans <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Remplacez le <xref:System.ServiceModel.Channels.SecurityBindingElement> d'origine par l'élément de liaison de sécurité de démarrage des <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant permet de créer une liaison fédérée personnalisée sans session sécurisée.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler l'exemple de code, créez un projet qui référence l'assembly System.ServiceModel.dll.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
