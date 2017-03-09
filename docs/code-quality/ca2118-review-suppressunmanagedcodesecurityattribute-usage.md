---
title: "CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un membro o un tipo pubblico o protetto presenta l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 L'oggetto <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifica il comportamento del sistema di sicurezza predefinito per i membri che eseguono codice non gestito mediante interoperabilità COM o chiamata al sistema operativo.  In genere, il sistema esegue un [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) per l'autorizzazione al codice non gestito.  Questa richiesta viene effettuata in fase di esecuzione per ogni chiamata al membro e verifica l'autorizzazione di ogni chiamante nello stack di chiamate.  Quando l'attributo è presente, il sistema effettua una [Link Demands](../Topic/Link%20Demands.md) per l'autorizzazione: le autorizzazioni del chiamante immediato vengono controllate quando il chiamante viene compilato tramite JIT.  
  
 Questo attributo viene principalmente utilizzato per aumentare le prestazioni. L'aumento delle prestazioni, tuttavia, comporta notevoli rischi in termini di sicurezza.  Se si inserisce l'attributo su membri pubblici che chiamano metodi nativi, i chiamanti nello stack di chiamate diversi dal chiamante immediato non necessitano dell'autorizzazione al codice non gestito per eseguire tale codice.  A seconda delle azioni del membro pubblico e della gestione dell'input, è possibile che venga consentito a chiamanti non attendibili di accedere a funzionalità normalmente limitate al codice attendibile.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] si basa sui controlli di sicurezza per impedire ai chiamanti di ottenere l'accesso diretto allo spazio degli indirizzi del processo corrente.  Poiché questo attributo ignora la sicurezza normale, il codice comporta una grave minaccia se può essere utilizzato per leggere o scrivere nella memoria del processo.  Si noti che il rischio non è limitato ai metodi che forniscono intenzionalmente accesso alla memoria del processo, ma è presente in qualsiasi scenario in cui codice dannoso possa ottenere l'accesso in qualsiasi modo, ad esempio fornendo input improvviso, non corretto o non valido.  
  
 I criteri di sicurezza predefiniti non concedono l'autorizzazione al codice non gestito a un assembly, a meno che non venga eseguito dal computer locale o sia membro di uno dei gruppi riportati di seguito:  
  
-   Gruppo di codice dell'area Risorse del Computer  
  
-   Gruppo di codice Nome sicuro Microsoft  
  
-   Gruppo di codice Nome sicuro ECMA  
  
## Come correggere le violazioni  
 Rivedere attentamente il codice per assicurarsi che questo attributo sia assolutamente necessario.  Se non si ha familiarità con la sicurezza del codice non gestito o non si comprendono le implicazioni di sicurezza derivanti dall'utilizzo di questo attributo, rimuoverlo dal codice.  Se l'attributo è necessario, è necessario assicurarsi che i chiamanti non utilizzino il codice in modo dannoso.  Se il codice non ha autorizzazione a eseguire codice non gestito, questo attributo non ha effetto e deve essere rimosso.  
  
## Esclusione di avvisi  
 Per escludere un avviso da questa regola in modo sicuro, è necessario assicurarsi che il codice non fornisca ai chiamanti accesso a operazioni native o risorse che possano essere utilizzate in modo distruttivo.  
  
## Esempio  
 Nell'esempio riportato di seguito viene violato il codice.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito, il metodo `DoWork` fornisce un percorso del codice accessibile pubblicamente al metodo di chiamata al sistema operativo `FormatHardDisk`.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito, il metodo pubblico `DoDangerousThing` causa una violazione.  Per risolvere la violazione, `DoDangerousThing` deve essere reso privato e l'accesso a esso deve essere effettuato tramite un metodo pubblico protetto da una richiesta di sicurezza, come illustrato dal metodo `DoWork`.  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## Vedere anche  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/it-it/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Link Demands](../Topic/Link%20Demands.md)