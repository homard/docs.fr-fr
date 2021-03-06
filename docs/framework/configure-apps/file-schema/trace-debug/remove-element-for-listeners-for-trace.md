---
title: '&lt;supprimer&gt; élément pour &lt;écouteurs&gt; pour &lt;trace&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 54fd529c571c8e8cf43c5dabe2398ae4a6cf4f11
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030533"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;supprimer&gt; élément pour &lt;écouteurs&gt; pour &lt;trace&gt;
Supprime un écouteur de la **écouteurs** collection.  
  
 \<configuration>  
\<System.Diagnostics >  
\<trace >  
\<écouteurs >  
\<remove>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Le nom de l’écouteur à supprimer de la **écouteurs** collection.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un écouteur qui collecte, stocke et achemine les messages. Les écouteurs dirigent la sortie de traçage vers une cible appropriée.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`trace`|Configure le service de trace ASP.NET.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Suppression de la <xref:System.Diagnostics.DefaultTraceListener> à partir de la `Listeners` collection modifie le comportement de la <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> méthodes. Appeler un `Assert` ou `Fail` méthode aboutit généralement à l’affichage d’une boîte de message, mais la boîte de message s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans le `Listeners` collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment supprimer l’écouteur de trace par défaut de la trace **écouteurs** collection.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
