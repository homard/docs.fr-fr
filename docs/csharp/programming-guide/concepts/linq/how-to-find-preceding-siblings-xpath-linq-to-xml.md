---
title: Guide pratique pour rechercher les frères précédents (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: d2bd34db7bd839e50ec3e77819230f5f6410b73e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43787116"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>Guide pratique pour rechercher les frères précédents (XPath-LINQ to XML) (C#)
Cette rubrique compare l’axe `preceding-sibling` XPath à l’axe <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> enfant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 L’expression XPath est la suivante :  
  
 `preceding-sibling::*`  
  
 Notez que les résultats de <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> et <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> sont dans l'ordre du document.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant recherche l'élément `FullAddress`, puis récupère les éléments précédents à l'aide de l'axe `preceding-sibling`.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
