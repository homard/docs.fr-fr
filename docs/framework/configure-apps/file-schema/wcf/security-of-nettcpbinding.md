---
title: '&lt;security&gt; de &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
ms.openlocfilehash: 045fb60f6ae0fb54dce7fd9bc8c634caee5fddcd
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48245125"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;security&gt; de &lt;netTcpBinding&gt;
Définit les paramètres de sécurité d’une liaison.  
  
 \<system.ServiceModel>  
\<liaisons >  
\<netTcpBinding>  
\<liaison >  
\<sécurité >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mode|Facultatif. Spécifie le type de sécurité appliqué. Les valeurs autorisées sont présentées ci-dessous. La valeur par défaut est `Transport`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Attribut Mode  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|La sécurité est désactivée.|  
|Transport|La sécurité de transport est fournie à l'aide du TLS sur le TCP ou SPNego. Le service peut devoir être configuré avec les certificats SSL. Il est possible de contrôler le niveau de protection avec ce mode.|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP. Par défaut, le corps SOAP est chiffré et signé. Ce mode offre diverses fonctionnalités, telles que, si les informations d'identification du service sont disponibles pour le client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message. L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
|TransportWithMessageCredential|La sécurité de transport est associée à la sécurité de message. La sécurité de transport est fournie par le TLS sur le TCP ou SPNego, et garantit l'intégrité, la confidentialité et l'authentification du serveur. La sécurité des messages SOAP fournit l'authentification du client. Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Définit les paramètres de sécurité pour le transport. Cet élément est de type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Définit les paramètres de sécurité pour le message. Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|L’élément de liaison de la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Notes  
 Chaque liaison standard fournit des paramètres pour le contrôle des exigences de sécurité de transfert. Ces paramètres incluent généralement le mode de sécurité qui indique si la sécurité au niveau du message ou du transport est utilisée et le choix du type d'informations d'identification du client. Selon le choix d'options présentées par ces paramètres, une pile de canaux est construite avec la sécurité appropriée.  
  
 Les liaisons fournies par le système par Windows Communication Foundation (WCF) constituent un ensemble conçu pour satisfaire aux impératifs de scénario les plus courants. Chaque liaison permet la spécification des conditions de sécurité pour des scénarios spécifiques.  
  
 Cet élément de configuration fournit les caractéristiques de sécurité pour `netTcpBinding`. Il s'agit d'une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs. Par défaut, elle génère une pile de communication d'exécution prenant en charge le TCP pour la remise des messages, Windows Security pour l'authentification et la sécurité des messages, WS-ReliableMessaging pour la fiabilité et l'encodage de messages binaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
