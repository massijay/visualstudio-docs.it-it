---
title: "Informazioni sui valori dei dati su conflitti di risorse negli strumenti per la profilatura | Microsoft Docs"
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
  - "profilatura della concorrenza (metodo)"
  - "strumenti per la profilatura, metodo di concorrenza"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informazioni sui valori dei dati su conflitti di risorse negli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il profiling delle risorse contese raccoglie informazioni dettagliate sullo stack delle chiamate ogni volta che ai thread concorrenti in un'applicazione viene imposto di attendere per l'accesso a una risorsa condivisa.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Nei rapporti sui conflitti di risorse viene visualizzato il numero complessivo di conflitti e il tempo totale di attesa di una risorsa per i moduli, le funzioni, le righe di codice sorgente e le istruzioni in cui si è verificata l'attesa.  
  
-   Nei valori inclusivi viene visualizzato il numero complessivo di conflitti che hanno imposto a una funzione di attendere in base a conflitti di risorse e il tempo totale di attesa.  I conflitti causati da funzioni figlio chiamate dalla funzione sono inclusi nei valori inclusivi.  
  
-   Nei valori esclusivi è visualizzato solo il numero di conflitti che hanno imposto a una funzione di attendere e che sono stati causati da codice nel corpo della funzione.  I conflitti causati da funzioni figlio non sono inclusi.  Il tempo esclusivo per la funzione include inoltre solo i tempi di attesa causati da istruzioni nel corpo della funzione.  
  
 Le visualizzazioni dei rapporti sui conflitti di risorse includono inoltre grafici cronologia che mostrano i singoli eventi di conflitto nel tempo e gli stack di chiamate che hanno creato un particolare evento.  Per ulteriori informazioni, vedere uno degli argomenti riportati di seguito:  
  
-   [Visualizzazione Dettagli thread](../profiling/thread-details-view-contention-data.md)  
  
-   [Visualizzazione Dettagli risorsa](../profiling/resource-details-view-contention-data.md)  
  
 Per ulteriori informazioni sulla seconda modalità di profilatura della concorrenza, vedere [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md).