---
title: "Procedura: Escludere o includere funzioni brevi nella strumentazione | Microsoft Docs"
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
  - "strumenti per la profilatura, eventi strumentazione"
  - "strumenti per la profilatura, includere funzioni brevi"
  - "strumenti per la profilatura, escludere funzioni brevi"
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Escludere o includere funzioni brevi nella strumentazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, gli strumenti di analisi escludono le *piccole funzioni* dalla strumentazione.  Le piccole funzioni sono funzioni brevi che non effettuano alcuna chiamata di funzione.  L'esclusione delle piccole funzioni fornisce un minore sovraccarico di strumentazione che migliora di conseguenza la velocità di strumentazione.  L'esclusione delle piccole funzioni riduce inoltre la dimensione del file di dati relativo all'analisi di prestazione \(.vsp\) e il tempo necessario per l'analisi.  Se le piccole funzioni vengono escluse, il tempo in esse impiegato viene considerato nel tempo esclusivo e inclusivo delle relative funzioni padre.  Le piccole funzioni possono essere escluse o incluse nella strumentazione, come descritto nella procedura seguente.  
  
### Per escludere o includere funzioni brevi nella strumentazione  
  
1.  In **Esplora prestazioni** selezionare **Sessione prestazioni** quindi fare clic con il pulsante destro del mouse e scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
2.  In **Pagine delle proprietà** scegliere le proprietà della scheda **Strumentazione**.  
  
3.  Per escludere le funzioni brevi dalla strumentazione, selezionare **Escludi funzioni brevi da strumentazione**.  Rappresenta l'impostazione predefinita.  
  
     In alternativa  
  
     Per includere le funzioni brevi nella strumentazione, deselezionare **Escludi funzioni brevi da strumentazione**.  
  
4.  Fare clic su **OK**.  
  
## Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)