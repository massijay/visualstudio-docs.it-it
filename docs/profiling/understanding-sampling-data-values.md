---
title: "Informazioni sui valori dei dati di campionamento negli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilatura del campionamento (metodo)"
  - "strumenti per la profilatura, campionamento"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informazioni sui valori dei dati di campionamento negli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo di profilatura di *campionamento* degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interrompe il processore del computer a intervalli impostati e raccoglie lo stack delle chiamate di funzione.  Uno *stack di chiamate* è una struttura dinamica che archivia le informazioni sulle funzioni in esecuzione sul processore.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 L'analisi del profiler determina se il processore esegue il codice nel processo di destinazione.  Se il processore non esegue il codice nel processo di destinazione, il campione viene ignorato.  
  
 Se il processore esegue il codice di destinazione, il profiler incrementa i numeri dei campioni per ogni funzione nello stack di chiamate.  Nel momento in cui è stato raccolto il campione, una sola funzione nello stack di chiamate sta eseguendo codice.  Le altre funzioni dello stack sono elementi padre nella gerarchia delle chiamate di funzione in attesa della restituzione degli elementi figlio.  
  
 Per l'evento di esempio, il profiler incrementa il numero del campione *esclusivo* della funzione che esegue effettivamente le istruzioni.  Poiché un campione esclusivo fa parte anche dei campioni totali \(*inclusivi*\) della funzione, viene incrementato anche il numero del campione inclusivo della funzione.  
  
 Il profiler incrementa il numero del campione inclusivo di tutte le altre funzioni dello stack di chiamate.  
  
## Campioni inclusivi  
 Numero totale dei campioni raccolti durante l'esecuzione della funzione di destinazione.  
  
 Sono compresi i campioni raccolti durante l'esecuzione diretta del codice della funzione e i campioni raccolti durante l'esecuzione delle funzioni figlio chiamate dalla funzione di destinazione.  
  
## Campioni esclusivi  
 Numero totale dei campioni raccolti durante l'esecuzione diretta delle istruzioni della funzione di destinazione.  
  
 Nei campioni esclusivi non sono compresi i campioni raccolti durante l'esecuzione delle funzioni chiamate dalla funzione di destinazione.  
  
## Percentuale campioni inclusivi  
 Percentuale del numero totale di campioni inclusivi nell'esecuzione dell'analisi che sono campioni inclusivi della funzione o dell'intervallo di dati.  
  
## Percentuale campioni esclusivi  
 Percentuale del numero totale di campioni esclusivi nell'esecuzione dell'analisi che sono campioni esclusivi della funzione o dell'intervallo di dati.  
  
## Vedere anche  
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)   
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)