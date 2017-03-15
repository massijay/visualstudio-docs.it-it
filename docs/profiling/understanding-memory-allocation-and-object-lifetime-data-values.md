---
title: "Informazioni sull&#39;allocazione di memoria e sui valori dei dati di durata di un oggetto negli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET (metodo di profilatura della memoria)"
  - "strumenti per la profilatura, metodo memoria .NET"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Informazioni sull&#39;allocazione di memoria e sui valori dei dati di durata di un oggetto negli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo di profilo *Allocazione di memoria .NET* di Strumenti di profilatura [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raccoglie informazioni sulle dimensioni e il numero di oggetti creati in un'allocazione o eliminati in modo permanente in un Garbage Collection e informazioni aggiuntive sullo *stack* di chiamate di funzione quando si è verificato l'evento.  Uno *stack di chiamate* è una struttura dinamica che archivia le informazioni sulle funzioni in esecuzione sul processore.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Il profiler di memoria interrompe il processore del computer ad ogni allocazione di un oggetto .NET Framework in un'applicazione profilata.  Quando vengono raccolti dati sulla durata degli oggetti, il profiler interrompe il processore dopo ogni Garbage Collection di .NET Framework.  I dati vengono aggregati per ciascuna funzione profilata e per ogni tipo di oggetto.  
  
## Dati di allocazione  
 Quando si verifica un evento .memory, vengono incrementati i conteggi e le dimensioni totali degli oggetti di memoria eliminati in modo permanente o allocati.  
  
 Quando si verifica un evento di allocazione .memory, il profiler incrementa i numeri dei campioni per ogni funzione nello stack di chiamate.  Quando vengono raccolti i dati, solo una funzione nello stack di chiamate esegue effettivamente il codice nel corpo della funzione.  Le altre funzioni dello stack sono elementi padri nella gerarchia delle chiamate di funzione in attesa della restituzione delle funzioni chiamate.  
  
-   Per l'evento di allocazione, il profiler incrementa il numero del campione *esclusivo* della funzione che esegue effettivamente le istruzioni.  Poiché un campione esclusivo fa parte anche dei campioni totali \(*inclusivi*\) della funzione, viene incrementato anche il numero del campione inclusivo della funzione.  
  
-   Il profiler incrementa il numero del campione inclusivo di tutte le altre funzioni dello stack di chiamate.  
  
## Dati sulla durata  
 Il Garbage Collector di .NET Framework gestisce l'allocazione e il rilascio di memoria per l'applicazione.  Per ottimizzare le prestazioni del Garbage Collector, l'heap gestito è diviso in tre generazioni: 0, 1 e 2.  Il Garbage Collector del runtime archivia i nuovi oggetti nella generazione 0.  Gli oggetti non raccolti vengono promossi e archiviati nelle generazioni 1 e 2.  
  
 Il Garbage Collector recupera memoria deallocando un'intera generazione di oggetti.  Per gli oggetti creati dall'applicazione profilata, nella visualizzazione Durata oggetti vengono visualizzati il numero e le dimensioni degli oggetti e la generazione al momento del recupero.