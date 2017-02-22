---
title: "Operatori logici nelle espressioni di ricerca | Microsoft Docs"
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
  - "Help Viewer 2.0, operatori logici nella ricerca"
  - "operatori logici nella ricerca [Help Viewer 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Operatori logici nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'utilizzo degli operatori logici consente di perfezionare la ricerca di contenuto creando espressioni di ricerca più complesse da quelle più semplici.  Come illustrato nella tabella che segue, l'utilizzo degli operatori logici permette di specificare come combinare più condizioni di ricerca in una query di ricerca.  
  
> [!IMPORTANT]
>  È necessario immettere gli operatori logici interamente in caratteri maiuscoli in modo che il motore di ricerca li riconosca.  
  
|Per eseguire la ricerca|Utilizzare|Esempio|Risultato|  
|-----------------------------|----------------|-------------|---------------|  
|Entrambi i termini nello stesso argomento|AND|dib AND tavolozza|Argomenti contenenti sia "dib" che "palette".|  
|Entrambi i termini in un argomento|OR|raster OR vettore|Argomenti contenenti "raster" o "vector".|  
|Primo termine senza il secondo termine nello stesso argomento|NOT|"sistema operativo" NOT DOS|Argomenti contenenti "sistema operativo" ma non "DOS".|  
|Entrambi i termini, insieme in un argomento|NEAR|utente NEAR kernel|Argomenti contenenti "utente" in prossimità di "kernel".|  
  
## Vedere anche  
 [Suggerimenti per la ricerca full\-text](../ide/full-text-search-tips.md)   
 [Individuare informazioni](../ide/locate-information.md)