---
title: 'Comment : obtenir un certificat (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519220"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Comment : obtenir un certificat (WCF)
Pour utiliser une de Windows Communication Foundation (WCF) fonctionnalités de qui utilisent des certificats X.509, vous devez d’abord obtenez des certificats.  
  
### <a name="to-obtain-an-x509-certificate"></a>Pour obtenir un certificat X.509  
  
1.  Choisissez l'une des valeurs suivantes :  
  
    -   Achetez un certificat auprès d'une autorité de certification, telle que VeriSign, Inc.  
  
    -   Installez votre propre service de certificats et faites en sorte qu'une autorité de certification signe les certificats. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter et Windows 2000 Datacenter Server incluent tous des services de certificat qui prennent en charge l'infrastructure à clé publique. Dans Windows Server 2008, utilisez le [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) rôle pour gérer une autorité de certification.  
  
    -   Installez votre propre service de certificats et ne faites pas signer les certificats.  
  
    > [!NOTE]
    >  Quelle que soit la méthode adoptée, le destinataire de la demande SOAP contenant le certificat X.509 doit approuver ce dernier. Cela signifie que le certificat X.509 ou un émetteur dans la chaîne de certificats se trouve dans le magasin de certificats Personnes de confiance et que le certificat X.509 ne se trouve pas dans le magasin de certificats non fiables.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Guide pratique pour créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
