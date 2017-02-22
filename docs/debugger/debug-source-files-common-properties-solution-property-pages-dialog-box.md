---
title: "Esegui debug dei file di origine, Propriet&#224; comuni, finestra di dialogo Pagine delle propriet&#224; di soluzione | Microsoft Docs"
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
  - "vs.debug.options.FindSource"
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
  - "Esegui debug dei file di origine (pagina delle proprietà)"
  - "debug [Visual Studio], specifica dei file di origine e di simboli"
  - "file di origine, specifica nel debugger"
  - "debugger, file di origine"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Esegui debug dei file di origine, Propriet&#224; comuni, finestra di dialogo Pagine delle propriet&#224; di soluzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.  
  
 Per accedere alla pagina delle proprietà **Esegui debug dei file di origine**, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Proprietà** dal menu di scelta rapida.  Espandere la cartella **Proprietà comuni** e fare clic sulla pagina **Esegui debug dei file di origine**.  
  
 **Directory contenenti codice sorgente**  
 Contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione.  La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.  
  
 **Escludi dalla ricerca i seguenti file di origine**  
 Immettere i nomi dei file che non si desidera vengano letti dal debugger.  Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora.  Se durante il debug viene visualizzata la finestra di dialogo **Trova origine** e si fa clic su **Annulla**, il file cercato verrà aggiunto all'elenco per evitare che il debugger continui a cercarlo.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)