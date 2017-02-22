---
title: "CA1027: Contrassegnare le enumerazioni con FlagsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1027: Contrassegnare le enumerazioni con FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 I valori di un'enumerazione pubblica sono potenze di due o combinazioni di altri valori definiti nell'enumerazione e l'attributo <xref:System.FlagsAttribute?displayProperty=fullName> non è presente.  Per ridurre i falsi positivi, questa regola non segnala una violazione per le enumerazioni con valori contigui.  
  
## Descrizione della regola  
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate.  Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le relative costanti denominate possono essere combinate in modo significativo.  Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia di quali risorse del giorno sono disponibili.  Se la disponibilità di ogni risorsa è codificata mediante l'enumerazione con l'attributo <xref:System.FlagsAttribute> presente, è possibile rappresentare qualsiasi combinazione di giorni.  Senza l'attributo, è possibile rappresentare un solo giorno della settimana.  
  
 Per i campi in cui vengono archiviate enumerazioni combinabili, i singoli valori di enumerazione vengono considerati come gruppi di bit all'interno del campo.  Questi campi vengono pertanto definiti anche *campi di bit*.  Per combinare valori di enumerazione per l'archiviazione in un campo di bit, utilizzare gli operatori condizionali Boolean.  Per verificare un campo di bit al fine di determinare se è presente un valore di enumerazione specifico, utilizzare gli operatori logici Boolean.  Affinché i valori di enumerazione vengano archiviati e recuperati correttamente in un campo di bit, ogni valore definito nell'enumerazione deve essere una potenza di due.  In caso contrario, gli operatori logici Boolean non saranno in grado di estrarre i singoli valori di enumerazione archiviati nel campo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se non si desidera che i valori di enumerazione siano combinabili.  
  
## Esempio  
 Nell'esempio riportato di seguito `DaysEnumNeedsFlags` è un'enumerazione che soddisfa i requisiti per l'utilizzo dell'attributo <xref:System.FlagsAttribute>, ma questo attributo non è presente.  L'enumerazione `ColorEnumShouldNotHaveFlag` non presenta potenze di due come valori, ma specifica erroneamente <xref:System.FlagsAttribute>.  Viene pertanto violata la regola [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## Regole correlate  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vedere anche  
 <xref:System.FlagsAttribute?displayProperty=fullName>