---
title: "CA1306: Specificare le impostazioni locali per i tipi di dati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1306: Specificare le impostazioni locali per i tipi di dati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo o un costruttore ha creato una o più istanze <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> e non ha impostato in modo esplicito la proprietà Locale \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\).  
  
## Descrizione della regola  
 Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e il criterio di ordinamento.  Quando si crea un oggetto <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, è opportuno definire in modo esplicito le impostazioni locali.  Per impostazione predefinita, le impostazioni locali per questi tipi sono rappresentate dalle impostazioni cultura attuali.  Per i dati archiviati in un database o in un file e condivisi globalmente, le impostazioni locali devono essere, in condizioni normali, impostate sulle impostazioni cultura invarianti \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\).  Quando i dati sono condivisi tra più impostazioni cultura, l'utilizzo delle impostazioni locali predefinite può causare la presentazione o l'interpretazione errata dell'oggetto <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, definire in modo esplicito le impostazioni locali per l'oggetto <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la libreria o l'applicazione è destinata a un ridotto pubblico locale, i dati non sono condivisi o l'impostazione predefinita produce il comportamento desiderato in tutti gli scenari supportati.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono create due istanze di <xref:System.Data.DataTable>.  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## Vedere anche  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>