---
title: "Procedura: attivare e disabilitare Modifica e continuazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "/INCREMENTAL (opzione del linker)"
  - "Applica modifiche del codice (comando)"
  - "modalità di interruzione, applicazione di modifiche al codice"
  - "modifiche al codice, applicazione in modalità di interruzione"
  - "Modifica e continuazione, applicazione di modifiche al codice"
  - "Modifica e continuazione, disabilitazione"
  - "Modifica e continuazione, abilitazione"
  - "Go (comando)"
  - "INCREMENTAL (opzione del linker)"
  - "comandi per l'esecuzione di istruzioni"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: attivare e disabilitare Modifica e continuazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile disabilitare o abilitare Modifica e continuazione nella finestra di dialogo **Opzioni** in fase di progettazione.  Non è possibile modificare questa impostazione durante il debug.  
  
 La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug.  Per il codice C\+\+ nativo, la funzionalità Modifica e continuazione richiede l'utilizzo dell'opzione \/INCREMENTAL.  
  
## Procedure  
  
#### Per abilitare o disabilitare Modifica e continuazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere il nodo **Debug** e selezionare la categoria **Modifica e continuazione**.  
  
3.  Per abilitare la funzionalità, selezionare la casella di controllo **Abilita Modifica e continuazione**.  Per disabilitarla, deselezionare la casella di controllo.  
  
    > [!NOTE]
    >  Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata.  Per ulteriori informazioni, vedere [Configurare IntelliTrace per raccogliere informazioni di debug](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Scegliere **OK**.  
  
## Vedere anche  
 [Modifica e continuazione](../debugger/edit-and-continue.md)   
 [Modifica e continuazione, Debug, finestra di dialogo Opzioni](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)