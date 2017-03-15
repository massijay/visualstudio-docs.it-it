---
title: "Procedura: utilizzare l&#39;esplorazione tramite la barra di navigazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Procedura: utilizzare l&#39;esplorazione tramite la barra di navigazione
Il set delle attività visualizzate in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] può essere modificato in tre modi principali:  
  
1.  Facendo doppio clic per analizzare un'attività figlio.  
  
2.  Facendo clic su un pulsante nella barra di navigazione per passare a un'attività predecessore.  
  
3.  Espandendo o comprimendo le attività sul posto.  
  
### Utilizzando l'esplorazione tramite la barra di navigazione  
  
1.  Fare doppio clic su un'attività di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] per impostare l'attività radice sull'attività selezionata tramite clic.L'attività selezionata viene quindi espansa completamente alla radice e i relativi predecessori vengono mostrati nella barra di navigazione.Questa operazione viene talvolta definita analisi o annullamento dell'analisi di un'attività.  
  
2.  Per passare a un predecessore dell'attività radice corrente, fare clic sull'attività nella barra di navigazione.  
  
### Espansione o compressione di un'attività sul posto  
  
1.  Fare clic sulle virgolette in un'attività per espanderla o comprimerla sul posto.  
  
2.  Quando lo stato di espansione viene modificato facendo clic sul pulsante, il nuovo stato di espansione viene salvato in XAML.  
  
    > [!WARNING]
    >  Non tutte le attività possono essere espanse sul posto.Esistono due casi in cui un'attività non può essere espansa sul posto, ovvero quando il padre dell'attività non consente l'espansione sul posto dei relativi figli \(le attività di un diagramma di flusso non possono ad esempio essere espanse sul posto\) o quando non è consentita l'espansione automatica dell'ActivityDesigner sul posto.Anche se nessuno degli ActivityDesigner inclusi in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] presenta quest'ultimo comportamento, è possibile che alcune attività personalizzate lo espongano.  
  
### Espansione o compressione di tutte le attività  
  
1.  Utilizzare i pulsanti **Espandi tutto** e **Comprimi tutto** dell'interfaccia utente per espandere o comprimere tutte le attività al di sotto della radice della barra di navigazione corrente.Si noti che Espandi tutto e Comprimi tutto sono stati globali.Ciò significa che quando si modifica l'attività radice utilizzando l'esplorazione tramite la barra di navigazione, lo stato Espandi tutto o Comprimi tutto permane fino a quando non si fa clic su **Ripristina**.  
  
2.  Una volta applicato uno stato Espandi tutto o Comprimi tutto, è possibile fare clic sul pulsante **Ripristina** visualizzato per tornare alla visualizzazione dello stato applicato precedentemente a ogni attività.  
  
    > [!WARNING]
    >  Se per un'attività, quale <xref:System.Activities.Statements.Flowchart>, non è stata scelta l'espansione sul posto, la funzionalità associata ai pulsanti **Espandi tutto** e **Comprimi tutto** risulta disabilitata nell'ActivityDesigner **Flowchart**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] la finestra di progettazione **diagramma di flusso**, vedere gli argomenti di [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md).  
  
    > [!WARNING]
    >  Il pulsante Espandi tutto determina inoltre un effetto speciale negli ActivityDesigner **Switch** e **TryCatch**.Quando si fa clic su **Espandi tutto**, vengono visualizzati tutti i case Switch e tutti i blocchi try\/catch\/finally.Facendo clic su **Ripristina** o su **Comprimi tutto** viene ripristinato lo stato predefinito di tali finestre di progettazione, in cui è possibile fare clic su un case\/blocco singolo per visualizzarne il contenuto.