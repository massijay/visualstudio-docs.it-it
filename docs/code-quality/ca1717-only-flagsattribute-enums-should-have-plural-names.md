---
title: "CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali | Microsoft Docs"
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
  - "CA1717"
  - "OnlyFlagsEnumsShouldHavePluralNames"
helpviewer_keywords: 
  - "OnlyFlagsEnumsShouldHavePluralNames"
  - "CA1717"
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|  
|CheckId|CA1717|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un'enumerazione visibile esternamente termina con una parola plurale e l'enumerazione non è contrassegnata con l'attributo <xref:System.FlagsAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 In base alle convenzioni di denominazione, un nome plurale in un'enumerazione indica che è possibile specificare più valori di enumerazione alla volta.  La presenza di <xref:System.FlagsAttribute> indica ai compilatori che l'enumerazione deve essere considerata come un campo di bit che consente l'esecuzione di operazioni bit per bit sull'enumerazione.  
  
 Se è possibile specificare un solo valore di enumerazione alla volta, il nome dell'enumerazione dovrà essere una parola singolare.  Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere destinata all'utilizzo in un'applicazione in cui è possibile specificare più giorni.  Questa enumerazione dovrà contenere l'attributo <xref:System.FlagsAttribute> e potrebbe essere denominata "Days".  Un'enumerazione simile che consenta di specificare un solo giorno, non conterrà tale attributo e potrebbe essere denominata "Day".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo, si riduce il tempo necessario per l'apprendimento di una nuova libreria software e i clienti possono confidare nel fatto che la libreria sia stata sviluppata da esperti nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Cambiare il nome dell'enumerazione in una parola singolare o aggiungere l'attributo <xref:System.FlagsAttribute>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il nome termina con una parola singolare.  
  
## Regole correlate  
 [CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vedere anche  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Progettazione di enum](../Topic/Enum%20Design.md)