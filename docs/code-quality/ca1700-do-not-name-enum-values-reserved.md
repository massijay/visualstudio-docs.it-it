---
title: "CA1700: Non denominare &#39;Reserved&#39; i valori di enumerazione | Microsoft Docs"
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
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1700: Non denominare &#39;Reserved&#39; i valori di enumerazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un membro di enumerazione contiene la parola "reserved".  
  
## Descrizione della regola  
 Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura.  La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale.  Non è opportuno presupporre che gli utenti ignorino un membro solo perché il relativo nome contiene "reserved" né che leggano o si attengano alla documentazione.  Inoltre, poiché i membri riservati vengono visualizzati in visualizzatori oggetti e in ambienti di sviluppo integrati, è possibile che si crei confusione su quali membri vengono effettivamente utilizzati.  
  
 Anziché utilizzare un membro riservato, aggiungere un nuovo membro all'enumerazione nella versione futura.  Nella maggior parte dei casi, l'aggiunta del nuovo membro non costituisce una modifica sostanziale, purché l'aggiunta non comporti la modifica dei valori dei membri originali.  
  
 In alcuni casi, l'aggiunta di un membro costituisce una modifica sostanziale anche se i membri originali mantengono i relativi valori originali.  Principalmente il nuovo membro non può essere restituito da percorsi di codice esistenti senza causare l'interruzione dei chiamanti che utilizzano un'istruzione `switch` \(`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) sul valore restituito che comprende l'intero elenco di membri che generano un'eccezione nel caso predefinito.  Un secondo problema è costituito dal fatto che il codice del client potrebbe non essere in grado di gestire la modifica di comportamento da metodi di reflection quali <xref:System.Enum.IsDefined%2A?displayProperty=fullName>.  Di conseguenza, se il nuovo membro deve essere restituito da metodi esistenti o se si verifica un'incompatibilità nota tra applicazioni a causa del ridotto utilizzo della reflection, l'unica soluzione è:  
  
1.  Aggiungere una nuova enumerazione contenente i membri originali e nuovi.  
  
2.  Contrassegnare l'enumerazione originale con l'attributo <xref:System.ObsoleteAttribute?displayProperty=fullName>.  
  
 Seguire la stessa procedura per qualsiasi membro o tipo visibile esternamente che espone l'enumerazione originale.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o rinominare il membro.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura per un membro attualmente utilizzato oppure per le librerie fornite in precedenza.  
  
## Regole correlate  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)