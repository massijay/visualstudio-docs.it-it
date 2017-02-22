---
title: "Operatori di ricerca avanzati nelle espressioni di ricerca | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visualizzatore della Guida 2.0, ricerca di codice"
  - "Visualizzatore della Guida 2.0, ricerca di codice in base al linguaggio di programmazione"
  - "Visualizzatore della Guida 2.0, ricerca di parole chiave"
  - "Visualizzatore della Guida 2.0, ricerca di titoli"
  - "ricerca di codice [Visualizzatore della Guida 2.0]"
  - "ricerca di titoli [Visualizzatore della Guida 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Operatori di ricerca avanzati nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'utilizzo degli operatori di ricerca avanzati consente di perfezionare la ricerca di contenuto creando espressioni di ricerca più complesse da quelle più semplici.  Come illustrato nella tabella che segue, questi operatori limitano il contesto in cui una query viene eseguita.  
  
> [!WARNING]
>  È necessario immettere gli operatori di ricerca avanzati con i due punti finali senza inserire alcuno spazio prima dei due punti in modo che il motore di ricerca li riconosca.  
  
|Per eseguire la ricerca|Utilizzare|Esempio|Risultato|  
|-----------------------------|----------------|-------------|---------------|  
|Un termine nel titolo dell'argomento|Titolo:|title:binaryreader|Argomenti contenenti “binaryreader” nei titoli.|  
|Un termine in un esempio di codice|codice:|codice: readdouble|Argomenti contenenti "readdouble" nel codice di esempio.|  
|Un termine in un esempio di un linguaggio di programmazione specifico|codice: vb:|codice: vb:string|Argomenti contenenti “stringa” in un esempio di Visual Basic.|  
|Un argomento associato a una specifica parola chiave dell'indice|parola chiave:|parola chiave: readbyte|Argomenti associati alla parola chiave di indice “readbyte”.|  
  
 È possibile utilizzare code: operator per trovare il contenuto su uno dei diversi linguaggi di programmazione, ma restituisce risultati solo per il contenuto contrassegnato con un linguaggio di programmazione specifico.  Nella tabella seguente sono elencati i linguaggi di programmazione supportati da questo operatore:  
  
|Linguaggio di programmazione|Utilizzare|  
|----------------------------------|----------------|  
|Visual Basic|codice: VB<br /><br /> oppure<br /><br /> code:visualbasic|  
|C\#|codice: c\#<br /><br /> oppure<br /><br /> codice: csharp|  
|C\+\+|codice: cpp<br /><br /> oppure<br /><br /> codice: C\+\+<br /><br /> oppure<br /><br /> codice: cplusplus|  
|F\#|codice: f\#<br /><br /> oppure<br /><br /> codice: fsharp|  
|JavaScript|code:javascript<br /><br /> oppure<br /><br /> codice: js|  
|XAML|codice: xaml|  
  
## Vedere anche  
 [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md)   
 [Suggerimenti per la ricerca full\-text](../ide/full-text-search-tips.md)