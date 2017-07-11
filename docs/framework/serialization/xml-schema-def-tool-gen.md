---
title: "Comment&#160;: utiliser l&#39;outil XML Schema Definition pour g&#233;n&#233;rer des classes et des documents de sch&#233;ma XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "générer des classes XML à l'aide de l'outil XML Schema Definition"
  - "générer un document de schéma à l'aide de l'outil XML Schema Definition"
  - "XML Schema Definition (outil), utiliser pour générer des classes qui se conforment à un schéma spécifique"
  - "XML Schema Definition (outil), utiliser pour générer un document de schéma XML"
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Comment&#160;: utiliser l&#39;outil XML Schema Definition pour g&#233;n&#233;rer des classes et des documents de sch&#233;ma XML
L'outil XML Schema Definition \(Xsd.exe\) vous permet de générer un schéma XML qui décrit une classe ou de générer la classe définie par un schéma XML.Les procédures suivantes indiquent comment exécuter ces opérations.  
  
### Pour générer des classes qui se conforment à un schéma spécifique  
  
1.  Ouvrez une invite de commandes.  
  
2.  Passez par exemple le schéma XML en tant qu'argument à l'outil XML Schema Definition, qui crée un ensemble de classes correspondant précisément au schéma XML :  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     L'outil ne peut traiter que les schémas qui référencent la spécification XML du W3C \(World Wide Web Consortium\) du 16 mars 2001.Autrement dit, l'espace de noms du schéma XML doit être http:\/\/www.w3.org\/2001\/XMLSchema, tel qu'illustré par l'exemple suivant.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  Modifiez si nécessaire les classes avec les méthodes, les propriétés ou les champs.Pour plus d'informations sur la modification d'une classe avec des attributs, consultez [Contrôle de la sérialisation XML à l'aide d'attributs](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Il est souvent utile d'examiner le schéma du flux de données XML généré lorsque les instances d'une ou de plusieurs classes sont sérialisées.Par exemple, vous pouvez publier votre schéma pour d'autres utilisateurs ou le comparer à un schéma auquel vous tentez de vous conformer.  
  
#### Pour générer un document de schéma XML à partir d'un ensemble de classes  
  
1.  Compilez la ou les classes dans une DLL.  
  
2.  Ouvrez une invite de commandes.  
  
3.  Passez la DLL en tant qu'argument dans Xsd.exe, par exemple :  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     Le ou les schémas sont écrits et commencent par le nom "schema0.xsd."  
  
## Voir aussi  
 [Outil XML Schema Definition et sérialisation XML](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)   
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [DataSet](frlrfSystemDataDataSetClassTopic)   
 [Outil XML Schema Definition \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)