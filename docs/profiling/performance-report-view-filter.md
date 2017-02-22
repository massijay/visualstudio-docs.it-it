---
title: "Filtro di visualizzazione dei report degli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, filtro di visualizzazione dei report del profiler"
  - "filtro di visualizzazione dei report del profiler, strumenti per la profilatura"
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Filtro di visualizzazione dei report degli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La finestra del filtro di visualizzazione dei report del profiler si trova nella parte superiore della finestra Report di prestazioni.  Se non è visibile, fare clic sul pulsante **Mostra filtro**.  
  
 È possibile modificare ogni clausola del filtro per definire ulteriormente i risultati.  Nel generatore di filtri sono disponibili le seguenti colonne.  
  
|Elemento del filtro|Descrizione|  
|-------------------------|-----------------|  
|And\/Or|Selezionare **And** se questa clausola e la successiva devono essere entrambe soddisfatte per restituire un risultato.  Selezionare **Or** se questa clausola o la successiva deve essere soddisfatta per restituire un risultato.|  
|Campo|Selezionare il campo da utilizzare nella clausola di filtro dall'elenco di campi dati disponibile nel file di rapporto corrente.|  
|Operatore|Scegliere l'operatore che specifica la relazione da impostare tra il campo e il valore.<br /><br /> \= Uguale a<br /><br /> \<\> Non uguale a<br /><br /> \< Minore di<br /><br /> \> Maggiore di<br /><br /> \<\= Minore o uguale a<br /><br /> \>\= Maggiore o uguale a|  
|Valore|Selezionare o immettere il valore da cercare.  Per alcuni campi è presente l'elenco dei valori disponibili.|  
  
 È possibile aggiungere le clausole di filtro finché non vengono raggiunti i risultati migliori.  Fare clic su **Esegui filtro** per applicare il filtro al file di dati.  
  
 Dalla visualizzazione del rapporto **Contrassegni**, è possibile generare le clausole di filtro per limitare i dati da includere nelle visualizzazioni di rapporto ai dati raccolti tra due contrassegni.  Selezionare i contrassegni da utilizzare come inizio e fine dei dati per il rapporto, fare clic con il pulsante destro del mouse e selezionare **Aggiungi filtro in contrassegni** o **Aggiungi filtro in timestamp**.  Entrambi i filtri limitano i dati del file di dati corrente allo stesso modo. L'opzione **Aggiungi filtro in contrassegni** può essere applicata ad altri file con estensione vsp.  
  
 Per salvare il filtro, fare clic su **Esporta filtro** nella barra degli strumenti di Report di prestazioni e specificare un percorso e un nome file per il file vspf.  Per caricare un filtro precedentemente salvato, fare clic su **Importa filtro** e individuare il file del filtro salvato.  I file di filtro possono essere utilizzati anche per filtrare file di dati nei computer in cui sono installati gli strumenti di profilatura autonomi.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
## Vedere anche  
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)