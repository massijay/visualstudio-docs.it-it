---
title: "Finestra di dialogo Terminazione debug in corso | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Terminazione debug in corso (finestra di dialogo)"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo Terminazione debug in corso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando il debugger tenta di interrompere una sessione di debug, ma questa operazione richiede tempo.  L'interruzione di una sessione di debug è in genere un'operazione molto veloce e questa finestra di dialogo non viene visualizzata.  Talvolta, tuttavia, è necessario più tempo per la disconnessione da tutti i processi in fase di debug.  Se l'interruzione della sessione richiede diversi secondi o si verifica un errore di disconnessione, viene visualizzata questa finestra di dialogo.  Se ciò avviene di frequente, è possibile che sia presente un problema interno. Può quindi essere opportuno contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
 È possibile attendere la disconnessione dei processi e la chiusura della finestra di dialogo oppure utilizzare il pulsante **Termina ora** per terminare immediatamente l'operazione.  
  
 **Termina ora**  
 Fare clic su questo pulsante per terminare immediatamente la sessione di debug.  Con il pulsante **Termina ora** i processi sottoposti a debug vengono interrotti, anziché disconnessi.  Se si esegue il debug di processi di sistema, l'interruzione di tali processi con **Termina ora** può generare effetti imprevisti e indesiderati.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/it-it/f2c756c2-8079-474b-94c2-01c19a141a01)