---
title: "Opzioni di avanzamento nell’esecuzione del debug (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "avanzamento nel ramo"
  - "debug dei flussi di lavoro, opzioni di avanzamento"
  - "debug, opzioni di avanzamento"
  - "avanzamento nell’istanza"
  - "istruzioni (esecuzione), opzioni per l'esecuzione del debug del flusso di lavoro"
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Opzioni di avanzamento nell’esecuzione del debug (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che dispongono di attività simultanee in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si esegue il debug di attività legacy ad esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni seguenti per eseguire le istruzioni del codice una alla volta.  
  
-   **Avanzamento nel ramo.** Questo metodo consente di procedere ed eseguire il debug di un particolare ramo di un'attività composta, ad esempio l'attività **ParallelActivity** o **ConditionalActivityGroup**.Quando si usa quest'opzione di debug, non si noterà una modifica nel controllo dovuta all'esecuzione contemporanea di altre attività all'interno del flusso di lavoro.Il debugger avanza solo attraverso le attività del ramo attualmente selezionato mentre le altre attività del flusso di lavoro possono essere eseguite contemporaneamente.Ad esempio, per impostazione predefinita vengono utilizzati per l'avanzamento il ramo all'estrema sinistra di un'attività **ParallelActivity** e la prima attività figlia di un'attività **ConditionedActivityGroup**.Se l’utente desidera eseguire il debug di qualsiasi altro ramo o attività figlia, un punto di interruzione esplicito deve essere posizionato su quel ramo o su quella attività figlia.Quando il punto di interruzione viene generato, l'avanzamento continua in quel ramo.  
  
-   **Avanzamento nell’istanza.** Questa modalità di procedere consente di procedere ed eseguire il debug eseguendo contemporaneamente le attività del flusso di lavoro.Con questa opzione, si noterà che si verifica una modifica nel controllo durante l'esecuzione contemporanea di attività eseguite all'interno del flusso di lavoro.  
  
 Per impostazione predefinita, l'opzione di avanzamento nel ramo è selezionata e gli utenti possono passare tra le due opzioni durante l'esecuzione del debug di un flusso di lavoro legacy.  
  
 È necessario selezionare l'opzione di avanzamento dell’istanza in caso di esecuzione di debug di flussi di lavoro di macchine a stati legacy.  
  
## Vedere anche  
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Procedura: modificare l'opzione di avanzamento nell'esecuzione del debug \(legacy\)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)