---
title: "Procedura: confrontare i file di dati del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "file dei risultati del profiler, confrontare"
  - "strumenti di profilatura, procedura per confrontare i file dei risultati del profiler"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Procedura: confrontare i file di dati del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile confrontare i risultati di due diversi file di dati del profiler \(con estensione vsp o vsps\) creando un rapporto o una visualizzazione di confronto \("Diff"\).  Il confronto indica le differenze, le regressioni relative alle prestazioni e i miglioramenti riscontrati da una sessione di profilatura all'altra.  
  
 Il report Diff riporta una visualizzazione tabella dei dati.  La tabella visualizza il delta o modifiche dalla linea di base.  Ciò viene calcolato determinando la differenza tra il vecchio valore, il valore di base e il valore della nuova analisi.  
  
 I confronti di dati del profiler possono essere basati sulle funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione \(IP\) e tipi.  
  
 È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dati nella visualizzazione tabella delle righe che non sono state modificate da una quantità specificata.  
  
### Per creare una visualizzazione file di confronto per un progetto in Esplora prestazioni  
  
1.  All’interno di **Esplora prestazioni** in **Report** selezionare il file di report .vsp o .vsps che si desidera utilizzare come valore di base per il confronto.  
  
2.  Selezionare i file di report con estensione vsp o vsps che si desidera confrontare.  
  
3.  Fare clic con il pulsante destro del mouse su uno dei file selezionati, quindi scegliere **Confronta report**.  
  
### Per confrontare i valori  
  
1.  Selezionare la scheda **Report di confronto** nella finestra Visualizzazione dei report.  
  
2.  Nell'elenco a discesa **Tabella** selezionare una delle funzioni o dei moduli da confrontare.  
  
3.  Nell'elenco a discesa **Colonna** selezionare il valore che si desidera confrontare.  
  
4.  \(facoltativo\) Digitare un valore per **Soglia**.  
  
5.  Scegliere **Applica**.  
  
### Per confrontare file di report  
  
1.  Dal menu **Analizza** scegliere **Confronta report di prestazioni**.  
  
2.  Nella finestra **Seleziona file di analisi da confrontare** esplorare e selezionare il file di analisi con estensione vsp o vsps **File di base** e il **File di confronto** con estensione vsp o vsps.  
  
3.  Fare clic su **OK**.