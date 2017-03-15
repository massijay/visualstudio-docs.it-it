---
title: "CA1305: Specificare IFormatProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1305: Specificare IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro <xref:System.IFormatProvider?displayProperty=fullName> e tale metodo o costruttore non chiama l'overload che accetta il parametro <xref:System.IFormatProvider>.  Questa regola ignora le chiamate ai metodi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] di cui è noto il fatto che ignorano il parametro <xref:System.IFormatProvider> oltre ai seguenti metodi:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Descrizione della regola  
 Quando non viene fornito un oggetto <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider>, il valore predefinito fornito dal membro di overload potrebbe non produrre l'effetto desiderato su tutte le impostazioni locali.  Inoltre, i membri [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] scelgono le impostazioni cultura e la formattazione predefinite in base a supposizioni che potrebbero non essere corrette per il codice.  Per garantire che il codice funzioni come previsto negli scenari correnti, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle seguenti linee guida:  
  
-   Se il valore verrà visualizzato dall'utente, utilizzare le impostazioni cultura correnti.  Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Se sarà il software ad archiviare e accedere al valore, ossia se il valore verrà mantenuto in un file o database, utilizzare le impostazioni cultura invarianti.  Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Se non si conosce la destinazione del valore, richiedere al provider o al consumer di dati di specificare le impostazioni cultura.  
  
 Si noti che la proprietà <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene utilizzata solo per recuperare le risorse localizzate utilizzando un'istanza della classe <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Anche se il comportamento predefinito del membro di overload è appropriato alle esigenze, è consigliabile chiamare in modo esplicito l'overload specifico delle impostazioni cultura affinché il codice risulti autodocumentato e di più agevole manutenzione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare l'overload che accetta un oggetto <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle linee guida elencate in precedenza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se si è certi che il provider predefinito delle impostazioni cultura o del formato sia la scelta corretta e quando la gestibilità del codice non è una priorità importante per lo sviluppo.  
  
## Esempio  
 Nel seguente esempio, `BadMethod` causa due violazioni di questa regola.  `GoodMethod` corregge la prima violazione passando le impostazioni cultura invarianti a <xref:System.String.Compare%2A> e corregge la seconda violazione passando le impostazioni cultura correnti a <xref:System.String.ToLower%2A> poiché `string3` viene visualizzato dall'utente.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'effetto delle impostazioni cultura correnti sull'oggetto <xref:System.IFormatProvider> predefinito selezionato dal tipo <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **4\/6\/1900 12:15:12 PM 04\/06\/1900 12:15:12**   
## Regole correlate  
 [CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## Vedere anche  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/it-it/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)