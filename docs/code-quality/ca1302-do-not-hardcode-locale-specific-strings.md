---
title: "CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo utilizza una stringa letterale che rappresenta parte del percorso di determinate cartelle di sistema.  
  
## Descrizione della regola  
 L'enumerazione <xref:System.Environment.SpecialFolder?displayProperty=fullName> contiene membri che fanno riferimento a cartelle di sistema speciali.  I percorsi di queste cartelle possono presentare valori diversi in sistemi operativi diversi. È possibile modificare alcuni dei percorsi e i percorsi sono localizzati.  Un esempio di cartella speciale è la cartella di sistema, "C:\\WINDOWS\\system32" in [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] ma "C:\\WINNT\\system32" in [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)].  Il metodo <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> restituisce i percorsi associati all'enumerazione <xref:System.Environment.SpecialFolder>.  I percorsi restituiti dal metodo <xref:System.Environment.GetFolderPath%2A> sono localizzati e appropriati per il computer in uso.  
  
 Questa regola rappresenta in formato token i percorsi delle cartelle recuperati mediante il metodo <xref:System.Environment.GetFolderPath%2A> in livelli di directory separati.  Ogni valore letterale stringa viene confrontato con i token.  Se viene trovata una corrispondenza, viene presupposto che un metodo stia compilando una stringa che fa riferimento al percorso di sistema associato al token.  A scopo di portabilità e localizzabilità, utilizzare il metodo <xref:System.Environment.GetFolderPath%2A> per recuperare i percorsi delle cartelle di sistema speciali anziché utilizzare stringhe letterali.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, recuperare la posizione mediante il metodo <xref:System.Environment.GetFolderPath%2A>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la stringa letterale non viene utilizzata per fare riferimento a uno dei percorsi di sistema associati all'enumerazione <xref:System.Environment.SpecialFolder>.  
  
## Esempio  
 Nell'esempio riportato di seguito viene compilato il percorso della cartella Application Data comune, con conseguente generazione di tre avvisi da questa regola.  Nell'esempio viene quindi recuperato il percorso mediante il metodo <xref:System.Environment.GetFolderPath%2A>.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Regole correlate  
 [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)