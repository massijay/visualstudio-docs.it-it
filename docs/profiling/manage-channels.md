---
title: "Gestione dei canali | Microsoft Docs"
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
  - "vs.cv.threads.tools.managechannels"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, gstione dei canali"
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gestione dei canali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In **Visualizzazione thread** nel Visualizzatore di concorrenza, è possibile organizzare i canali per il processo in modo da poter esaminare determinati modelli.  È possibile ordinare i canali, alzarli e abbassarli e nasconderli o visualizzarli.  
  
## Ordina per  
 È possibile utilizzare il comando Sort By per ordinare le thread in base a criteri diversi, basati sul livello di zoom corrente.  Ciò può risultare particolarmente utile quando si è in cerca di un modello particolare.  È possibile ordinare secondo questi criteri:  
  
|Criteri|Definizione|  
|-------------|-----------------|  
|Ora di inizio|Ordina i thread in base al tempo di inizio.  Si tratta dell'ordinamento predefinito.|  
|Ora di fine|Ordina i thread in base ai relativi tempi di fine.|  
|Esecuzione|Ordina i thread in base alla percentuale di tempo trascorso in fase di esecuzione.|  
|Sincronizzazione|Ordina i thread in base alla percentuale di tempo trascorso in fase di sincronizzazione.|  
|I\/O|Ordina i thread in base alla percentuale di tempo trascorsa in I\/O \(lettura e scrittura di dati\).|  
|Sleep|Ordina i thread in base alla percentuale di tempo trascorso in fase di sospensione.|  
|Paging|Ordina i thread in base alla percentuale di tempo trascorso in fase di paging.|  
|Priorità|Ordina i thread in base alla percentuale di tempo trascorso in fase di annullamento.|  
|Elaborazione interfaccia utente|Ordina i thread in base alla percentuale di tempo trascorso nell'elaborazione dell'interfaccia utente.|  
  
## Sposta il Canale Selezionato Su o Giù  
 È possibile utilizzare questi controlli per spostare un canale verso l'alto o verso il basso nell'elenco.  Ad esempio, è possibile posizionare i canali correlati accanto agli altri per esaminare un modello specifico oppure una relazione cross\-thread.  
  
## Sposta il canale selezionato in cima o in fondo  
 È possibile spostare i canali selezionati nella parte superiore o inferiore dell'elenco in modo da poter esaminare un particolare modello, oppure spostare alcuni canali per allontanarli quando si esaminano gli altri.  
  
## Nascondere i Canali Selezionati  
 Scegliere questo controllo quando si desidera nascondere i canali.  Se, ad esempio, viene visualizzato un thread che rappresenta una sincronizzazione al 100% per la durata del processo gestito, è probabilmente possibile nasconderlo mentre vengono analizzati altri thread.  
  
> [!NOTE]
>  Se un thread viene nascosto, viene anche rimosso dal tempo di calcolo mostrato nella legenda attiva e nei rapporti di profilo.  
  
## Mostra Tutti i Canali  
 Questo controllo è attivo quando uno o più canali vengono nascosti.  Se lo si sceglie, tutti gli elementi nascosti vengono mostrati e vengono inclusi nel calcolo del tempo.  
  
## Spostare i Marcatori in Cima  
 Se una traccia contiene gli eventi del marcatore, è possibile utilizzare questo comando per spostare i canali del marcatore nella parte superiore della sequenza temporale.  Il loro ordine relativo viene preservato.  
  
## Raggruppare i Marcatori in base ai Thread  
 Se una traccia contiene gli eventi del marcatore, è possibile utilizzare questo comando per raggruppare i canali del marcatore sotto un thread che ha generato gli eventi del marcatore.  I canali dei dischi vengono spostati nella parte superiore dell'elenco dei canale e i canali di GPU vengono spostati nella parte inferiore.  
  
## Vedere anche  
 [Controllo zoom \(visualizzazione Thread\)](../profiling/zoom-control-threads-view.md)   
 [Modalità misurazione attiva\/non attiva](../profiling/measure-mode-on-off.md)   
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)