---
title: Guide pratique pour écrire des données d’objet dans un fichier XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: b8fb60640c9bdc0337d45b6901b1be3979dbac1f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259754"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Guide pratique pour écrire des données d’objet dans un fichier XML (C#)
Cet exemple écrit l’objet d’une classe dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Exemple  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 La classe doit disposer d’un constructeur public sans paramètres.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   La classe qui est sérialisée n’a pas de constructeur public sans paramètres.  
  
-   Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).  
  
-   Le chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
-   Le disque est plein (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur. Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamWriter>  
- [Guide pratique : lire des données d’objet à partir d’un fichier XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
- [Sérialisation (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)
