---
title: "Impl&#233;mentation de la logique m&#233;tier (LINQ to SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Impl&#233;mentation de la logique m&#233;tier (LINQ to SQL)
Le terme "logique métier" utilisé dans cette rubrique désigne toutes les règles ou tests de validation personnalisés que vous appliquez aux données avant de les insérer, de les mettre à jour ou de les supprimer de la base de données.  La logique métier est parfois également désignée par le terme "règles métier" ou "logique de domaine". Dans les applications multicouches, elle est généralement conçue comme une couche logique de manière à ce qu'elle puisse être modifiée indépendamment de la couche Présentation ou de la couche Data Access.  La logique métier peut être appelée par la couche Data Access avant ou après toute mise à jour, insertion ou suppression de données dans la base de données.  
  
 La logique métier peut être aussi simple qu'une validation de schéma effectuée pour vérifier que le type du champ est compatible avec le type de la colonne de table.  Elle peut également être constituée d'un ensemble d'objets qui interagissent de manières arbitrairement complexes.  Les règles peuvent être implémentées comme des procédures stockées sur la base de données ou comme des objets en mémoire.  Quelle que soit la manière dont la logique métier est implémentée, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vous permet d'utiliser des classes partielles et des méthodes partielles pour séparer la logique métier du code d'accès aux données.  
  
## Comment LINQ to SQL appelle votre logique métier  
 Lorsque vous générez une classe d'entité au moment du design, soit manuellement, soit à l'aide de [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou de SQLMetal, elle est définie comme une classe partielle.  Cela signifie que, dans un fichier de code distinct, vous pouvez définir une autre partie de la classe d'entité qui contient votre logique métier personnalisée.  Lors de la compilation, les deux parties sont fusionnées en une classe unique. Mais si vous devez régénérer vos classes d'entité à l'aide de [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou SQLMetal, vous pouvez le faire et votre partie de la classe ne sera pas modifiée.  
  
 Les classes partielles qui définissent des entités et le <xref:System.Data.Linq.DataContext> contiennent des méthodes partielles.  Ce sont les points d'extensibilité que vous pouvez utiliser pour appliquer votre logique métier avant et après toute mise à jour, insertion ou suppression pour une entité ou une propriété d'entité.  Les méthodes partielles peuvent être comparées à des événements de compilation.  Le générateur de code définit une signature de méthode et appelle les méthodes dans les accesseurs de propriété get et set, le constructeur `DataContext`, et dans certains cas en arrière\-plan lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé.  Toutefois, si vous n'implémentez pas de méthode partielle particulière, toutes les références à celle\-ci et la définition sont supprimées à la compilation.  
  
 Dans la définition d'implémentation que vous écrivez dans votre fichier de code distinct, vous pouvez exécuter toute logique personnalisée requise.  Vous pouvez utiliser votre classe partielle elle\-même comme votre couche de domaine, ou vous pouvez l'appeler à partir de votre définition d'implémentation de la méthode partielle dans un objet ou des objets séparés.  Dans l'un et l'autre cas, votre logique métier est nettement séparée de votre code d'accès aux données et de votre code de couche Présentation.  
  
## Présentation détaillée des points d'extensibilité  
 L'exemple suivant montre des parties du code généré par [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour la classe `DataContext` qui a deux tables : `Customers` et `Orders`.  Notez que les méthodes Insert, Update et Delete sont définies pour chaque table de la classe.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Si vous implémentez les méthodes Insert, Update et Delete dans votre classe partielle, le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les appelle à la place de ses propres méthodes par défaut lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé.  Cela vous permet de substituer le comportement par défaut pour les opérations de création \/ lecture \/ mise à jour \/ suppression.  Pour plus d'informations, consultez [Procédure pas à pas : personnalisation du comportement d'insertion, de mise à jour et de suppression de classes d'entité](../Topic/Walkthrough:%20Customizing%20the%20insert,%20update,%20and%20delete%20behavior%20of%20entity%20classes.md).  
  
 La méthode `OnCreated` est appelée dans le constructeur de classe.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 Les classes d'entité ont trois méthodes qui sont appelées par le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lorsque l'entité est créée, chargée et validée \(lorsque `SubmitChanges` est appelé\).  Les classes d'entité ont également deux méthodes partielles pour chaque propriété, l'une est appelée avant que la propriété soit définie et l'autre après.  L'exemple de code suivant illustre quelques\-unes des méthodes générées pour la classe `Customer` :  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Les méthodes sont appelées dans l'accesseur set de propriété comme illustré dans l'exemple suivant pour la propriété `CustomerID` :  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 Dans votre partie de la classe, vous écrivez une définition d'implémentation de la méthode.  Dans [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], après avoir tapé `partial` vous consulterez IntelliSense pour les définitions de méthode dans l'autre partie de la classe.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer   
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Pour plus d'informations sur l'ajout de la logique métier à votre application à l'aide des méthodes partielles, consultez les rubriques suivantes :  
  
 [Procédure : ajouter une validation à des classes d'entité](../Topic/How%20to:%20Add%20validation%20to%20entity%20classes.md)  
  
 [Procédure pas à pas : personnalisation du comportement d'insertion, de mise à jour et de suppression de classes d'entité](../Topic/Walkthrough:%20Customizing%20the%20insert,%20update,%20and%20delete%20behavior%20of%20entity%20classes.md)  
  
 [Procédure pas à pas : ajout d'une validation à des classes d'entité](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)  
  
## Voir aussi  
 [Classes et méthodes partielles](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)   
 [LINQ to SQL Tools dans Visual Studio](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio2.md)   
 [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)