---
title: "CA1714: Le enumerazioni con Flags devono avere nomi plurali | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714: Le enumerazioni con Flags devono avere nomi plurali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un'enumerazione pubblica dispone dell'attributo <xref:System.FlagsAttribute?displayProperty=fullName> e il nome non termina per "s".  
  
## Descrizione della regola  
 Ai tipi contrassegnati con <xref:System.FlagsAttribute> sono assegnati nomi plurali perché tale attributo indica che è possibile specificare più valori.  Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere destinata all'utilizzo in un'applicazione in cui è possibile specificare più giorni.  Questa enumerazione dovrà contenere l'attributo <xref:System.FlagsAttribute> e potrebbe essere denominata "Days".  Un'enumerazione simile che consenta di specificare un solo giorno, non conterrà tale attributo e potrebbe essere denominata "Day".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Cambiare il nome dell'enumerazione in una parola plurale o rimuovere l'attributo <xref:System.FlagsAttribute> se non è consentito specificare più valori di enumerazione alla volta.  
  
## Esclusione di avvisi  
 L'esclusione di una violazione è sicura se il nome è una parola plurale, ma non termina per "s".  Se, ad esempio, l'enumerazione di più giorni descritta in precedenza fosse denominata "DaysOfTheWeek", verrebbe violata la logica della regola, ma non lo scopo.  Tali violazioni devono essere escluse.  
  
## Regole correlate  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vedere anche  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Progettazione di enum](../Topic/Enum%20Design.md)