---
title: "Modifica e continuazione (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "Modifica e continuazione a 64 bit"
  - "debug [Visual Basic], Modifica e continuazione"
  - "Modifica e continuazione [Visual Basic]"
  - "Modifica e continuazione, 64 bit"
  - "Visual Basic, Modifica e continuazione"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# Modifica e continuazione (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifica e continuazione è una funzionalità per il debug di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] che consente di apportare modifiche al codice mentre viene eseguito in modalità di interruzione.  Dopo aver applicato le modifiche al codice, è possibile riprendere l'esecuzione del codice con le nuove modifiche già inserite e verificarne l'effetto.  
  
 La funzionalità Modifica e continuazione può essere utilizzata ogni volta che si attiva la modalità di interruzione.  In modalità di interruzione il puntatore all'istruzione, ovvero la freccia gialla nella finestra del codice sorgente, punta alla riga che verrà eseguita successivamente ed è posizionato in un'istruzione eseguibile all'interno del corpo di un metodo o una proprietà.  In questa modalità è possibile apportare alle istruzioni eseguibili quasi tutti i tipi di modifiche, le quali verranno incorporate nel progetto sottostante.  In modalità di interruzione, tuttavia, non è in genere consentito apportare modifiche a istruzioni di dichiarazione, quali i metodi pubblici, i campi pubblici o le dichiarazioni di classe.  
  
 Quando si apporta una modifica non autorizzata, la modifica viene contrassegnata con una sottolineatura ondulata di colore viola e nell'Elenco attività viene visualizzata un'attività.  Per poter continuare a utilizzare Modifica e continuazione, è necessario annullare la modifica non autorizzata.  Alcune modifiche non autorizzate sono consentite se effettuate all'esterno di Modifica e continuazione.  Se si desidera mantenere i risultati di tale modifica non autorizzata, è necessario interrompere il debug e riavviare l'applicazione.  
  
 La modalità Modifica e continuazione è supportata per i progetti a 64 bit destinati a .NET Framework 4.5.1.  
  
 Modifica e continuazione non è supportato quando si avvia il debug con il comando **Connetti a processo**.  La funzionalità Modifica e continuazione non è supportata per il codice ottimizzato, il codice nativo e gestito misto o i progetti Compact Framework \(Smart Device\).  
  
 Negli argomenti di questa sezione vengono fornite informazioni dettagliate sull'utilizzo di questa funzionalità e sui tipi di modifiche non consentiti.  
  
## In questa sezione  
 [Procedura: applicare modifiche in modalità di interruzione con Modifica e continuazione](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Viene descritto come applicare modifiche al codice in modalità di interruzione.  
  
 [Modifiche non supportate in Modifica e continuazione di Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Descrive i tipi di modifiche che non è possibile eseguire in Modifica e continuazione di [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## Sezioni correlate  
 [Modifica e continuazione](../debugger/edit-and-continue.md)  
 È disponibile un elenco di argomenti su Modifica e continuazione.