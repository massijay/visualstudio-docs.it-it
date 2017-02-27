---
title: "Procedura: Serializzare le informazioni sui simboli | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "strumenti per la profilatura, serializzazione delle informazioni sui simboli"
  - "strumenti per le prestazioni, serializzazione delle informazioni sui simboli"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Procedura: Serializzare le informazioni sui simboli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile serializzare i simboli necessari per analizzare l'applicazione.  Mediante la serializzazione dei simboli vengono aggiunti simboli al file vsp.  L'aggiunta di informazioni sui simboli nel file vsp consente ad altri utenti di analizzare il rapporto di prestazioni senza disporre di accesso ai simboli originali.  Se i simboli non vengono serializzati, sarà necessario disporre dei file exe e pdb originali instrumentati per analizzare il file vsp.  
  
### Per serializzare automaticamente le informazioni sui simboli  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
     Verrà visualizzata la finestra di dialogo **Opzioni**  
  
2.  Fare clic su **Strumenti di prestazioni**.  
  
3.  In **Opzioni generali** selezionare **Serializzare automaticamente le informazioni sui simboli**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/it-it/0340ddde-caf4-48ac-8af3-d15dcdade556)