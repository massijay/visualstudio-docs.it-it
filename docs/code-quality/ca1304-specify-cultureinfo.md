---
title: "CA1304: Specificare CultureInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
helpviewer_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1304: Specificare CultureInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|CheckId|CA1304|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro <xref:System.Globalization.CultureInfo?displayProperty=fullName> e il metodo o il costruttore non chiama l'overload che accetta il parametro <xref:System.Globalization.CultureInfo>.  Questa regola ignora le chiamate ai seguenti metodi:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Descrizione della regola  
 Quando non viene fornito un oggetto <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName>, il valore predefinito fornito dal membro di overload potrebbe non produrre l'effetto desiderato su tutte le impostazioni locali.  Inoltre, i membri [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] scelgono le impostazioni cultura e la formattazione predefinite in base a supposizioni che potrebbero non essere corrette per il codice.  Per assicurare che il codice funzioni come previsto negli scenari correnti, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle seguenti linee guida:  
  
-   Se il valore verrà visualizzato dall'utente, utilizzare le impostazioni cultura correnti.  Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Se il software archivierà e accederà al valore, ovvero il valore verrà mantenuto in un file o in un database, utilizzare le impostazioni cultura invarianti.  Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Se non si conosce la destinazione del valore, richiedere al provider o al consumer di dati di specificare le impostazioni cultura.  
  
 Si noti che la proprietà <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene utilizzata solo per recuperare le risorse localizzate utilizzando un'istanza della classe <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Anche se il comportamento predefinito del membro di overload è appropriato alle esigenze, è consigliabile chiamare in modo esplicito l'overload specifico delle impostazioni cultura affinché il codice risulti autodocumentato e di più agevole manutenzione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare l'overload che accetta un oggetto <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle linee guida elencate in precedenza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se si è certi che il provider predefinito delle impostazioni cultura o del formato sia la scelta corretta e quando la gestibilità del codice non è una priorità importante per lo sviluppo.  
  
## Esempio  
 Nel seguente esempio, `BadMethod` causa due violazioni di questa regola.  `GoodMethod` corregge la prima violazione passando le impostazioni cultura invarianti a System.String.Compare e corregge la seconda violazione passando le impostazioni cultura correnti a <xref:System.String.ToLower%2A> poiché `string3` viene visualizzato dall'utente.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'effetto delle impostazioni cultura correnti sull'oggetto <xref:System.IFormatProvider> predefinito selezionato dal tipo <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **4\/6\/1900 12:15:12 PM 04\/06\/1900 12:15:12**   
## Regole correlate  
 [CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## Vedere anche  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/it-it/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)