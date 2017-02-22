---
title: "Procedura: modificare l&#39;opzione di avanzamento nell&#39;esecuzione del debug (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "avanzamento nel ramo"
  - "debug dei flussi di lavoro, opzioni di avanzamento"
  - "debug, opzioni di avanzamento"
  - "avanzamento nell’istanza"
  - "istruzioni (esecuzione), modifica delle opzioni"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: modificare l&#39;opzione di avanzamento nell&#39;esecuzione del debug (legacy)
In questo argomento viene descritto come modificare l'opzione di avanzamento nell'esecuzione del debug per le applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy aventi azioni simultanee.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si esegue il debug di attività legacy ad esecuzione contemporanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni disponibili per eseguire le istruzioni del codice una alla volta.  
  
 Seguire questi passaggi per modificare l'opzione di avanzamento nell’esecuzione del debug nel progetto del flusso di lavoro legacy.  
  
## Procedure  
  
#### Per modificare l'opzione di avanzamento nell'esecuzione del debug  
  
1.  Avviare Visual Studio.  
  
2.  Aprire un progetto flusso di lavoro legacy esistente o creare un nuovo progetto che utilizza attività simultanee e che viene destinato a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  Nel menu **Flusso di lavoro** della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy, selezionare **Debug**, quindi **Opzioni per l'esecuzione di istruzioni**.  
  
4.  Selezionare **Istanza** o **Ramo**.  
  
## Vedere anche  
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Opzioni di avanzamento nell’esecuzione del debug \(legacy\)](../workflow-designer/debug-stepping-options-legacy.md)