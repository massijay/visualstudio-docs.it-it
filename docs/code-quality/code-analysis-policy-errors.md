---
title: "Errori dei criteri per l&#39;analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyfailures"
helpviewer_keywords: 
  - "errori dei criteri, analisi codice"
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Errori dei criteri per l&#39;analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si verificano gli errori seguenti se i criteri dell'analisi del codice non vengono soddisfatti all'archiviazione:  
  
 **Le impostazioni di analisi codice per uno o più progetti non sono compatibili con i criteri di analisi codice.**  
  
 I requisiti di analisi del codice archiviano nel controllo del codice sorgente del progetto team non vengono soddisfatti per uno o più progetti di codice.  Questo errore può essere causato da una o più delle seguenti condizioni:  
  
1.  L'analisi del codice non è abilitata nella compilazione per tutti i progetti nella soluzione.  
  
2.  Il set di regole locale per il progetto in Visual Studio ha un'impostazione **Azione** meno restrittiva del set di regole per il progetto team, ad esempio una regola impostata su **Azione**\=**Errore** sul server ha **Azione** impostato su **Avviso** o **Nessuno** nel set di regole che viene eseguito in Visual Studio.  
  
3.  Il set di regole specificato in Visual Studio non contiene tutte le regole indicate nel set di regole specificato nei criteri di archiviazione dell'analisi del codice per il progetto team.  
  
 **Impossibile applicare i criteri di analisi del codice.  Il progetto {0} contiene errori oppure la build non è aggiornata.**  
  
 La compilazione contiene errori oppure gli errori sono stati corretti, ma l'analisi del codice non è stata eseguita dopo la correzione.  
  
 **Impossibile archiviare.  I criteri di analisi del codice richiedono che l'archiviazione avvenga tramite Visual Studio con una soluzione aperta.**  
  
 I criteri dell'analisi del codice richiedono che tutti i file in corso di archiviazione siano nella soluzione attualmente aperta.  Per correggere questo errore, aprire la soluzione che contiene il file da archiviare.  
  
 **Alcuni file nell'archiviazione in sospeso fanno parte della soluzione attualmente aperta.**  
  
 I criteri dell'analisi del codice richiedono che tutti i file in corso di archiviazione siano nella soluzione attualmente aperta.  Questo errore viene generato quando una soluzione è aperta, ma alcuni file nella visualizzazione dell'archiviazione in sospeso non fanno parte di tale soluzione.  Per correggere questo errore, aprire la soluzione che contiene il file da archiviare.  
  
 **Versione di '{0}' non corretta.  Il nome sicuro specificato nei criteri è '{1}'.**  
  
 Questo errore si applica ai progetti .NET.  Un file .dll di regole richiesto dai criteri di analisi del codice esiste nel computer locale, ma la versione\/chiave pubblica non corrisponde.  Per correggere questo errore, l'autore dei criteri deve aggiornare i file .dll nella directory *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* del computer.  
  
 **L'assembly '{0}' specificato nei criteri non esiste.**  
  
 Questo errore si applica ai progetti .NET.  Una regola richiesta dai criteri di analisi del codice non dispone del file dll corrispondente installato nel computer client.  Per correggere questo errore, l'autore dei criteri deve aggiornare il file .dll nella directory *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* del computer.  
  
 **Le impostazioni relative alle regole del progetto {0} non sono conformi ai criteri dell'analisi del codice.**  
  
 Questo errore si applica ai progetti .NET.  Le impostazioni del codice gestito sono meno rigorose di quanto richiesto dai criteri.  Per correggere questo errore, l'impostazione del client deve essere rigorosa almeno quanto richiesto dai requisiti dei criteri nel server.  
  
 **L'analisi del codice non è attivata nella configurazione attiva.  Passare alla configurazione {0} e compilare il progetto {1} prima di archiviare.**  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configurazione attiva non prevede l'analisi del codice, tuttavia è abilitata almeno un'analisi di questo tipo.  
  
 **È necessario abilitare l'analisi del codice per i binari gestiti nelle proprietà {0} del progetto e compilare prima dell'archiviazione.**  
  
 Questo errore si applica ad applicazioni [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET.  I criteri richiedono l'esecuzione dell'analisi del codice gestito, tuttavia essa non è abilitata nel progetto corrente nel client.  
  
 **È necessario abilitare l'analisi del codice nelle proprietà {0} del progetto e compilare prima dell'archiviazione.**  
  
 Questo errore si applica a progetti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e a progetti Web.  I criteri richiedono l'esecuzione dell'analisi del codice gestito, tuttavia essa non è abilitata nel progetto corrente nel client.  
  
 **È necessario abilitare l'analisi del codice C\/C\+\+ nelle proprietà {0} del progetto e compilare prima dell'archiviazione.**  
  
 Questo errore si applica ai progetti non gestiti.  I criteri richiedono l'esecuzione dell'analisi del codice per C\/C\+\+, tuttavia essa non è abilitata nel progetto corrente nel client.  
  
## Vedere anche  
 [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)